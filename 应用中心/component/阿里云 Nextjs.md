# 阿里云 Next.JS 项目部署文档

## 前言

通过本组件，您可以简单快速的将Next.JS项目部署到线上。

## 使用

### 最简使用方法

模版拉取：

```
s init nextjs
```

其中Yaml的默认配置为：

```yaml
NextjsComponent:
  Component: nextjs
  Provider: alibaba
  Extends:
    deploy:
      - Hook: npm install --production
        Path: ./src
        Pre: true
  Properties:
    Region: 'cn-hangzhou'
    CodeUri: './src'
```

系统默认bootstrap内容：

```shell script
#!/usr/bin/env bash

export PORT=9000
npx next start --port $PORT
```

### 完整Yaml示例

```yaml
NextjsComponent:
  Component: nextjs
  Provider: alibaba
  Extends:
  deploy:
    - Hook: npm install --production
      Path: ./src
      Pre: true
  Properties:
    Region: 'cn-hangzhou'
    #      CodeUri: 本地路径
    #      CodeUri:
    #        Src: 本地路径
    #        Exclude:
    #          - path
    #        Include:
    #          - path
    #      CodeUri:
    #        Bucket: function code包的bucket name
    #        Object: code zip包的object name
    CodeUri:
      Bucket: function code包的bucket name
      Src: 本地路径
      Exclude:
        - path
      Include:
        - path
    Environment:
      - Key: Environmentkey
        Value: EnvironmentValue
    Log:
      LogStore: loghub中的logstore名称
      Project: loghub中的project名称
    Detail:
      Service:
        Name: 服务名
        Description: 服务描述
        InternetAccess: 访问公网
        Role: 授予函数计算所需权限的RAM role
        Vpc:
          SecurityGroupId: 安全组
          VSwitchIds:
            - 一个或多个VSwitch ID
          VpcId: VPC ID
        Nas:
          Use--package-type pip oss2 pymysqlrId: userID
          GroupId: groupID
          MountPoints:
            - ServerAddr: adasdasdas
              MountDir: ./ssssss
        Tags:
          - Key: 标签名
            Value: 标签值
          - Key: 标签名
            Value: 标签值
      Function: 函数名
        Name: 函数名
        Description: 函数描述
        MemorySize: function的内存规格
        Timeout: function运行的超时时间
        Triggers:
          - Name: TriggerNameHttp
            Parameters:
              AuthType: ANONYMOUS
              InvocationRole: 使用一个 RAM 角色的 ARN 为函数指定执行角色
              Methods:
                - GET
                - POST
                - PUT
              Domains:
                - Domain: AUTO/或者您的网址
                  Protocol:
                    - HTTP
                    - HTTPS
                  CertConfig:
                    CertName: 'CertName'
                    PrivateKey: './certificates/privateKey.pem'
                    Certificate: './certificates/certificate.pem'
                  Routes:
                    - Path: '/a'
                      Qualifier: Prod # 版本（可选)
                    - Path: '/a'
                      Qualifier: Prod # 版本（可选)
```

### 详细使用方法

| 参数名 |  必填|  类型|  参数描述 | 
| --- |  --- |  --- |  --- | 
| Region | true | Enum | 地域 |
| Log | false | Struct | log配置，function产生的log会写入这里配置的logstore |
| CodeUri | false(默认为./) | String/Struct | 代码位置 |
| Environment | false | Struct | 环境变量 |
| Domains | false | Struct/<Struct>List | 自定义域名配置 |
| Detail | false | Struct | 详细配置 |


#### Region

