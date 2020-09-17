# Search指令帮助文档

用户是可以`s search`进行相关组件、应用和插件的搜索。搜索数据来源是Serverless Devs App Store（即应用中心，应用中心是一个人人可贡献的平台，欢迎大家为Serverless贡献一份自己的力量，可参考[Platform指令文档](Platform指令.md)）。

- [搜索能力](#搜索能力)
- [帮助信息](#帮助信息)

## 搜索能力

在命令行工具进行搜索，默认是搜索应用（关于应用、组件和插件的概念可以查看[相关文档](../others/Package概念区分.md)）,例如，此时我们想要搜索`test`相关的内容，我们只需要执行`s search test`即可：

![](https://images.serverlessfans.com/s-tool/zh/s-search-test.jpg)

如果我们需要指定云厂商，我们可以添加对应的参数，不同云厂商的信息如下：

|  云厂商   | 英文名  | 简写  |
|  ----  | ----  |  ----  |
| 阿里云  | Alibaba Cloud |  alibaba |
| AWS  | AWS |  aws |
| Azure  | Azure |  azure |
| 百度云  | Baidu Cloud |  baidu |
| Google Cloud  | Google Cloud |  google |
| 华为云  | Huawei Cloud |  huawei |
| 腾讯云  | Tencent Cloud |  tencent |

我们只需要添加云厂商的简写即可，例如搜索阿里云的`test`应用，可以是：`s search test -p alibaba`，搜索的结果：

![](https://images.serverlessfans.com/s-tool/zh/s-search-test-alibaba.jpg)

当然，如果我们想要搜索其他的内容，例如插件或者组件等，我们可以增加对应的参数`-t`，例如我们要搜索阿里巴巴的`test`相关的组件（关于应用、组件和插件的概念可以查看[相关文档](../others/Package概念区分.md)）：`s search test -p alibaba -t component`，结果是：

![](https://images.serverlessfans.com/s-tool/zh/s-search-test-alibaba-component.jpg)

## 帮助信息

当然，您还可以通过`s search`或者`s search -h`调出帮助文档信息：

![](https://images.serverlessfans.com/s-tool/zh/s-search-help.jpg)