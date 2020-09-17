## 前言

通过本组件，您可以简单快速的部署腾讯云API网管。

## 使用

### 最简使用方法

模版拉取：

```
s init apigateway -p tencent
```

其中Yaml的默认配置为：

```yaml
MyAPIGateway:
  Component: apigateway
  Provider: tencent
  Properties:
    Region: ap-shanghai
    Service:
      Name: serverless
      Description: the serverless service
    API:
        - Path: '/'
          Protocol: HTTP
          Method: GET
          Name: 'mock-api'
          ServiceType: MOCK
          ServiceMockReturnMessage: 'Hello Serverless Devs Tool'
```

### 完整Yaml示例

```yaml
MyAPIGateway:
  Component: apigateway
  Provider: tencent
  Access: release
  Properties:
    Region: ap-shanghai
    Service:
      Id: service-8dsikiq6
      Name: serverless
      Protocols:
        - http
        - https
      Description: the serverless service
      Environment: release
      NetTypes:
        - OUTER
        - INNER
      Domains:
        - Domain: abc.com
          # 如要添加https，需先行在腾讯云-SSL证书进行认证获取cettificateId
          CertificateId: abcdefg
          # 如要设置自定义路径映射，请设置为 false
          IsDefaultMapping: false
          PathMappingSet:
            - Path: /
              Environment: release
          Protocols:
            - http
            - https
    API:
        # 前端类型: WEBSOCKET, 后端类型: SCF
        - Path: /
          Method: GET
          Protocol: WEBSOCKET
          Function:
            # 前端类型为WEBSOCKET且后端为SCF时, transportFunctionName 为必填
            TransportFunctionName: myFunction
            RegisterFunctionName: myFunction
            CleanupFunctionName: myFunction
        # 前端类型: WEBSOCKET, 后端类型: HTTP
        - Path: /ws
          Protocol: WEBSOCKET
          Name: 'test-ws'
          Method: GET
          ServiceType: WEBSOCKET
          ServiceConfig:
            Url: 'ws://www.test.com'
            Path: /
            Method: GET
        # 前端类型: HTTP, 后端类型: SCF
        - Path: /test/{abc}/{cde}
          Id: api-id
          Method: GET
          Description: Serverless REST API
          EnableCORS: TRUE
          ResponseType: HTML
          ServiceTimeout: 10
          Parameters:
            - Name: abc
              Position: PATH
              Required: 'TRUE'
              Type: string
              DefaultValue: abc
              Description: mytest
            - Name: cde
              Position: PATH
              Required: 'TRUE'
              Type: string
              DefaultValue: abc
              Description: mytest
          Function:
            IsIntegratedResponse: true
            FunctionQualifier: $LATEST
            FunctionName: myFunction
          UsagePlan:
            UsagePlanId: 1111
            UsagePlanName: slscmp
            UsagePlanDesc: sls create
            MaxRequestNum: 1000
          Auth:
            SecretName: secret
            SecretIds:
              - AKIDNSdvdFcJ8GJ9th6qeZH0ll8r7dE6HHaSuchJ
        # 前端类型: HTTP, 后端类型: MOCK
        - Path: /mo
          Protocol: HTTP
          Method: GET
          Name: 'mock-api'
          ServiceType: MOCK
          ServiceMockReturnMessage: 'mock response content'
        # 前端类型: HTTP, 后端类型: HTTP
        - Path: /rest
          Protocol: HTTP
          Name: 'test-http'
          Method: GET
          ServiceType: HTTP
          ServiceConfig:
            Url: 'http://www.test.com'
            Path: /test
            Method: GET
```

### 详细使用方法

| 参数名 |  必填|  类型|  参数描述 |
| --- |  --- |  --- |  --- |
| Region | true | Enum | 地域 |
| Service | false | Struct | API网关服务 |
| API | false | Struct | API详细信息 |


#### Service

| 参数         | 必填 | 参数类型 |     默认值     | 描述                                                                                   |
| ------------ | :-------: | :------: | :------------: | :------------------------------------------------------------------------------------- |
| Id    |   false    |  String  |                | 服务的全局唯一 ID，由系统生成                                                          |
| Protocols    |   true    | <String>List |   `['http']`   | 服务的前端请求类型，例如 HTTP，HTTPS，HTTP 和 HTTPS。 （http / https）                 |
| Name  |   false    |  String  |                | 用户自定义的服务名称。 如果该参数未传递，则由系统自动生成一个唯一名称                  |
| NetTypes     |   false    | <String>List |  `['OUTER']`   | 网络类型列表，用于指定支持的访问类型，INNER 为内网访问，OUTER 为外网访问。             |
| Description  |   false    |  String  |                | 用户自定义的服务描述说明                                                               |
| Environment  |   false    |  String  |                | 服务要发布的环境的名称，支持三种环境: test（测试）、prepub（预发布）、 release（发布） |
| Domains |   false    | <Struct>List |      `[]`      | 自定义 API 域名，配置参数参考customDomain 参数说明  |

##### Domains

