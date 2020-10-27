# Platform指令帮助文档

Platform是命令行工具与应用中心连接的桥梁，您可以通过Platform中的相关指令，来发布、升级、删除相关组件、插件、应用（关于应用、组件和插件的概念可以查看[相关文档](../../Serverless-Devs/Package相关/Package概念区分.md)）。

- [登陆账号](#登陆账号)
- [初始化项目](#初始化项目)
- [发布包](#发布包)
- [删除包](#删除包)
- [帮助信息](#帮助信息)

## 登陆账号

您可以通过`s platform login`指令进行登陆操作。

![](https://images.serverlessfans.com/s-tool/zh/s-platform-login.jpg)

在输出的交互选项中，填写自己的平台账号密码即可完成登陆。

当然您也可以直接通过命令式进行登录，例如：

```
s platform login -u username -p password
```

当然，您还可以通过`s platform login -h`调出帮助文档信息：

![](https://images.serverlessfans.com/s-tool/zh/s-platform-login-help.jpg)

> 这里的账号密码和Config中配置的账号密码区别：
> - Platform login的账号密码是Serverless Devs平台的账号密码，在此处做登陆操作之后，您可以通过`s platform publish`指令发布/更新包，也可以通过`s platform delete`指令删除指定包。如果您并不想为Serverless Devs Tool/Serverless Devs贡献力量，你可以无视该能力；
> - Config中配置的密钥信息，是云厂商的密钥信息。 是您在使用组件时所需要的相关信息。

## 初始化项目

您可以在此处初始化一个模板，这个模板指的是，您要将应用/组件/插件发布到应用商城的模板(您可以参考开发应用/组件/插件[相关文档](../../Serverless-Devs/Package相关/Package开发指南.md))。

例如，我想初始化一个组件，我可以执行`s platform init -t Component`，得到结果：

![](https://images.serverlessfans.com/s-tool/zh/s-platform-init-component.jpg)

其中`-t\--type`的取值包括：

- 组件：Component
- 插件：Plugin
- 应用：Application

当然，您还可以通过`s platform init -h`调出帮助文档信息：

![](https://images.serverlessfans.com/s-tool/zh/s-platform-init-help.jpg)

> 关于应用、组件和插件的概念可以查看[相关文档](../../Serverless-Devs/Package相关/Package概念区分.md)

## 发布包

当您开发完成一个package（组件/插件/应用），您可以通过`s platform publish`将其发布到应用中心：

![](https://images.serverlessfans.com/s-tool/zh/s-platform-publish.jpg)

这里要额外声明：

- 您只要在这里发布了包，就意味着您已经将您的项目发布到了应用中心，是所有人都可以查看到的
- 如果您因为自己意外将私密包发布到应用中心，您需要立即删除其版本，并且马上联系我们官方邮箱，进行残留数据清理
- 如果您因为个人原因将私密包分享到应用中心，造成个人/组织损失，Serverless Devs Tool概不负责


当然，您还可以通过`s platform publish -h`调出帮助文档信息：

![](https://images.serverlessfans.com/s-tool/zh/s-platform-publish-help.jpg)

## 删除包

您可以将已经发布的Package进行删除。

删除的时候您需要指定相关信息：

- `-n\--name`: 包名称
- `-k\--version`: 包版本
- `-t\--type`: 包类型，包括Component、Plugin、Application
- `-p\--provider`: 云厂商

例如：

我要删除，我发布过的阿里云的`fc-jiangyu`组件，版本是`0.0.19`，我则可以写：

```
s platform delete -nv fc-jiangyu@0.0.19 -p alibaba -t component
```

执行结果：

![](https://images.serverlessfans.com/s-tool/zh/s-platform-delete-content.jpg)

当然，您还可以通过`s platform delete -h`调出帮助文档信息：

![](https://images.serverlessfans.com/s-tool/zh/s-platform-delete-help.jpg)
## 帮助信息

当然，您还可以通过`s platform`或者`s platform -h`调出帮助文档信息：

![](https://images.serverlessfans.com/s-tool/zh/s-platform-help.jpg)