参数取值：`cn-beijing`, `cn-hangzhou`, `cn-shanghai`, `cn-qingdao`, `cn-zhangjiakou`, `cn-huhehaote`, `cn-shenzhen`, `cn-chengdu`, `cn-hongkong`, `ap-southeast-1`, `ap-southeast-2`, `ap-southeast-3`, `ap-southeast-5`, `ap-northeast-1`, `eu-central-1`, `eu-west-1`, `us-west-1`, `us-east-1`, `ap-south-1`, `cn-zhangjiakou-na62-a01

#### Log

| 参数名 |  必填|  类型|  参数描述 | 
| --- |  --- |  --- |  --- | 
| LogStore | false | String | loghub中的logstore名称 |
| Project | false | String | loghub中的project名称 |

#### CodeUri

- 
    直接填写路径
    
- 
    | 参数名 |  必填|  类型|  参数描述 | 
    | --- |  --- |  --- |  --- | 
    | Bucket | false | String | function code包的bucket name |
    | Object | false | String | code zip包的object name |
    | Exclude | false | <String>List | 除去路径 |
    | Include | false | <String>List | 包括路径 |

- 
    | 参数名 |  必填|  类型|  参数描述 | 
    | --- |  --- |  --- |  --- | 
    | Bucket | false | String | function code包的bucket name |
    | Src | false | String | 本地路径 |
    | Exclude | false | <String>List | 除去路径 |
    | Include | false | <String>List | 包括路径 |
    
#### Domains

- 
    | 参数名 |  必填|  类型|  参数描述 | 
    | --- |  --- |  --- |  --- | 
    | Domain | false | String | 域名 |
    
- 
    | 参数名 |  必填|  类型|  参数描述 | 
    | --- |  --- |  --- |  --- | 
    | Domain | false | String | 域名 |
    | Protocol | false | List(HTTP,HTTPS) | 协议 |
    | CertConfig | false | Struct | 域名证书 |
    | Routes | false | Struct | 路径配置 |
    
##### CertConfig

| 参数名 |  必填|  类型|  参数描述 | 
| --- |  --- |  --- |  --- | 
| CertName | false | String | 名称 |
| PrivateKey | false | String | 表示私钥 |
| Certificate | false | String | 表示证书 |
    
##### Routes

| 参数名 |  必填|  类型|  参数描述 | 
| --- |  --- |  --- |  --- | 
| Path | false | String | 路径 |
| Qualifier | false | String | service 版本 |
    
#### Detail

| 参数名 |  必填|  类型|  参数描述 | 
| --- |  --- |  --- |  --- | 
| Service | false | Struct | 服务 |
| Function | false | Struct | 函数 |
| Bootstrap | false | Struct | 启动配置 |

##### Service

| 参数名 |  必填|  类型|  参数描述 | 
| --- |  --- |  --- |  --- | 
| Name | false | String | service名称 |
| Description | false | String | service的简短描述 |
| InternetAccess | false | Boolean | 设为true让function可以访问公网 |
| Role | false | String | 授予函数计算所需权限的RAM role, 使用场景包含 1. 把 function产生的 log 发送到用户的 logstore 中 2. 为function 在执行中访问其它云资源生成 token |
| Vpc | false | Struct | vpc配置, 配置后function可以访问指定VPC |
| Nas | false | Struct |  NAS配置, 配置后function可以访问指定NAS |
| Tag | false | <Struct>List | 标签 |

###### Vpc

| 参数名 |  必填|  类型|  参数描述 | 
| --- |  --- |  --- |  --- | 
| SecurityGroupId | false | String | 安全组ID |
| VSwitchIds | false | String | 一个或多个VSwitch ID |
| VpcId | false | String | VPC ID |

###### Nas

| 参数名 |  必填|  类型|  参数描述 | 
| --- |  --- |  --- |  --- | 
| UserId | false | String | userID |
| GroupId | false | String | groupID |
| MountPoints | false | <Struct>List | 挂载点 |


其中MountPoints为：

| 参数名 |  必填|  类型|  参数描述 | 
| --- |  --- |  --- |  --- | 
| ServerAddr | false | String |  NAS 服务器地址 |
| MountDir | false | String | 本地挂载目录 |

###### Tag

| 参数名 |  必填|  类型|  参数描述 | 
| --- |  --- |  --- |  --- | 
| Key | false | String |  标签名 |
| Value | false | String | 标签值 |

##### Function

| 参数名 |  必填|  类型|  参数描述 | 
| --- |  --- |  --- |  --- | 
| Name | false | String |  function名称 |
| Description | false | String | function的简短描述 |
| MemorySize | false | String |  function的内存规格 |
| Timeout | false | String | function运行的超时时间 |
| Triggers | false | <Struct>List |  触发器 |

###### Triggers

| 参数名 |  必填|  类型|  参数描述 | 
| --- |  --- |  --- |  --- | 
| Name | true | String |  触发器名称 |
| Parameters | true | Struct | 参数内容 |

其中Parameters为：

| 参数名 |  必填|  类型|  参数描述 | 
| --- |  --- |  --- |  --- | 
| AuthType | true | List |  鉴权类型，可选值：ANONYMOUS、FUNCTION |
| Methods | true | List | HTTP 触发器支持的访问方法 |
| Domains | false | String | 参数内容 |
| Enable | false | String | 表示是否启用该触发器。 |
| InvocationRole | false | String | 使用一个 RAM 角色的 ARN 为函数指定执行角色，事件源会使用该角色触发函数执行，请确保该角色有调用函数的权限 |
| Qualifier | false | String | service 版本 |

AuthType枚举：`ANONYMOUS`，`FUNCTION`

Methods枚举：`GET`，`POST`，`PUT`，`DELETE`，`HEAD`

Domains类型为：


- 
    | 参数名 |  必填|  类型|  参数描述 | 
    | --- |  --- |  --- |  --- | 
    | Domain | false | String | 域名 |
    
- 
    | 参数名 |  必填|  类型|  参数描述 | 
    | --- |  --- |  --- |  --- | 
    | Domain | false | String | 域名 |
    | Protocol | false | List(HTTP,HTTPS) | 协议 |
    | CertConfig | false | Struct | 域名证书 |
    | Routes | false | Struct | 路径配置 |

##### Bootstrap

| 参数名 |  必填|  类型|  参数描述 | 
| --- |  --- |  --- |  --- | 
| Port | false | Number | 启动端口 |
| Start | false | String | 启动指令 |