| 参数             | 必填/可选 | 参数类型 | 默认值 | 描述                                                                                                                     |
| ---------------- | :-------: | :----: | :----: | :----------------------------------------------------------------------------------------------------------------------- |
| Domain           |   true    | String |        | 需要绑定的自定义域名                                                                                                     |
| CertificateId    |   false    | String |        | 自定义域名的证书，如果设置为 https，则为必需。                                                                           |
| IsDefaultMapping |   false    | Boolean | `true` | 是否使用默认路径映射。 如果要自定义路径映射，请设为`false`                                                               |
| PathMappingSet   |   false    | Struct | `[]`  | 自定义路径映射, 当 `isDefaultMapping` 为 `false` 时必填，配置参数参考pathMappingSet 参数说明 |
| Protocols        |   false    | <String>List |      | 绑定自定义域协议类型，例如 HTTP，HTTPS，HTTP 和 HTTPS，默认与前端协议相同                                                |

###### PathMappingSet

| 参数名 |  必填|  类型|  参数描述 |
| --- |  --- |  --- |  --- |
| path | false | String | 自定义映射路径 |
| environment | false | String | 自定义映射环境 |


#### API


| 参数                     | 必填/可选 | 类型 | 默认值  | 描述                                                                                 |
| ------------------------ | :-------: | :-------: | :-----: | :----------------------------------------------------------------------------------- |
| Id                    |   false    | String |         | API 的唯一 ID                                                                        |
| Protocol                 |   false   | <String>List | `HTTP`  | 指定的前端 API 类型， 默认为`HTTP`，如要创建 websocket 类型的 API，请设为`WEBSOCKET` |
| Path                     |   true    | String |         | API 路径                                                                             |
| Method                   |   true    |  String|        | 请求方法                                                                             |
| ServiceType              |   false    | String | `SCF`  | 指定的后端类型，默认为 `SCF`，如要创建 mock 或 http 的类型，可设为 `MOCK`或`HTTP`    |
| Description              |   false    |  String |       | API 描述                                                                             |
| EnableCORS               |   false    | Boolean | `false` | 是否启用跨域访问。 true：启用， false：不启用                                        |
| Function                 |   必填    |  Struct |       | 对应的 Serverless 云函数，配置参数参考function 参数说明        |
| UsagePlan                |   false    |  Struct |        | 基于 API 维度的使用计划，配置参数参考usagePlan 参数说明     |
| Auth                     |   false    |  Struct  |     | API 鉴权设置，配置参数参考auth 参数说明                  |
| ServiceTimeout           |   false    |  Number |       | API 的后端服务超时时间，单位为秒                                                     |
| ResponseType             |   false    |   String      | 返回类型: HTML、JSON、TEST、BINARY、XML                                              |
| Parameters                    |   false    |  <Struct>List |       | 前端请求参数，配置参数参考param 参数说明                    |
| ServiceConfig            |   false    |   Struct |      | API 的后端服务配置，配置参数参考serviceConfig 参数说明    |
| ServiceMockReturnMessage |   false    |    String |     | Mock 接口类型返回结果，如果 `serviceType` 设置为 `MOCK`，此参数必填                  |

##### Function


| 参数                  | 描述                                                                  |
| --------------------- | :-------------------------------------------------------------------- |
| IsIntegratedResponse  | 是否开启响应集成，当前端类型为`HTTP`时生效                            |
| FunctionQualifier     | scf 函数版本                                                          |
| FunctionName          | API 的后端服务的 SCF 函数的名称，当前端类型为`HTTP`时生效且为必填     |
| TransportFunctionName | API 的后端服务的传输函数的名称，当前端类型为`WEBSOCKET`时生效且为必填 |
| RegisterFunctionName  | API 的后端服务的注册函数的名称，当前端类型为`WEBSOCKET`时生效         |
| CleanupFunctionName   | API 的后端服务的清理函数的名称，当前端类型为`WEBSOCKET`时生效         |


##### ServiceConfig

| 参数   | 描述                   |
| ------ | :--------------------- |
| Url    | API 的后端服务 url     |
| Path   | API 的后端服务路径     |
| Method | API 的后端服务请求方法 |


##### UsagePlan

| 参数          | 描述                                                                                       |
| ------------- | :----------------------------------------------------------------------------------------- |
| UsagePlanId   | 用户自定义的基于 API 的使用计划 ID                                                         |
| UsagePlanName | 用户自定义的基于 API 的使用计划名称                                                        |
| UsagePlanDesc | 用户自定义的基于 API 的使用计划描述                                                        |
| MaxRequestNum | 允许的请求总数。不传该参数时默认为 1000 次，若其保留为空，则默认情况下将使用-1，表示已禁用 |

##### Auth

| 参数       | 描述                                                                                  |
| ---------- | :------------------------------------------------------------------------------------ |
| SecretName | 用户自定义的密钥名称                                                                  |
| SecretIds  | 用户自定义的 secretID。当类型为手动时需要。 它可以包含 5 到 50 个字母，数字和下划线。 |



##### Parameters

| 参数         | 描述                                          |
| ------------ | :-------------------------------------------- |
| Name         | 请求参数名称                                  |
| Position     | 参数位置，仅支持`PATH`，`QUERY`和`HEADER`类型 |
| Type         | 参数类型，如 String 和 int.                   |
| DefaultValue | 参数默认值                                    |
| Required     | 参数是否必填， true: 必填; false: 可选        |
| Description         | 参数备注/描述                                 |
