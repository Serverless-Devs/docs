# Yaml规范文档

Serverless Devs是可以通过Yaml进行资源描述的，我们也是推荐使用者通过Yaml进行资源和行为的管理。

Serverless Devs Cli可以识别的Yaml默认文件为`s.yaml`/`s.yml`，使用者也可以通过`-t/--template`来进行其他名称的Yaml文件的指定，Serverless Devs Cli可识别的Yaml规范格式整体为：

```yaml
edition: 1.0.0        #  命令行YAML规范版本，遵循语义化版本（Semantic Versioning）规范
name: FullStack       #  项目名称
access: xxx-account1  #  秘钥别名

vars: # [全局变量，提供给各个服务使用]
  logo: https://image.aliyun.com/xxxx.png
  domain: xxxx.yyy.com

services:
  nextjs-portal: #  服务名称
    provider: alibaba     # 云厂商名称，如果和项目的provider相同，可省略
    access: xxx-account1  #  秘钥别名，如果和项目的access相同，可省略
    component: vue-component  # 组件名称
    props: #  组件的属性值
      src: ./frontend_src
      url: ${backend.output.url}
    actions: # 自定义执行逻辑
      pre-deploy: # 在deploy之前运行
        - run: s exec -- publish  # 要运行的命令行
          path: ./backend_src # 命令行运行的路径
        - plugin: plugin-name # 要运行的plugin名称
      post-deploy: # 在deploy之后运行
        - run: s clean
          path: ./frontend_src

  assets:
    component: static
    props:
      cache-control: "public, max-age=604800, immutable"
      www: "./public"

  express-blog:
    component: express
    props:
      app: ./express-blog
      url: ${domain}
    actions:
      pre-deploy:
        - run: npm run build
          path: ./express-blog

  gateway:
    component: serverless-gateway # 路由组件：HTTP URL和服务之间的映射规则
    props:
      routes:
        - route: /~assets
          value: ${assets.outPut.url}
        - route: /
          value: ${nextjs-portal.outPut.url}
          index: index.html
        - route: /~portal
          value: ${nextjs-portal.outPut.url}
          inex: index.html
        - route: /~blog
          value: ${express-blog.outPut.url}
```