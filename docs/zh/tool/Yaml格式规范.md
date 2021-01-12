# Yaml配置相关

Serverless Devs Tool的默认资源配置获取顺序：
```
s.yaml
s.yml
s.json
template.yaml
template.yml
template.json
```

Yaml文件配置基本格式是：

```yaml
ProjectName:
  Component: 组件名
  Provider: 云厂商
  Properties: 组件定义的参数
```

也就是说，您在使用Serverless Devs Tool的时候，至少要保证您的数据格式符合以上要求。当然，工具中还有很多高级参数，例如完整格式是：

```yaml
ProjectName:
  Component: 组件名
  Provider: 云厂商
  Access: 密钥名称
  Extends: # 插件信息
      deploy: # 组件支持的某个方法，例如组件的deploy方法
        - Plugin: stest_plugin # 执行的插件
          Pre: true # 在执行某个指令之前/之后执行
        - Hook: pip install # hook内容
          Path: ./ # 执行Hook的目录，可选
          Pre: true # 在执行某个指令之前/之后执行
  Properties: 组件定义的参数
```

据一个相对完整的例子，例如某个Yaml可以写成这样子：

```yaml
MyExpress:
  Component: express
  Provider: alibaba
  Access: release
  Extends: 
      deploy: 
        - Plugin: TestPlugin
          Pre: true 
        - Hook: npm install
          Path: ./ 
          Pre: true 
  Properties: 
    Region: cn-hangzhou
    CodeUri: ./
```

这个Yaml内容的意思是：
1. 这个项目是MyExpress
2. 这个项目使用了alibaba的express组件
3. 这个项目使用了alibaba.release的密钥信息
4. 这个项目在用执行deploy之前要分别执行：
    - 插件TestPlugin
    - 在目录./下执行命令`npm install`

当然，一个项目中也可以存在多段，例如，我有一个项目包括前端和后端两个部分，那么我就可以在一个Yaml中写两个项目`WebBackend`和`WebFronted`：

```yaml
WebBackend:
  Component: express
  Provider: alibaba
  Access: release
  Properties: 
    Region: cn-hangzhou
    CodeUri: ./

WebFronted:
  Component: website
  Provider: alibaba
  Access: release
  Properties: 
    Region: cn-hangzhou
    CodeUri: ./
```

在写Yaml的时候，我们也可以写一些全局变量，全局变量可以用`Global`来表示，例如：

```yaml
Global:
    Region: cn-hangzhou

WebBackend:
  Component: express
  Provider: alibaba
  Access: release
  Properties: 
    Region: ${Global.Region}
    CodeUri: ./

WebFronted:
  Component: website
  Provider: alibaba
  Access: release
  Properties: 
    Region: ${Global.Region}
    CodeUri: ./

```

在实际项目中，经常会出现，两个Project之间有相互依赖，例如我要部署完成我的后端项目，拿到后端地址，放到前端项目中，才能进行build，进而才能进行前端项目的部署，所以我们往往会存在一些动态参数，例如：

```yaml
Global:
    Region: cn-hangzhou

WebBackend:
  Component: express
  Provider: alibaba
  Access: release
  Properties: 
    Region: ${Global.Region}
    CodeUri: ./

WebFronted:
  Component: website
  Provider: alibaba
  Access: release
  Properties: 
    Region: ${Global.Region}
    CodeUri: ./
    BackedUrl: ${WebBackend.Output.Url[0].Value}

```

此时，Serverless Devs Tool就会对Yaml内容进行分析，分析出我们需要先部署`WebBackend`获得到输出结果后，并将输出结果中的`Url[0].Value`赋值到项目`WebFronted`的`BackedUrl`属性中，再进行部署`WebFronted`。

除了上述所说的Yaml支持的格式，Yaml支持的更多的格式如下：

- 获取当前机器中的环境变量：${Env(环境变量)}，例如${Env(SecretId)}
- 获取外部文档的变量：${File(路径)}，例如${File(./path)}
- 获取全局变量：${Global.*}
- 获取其他项目的变量：${ProjectName.Properties.*}
- 获取Yaml中其他项目的结果变量：${ProjectName.Output.*}

当然，如果一个Yaml中有过多的项目，系统也会默认分析部署顺序：
1. 分析项目中的依赖关系
2. 有依赖关系的按照依赖关系从前到后部署，无依赖关系的按Yaml配置的从上到下部署
3. 插件分析，按照配的从上到下部署（pre为true就是之前部署，pre为false就是组件部署之后再部署）

例如：

```yaml
Global:
    Region: cn-hangzhou

WebBackend:
  Component: express
  Provider: alibaba
  Access: release

  Properties: 
    Region: ${Global.Region}
    CodeUri: ./

WebFronted:
  Component: website
  Provider: alibaba
  Access: release
  Extends: 
      deploy: 
        - Plugin: TestPlugin
          Pre: true 
        - Plugin: TestPluginEnd
          Pre: false 
        - Hook: npm install
          Path: ./ 
          Pre: true 
  Properties: 
    Region: ${Global.Region}
    CodeUri: ./
    BackedUrl: ${WebBackend.Output.Url[0].Value}

```

整个部署流程是：
1. 分析部署顺序: WebBackend->WebFronted
2. 部署WebBackend-express
3. 获得到WebBackend的输出结果，并将结果中的`Url[0].Value`赋值给WebFronted中的`BackedUrl`
4. 部署WebFronted的插件：
    - 运行TestPlugin插件
    - 在`./`目录下执行`npm install`
5. 部署WebBackend-website
6. 部署WebFronted的插件：
    - TestPluginEnd
    
额外说明：如果在执行项目的时候，想跳过行为描述，可以使用：`--skip-extends`参数。