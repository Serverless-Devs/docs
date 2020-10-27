# Config指令帮助文档

Config指令是用来配置账号信息的指令。确切来说，在Serverless Devs Tool中，您可以通过Config来配置多云的全局密钥，也可以通过在当前项目目录下创建/配置临时密钥信息。

- [config add](#Config-add-指令)
- [config get](#Config-get-指令)
- [config delete](#Config-delete-指令)
- [config update](#Config-update-指令)
- [相关说明](#相关说明)
- [帮助信息](#帮助信息)
- [云厂商密钥获取方案](#云厂商密钥获取方案)

## Config add 指令

通过`s config add`指令，您可以添加云厂商账号信息。

目前本工具支持的全局配置厂商包括（按字母先后顺序排序）：

|  云厂商   | 英文名  | 简写  |
|  ----  | ----  |  ----  |
| 阿里云  | Alibaba Cloud |  alibaba |
| AWS  | AWS |  aws |
| Azure  | Azure |  azure |
| 百度云  | Baidu Cloud |  baidu |
| Google Cloud  | Google Cloud |  google |
| 华为云  | Huawei Cloud |  huawei |
| 腾讯云  | Tencent Cloud |  tencent |

### 交互式添加

当您输入`s config add`指令后，系统将会进入交互式添加页面，您此时可以选择一个云厂商进行交互式添加。

- 选择云厂商
    ![](https://images.serverlessfans.com/s-tool/zh/s-config-add.jpg)

- 按照要求输入对应参数
    ![](https://images.serverlessfans.com/s-tool/zh/s-config-add-select.jpg)

    > 这里需要额外注意，最后一个交互内容是别名，这个内容是一个选填内容，如果不填写则默认是`default`，理论上`云厂商+别名`的组合是唯一的。
- 最后系统会让您预览结果，并将输入存储到系统中
    ![](https://images.serverlessfans.com/s-tool/zh/s-config-add-select-result.jpg)

### 命令式添加

通过命令添加密钥信息，您可以更加简单、轻松、快速的配置账号密钥信息。以阿里云为例：

![](https://images.serverlessfans.com/s-tool/zh/s-config-add-direct.jpg)
 
针对不同云厂商，这里有不同的设置：

```
 alibaba: AccountID, AccessKeyID, AccessKeySecret
 aws: AccessKeyID, SecretAccessKey
 baidu: AccessKeyID, SecretAccessKey
 huawei: AccessKey, SecretKey
 tencent: AccountID, SecretID, SecretKey
```

### 其他配置密钥方法

您可以在项目目录下创建`access.yaml`文件，配置密钥信息，例如：

```
# access.yaml

密钥信息名字1：
    Key1: Value1
    Key2: Value2

密钥信息名字2：
    Key1: Value1
    Key2: Value2
```

通过这种方法，您可以配置自定义密钥信息，当然您也可以通过这种方法，解决临时密钥信息配置问题。

### 获取帮助信息

您可以通过指令`s config add -h`获取帮助信息：

![](https://images.serverlessfans.com/s-tool/zh/s-config-add-help.jpg)

## Config get 指令

通过`s config get`指令，您可以获得配置过的账号信息。

- 如您需要获取全部密钥信息: `s config get -l`

    ![](https://images.serverlessfans.com/s-tool/zh/s-config-get-l.jpg)
    
    > 格式为 云厂商(标识) 的是全局配置，例如图中的 阿里云(Alibaba)；格式为 project 的是当前项目配置

- 如果您需要获得某个云厂商的密钥信息，以阿里云为例： `s config get -p alibaba`

    ![](https://images.serverlessfans.com/s-tool/zh/s-config-get-provider.jpg)
    
    > 在这种情况下，系统会默认输出 阿里云 的密钥信息，以及当前项目下的密钥信息。

- 如果您需要获得指定的密钥信息，以上图中的 百度云 demo 为例：`s config get -p baidu -a demo`

    ![](https://images.serverlessfans.com/s-tool/zh/s-config-get-provider-alias.jpg)

当然，您还可以通过`s config get`或者`s config get -h`调出帮助文档信息：

![](https://images.serverlessfans.com/s-tool/zh/s-config-get-help.jpg)

## Config delete 指令

通过`s config delete`指令，您可以删除指定云厂商账号信息。

使用方式是指定云厂商和别名即可（如果在设置的时候没有设置别名，可以默认别名为`default`）。

例如，删除`阿里云`的`release`密钥信息，可以是：

```
s config delete -p alibaba -a release
```

再例如，删除`阿里云`的默认密钥（即在设置的时候没有填写别名）信息，可以是：

```
s config delete -p alibaba -a default
```

> 删除密钥只可以删除全局配置的密钥信息，即通过`s config add`添加的密钥信息，在当前项目下的临时密钥信息，是不支持这种方法删除的。

当然，您还可以通过`s config delete`或者`s config delete -h`调出帮助文档信息：

![](https://images.serverlessfans.com/s-tool/zh/s-config-delete-help.jpg)

## Config update 指令

通过`s config update`指令，您可以更新指定云厂商账号信息。

与`s config add`指令类似，`update`方法也是有两种形式，分别是交互式和命令式。

### 交互式修改

在只指定厂商和别名的时候，可以唤起交互式修改：

![](https://images.serverlessfans.com/s-tool/zh/s-config-update-select.jpg)

在这里，您可以根据系统提示，修改对应的字段信息。如果不修改可以直接按回车跳过。

### 命令式修改

为了给大家更多便利，在此处也增加了命令式修改方法，即在提供Provider（云厂商）和Alias（别名）的同时，指定其他任何对应信息：

```
 alibaba: AccountID, AccessKeyID, AccessKeySecret
 aws: AccessKeyID, SecretAccessKey
 baidu: AccessKeyID, SecretAccessKey
 huawei: AccessKey, SecretKey
 tencent: AccountID, SecretID, SecretKey
```

系统会修改对应内容，例如，将上述图片中的 百度云 demo 中的`AccessKeyID`进行修改：

![](https://images.serverlessfans.com/s-tool/zh/s-config-update-direct.jpg)

当然，您还可以通过`s config update`或者`s config update -h`调出帮助文档信息：

![](https://images.serverlessfans.com/s-tool/zh/s-config-update-help.jpg)

## 相关说明

### 如何使用密钥信息

使用密钥信息的方法很简单，您只需要在项目中填写好密钥的名字即可，例如在项目`MyTest1`中使用了`test`组件，此时配置密钥信息，只需要在`Provider`处指定云厂商（此处指定的是百度云），在`Access`中指定密钥别名即可：

```yaml
MyTest1:
  Component: test
  Provider: baidu
  Access: demo
  Properties:
    Region: 项目相关信息
```

> 如果您在设置的时候没有使用别名，`Access`处可以不填写，或者填写`default`

> 如果您需要使用当前项目的密钥信息，您可以直接使用密钥名称即可。

### 密钥信息使用顺序

当用户使用某云厂商之后，项目中存在临时密钥信息，全局中存在别名一致的密钥信息，系统使用策略如下：

![](https://images.serverlessfans.com/s-tool/zh/s-config-extend-sort.jpg)

## 帮助信息

当然，您还可以通过`s config`或者`s config -h`调出帮助文档信息：

![](https://images.serverlessfans.com/s-tool/zh/s-config-help.jpg)

## 云厂商密钥获取方案

- [阿里云](../../Serverless-Devs/密钥相关/阿里云密钥获取.md)
- [百度云](../../Serverless-Devs/密钥相关/百度云密钥获取.md)
- [AWS](../../Serverless-Devs/密钥相关/AWS密钥获取.md)
- [Azure](../../Serverless-Devs/密钥相关/Azure密钥获取.md)
- [Google Cloud](../../Serverless-Devs/密钥相关/GoogleCloud密钥获取.md)
- [华为云](../../Serverless-Devs/密钥相关/华为云密钥获取.md)
- [腾讯云](../../Serverless-Devs/密钥相关/腾讯云密钥获取.md)