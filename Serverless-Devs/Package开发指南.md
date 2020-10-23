# 开发package指南

感谢您准备开发Serverless Devs Tool Package，也非常期待您开发完成，可以将这个Package发布到应用中心，让更多人可以使用，给更多人帮助。

开发一个Package的基本流程是：

![](https://images.serverlessfans.com/s-tool/zh/how-to-dev-package-1.jpg)


- [初始化Package](#初始化Package)
- [项目开发](#项目开发)
- [账号登录](#账号登录)
- [发布Package](#发布Package)
- [不发布Package如何使用](#不发布Package如何使用)

## 初始化Package

此时您可以参考[platform指令文档中的初始化项目](../开发者工具/指令相关/Platform指令.md#初始化项目)

您可以在此处初始化一个模板，这个模板指的是，您要将应用/组件/插件发布到应用商城的模板。

例如，我想初始化一个组件，我可以执行`s platform init -t Component`，得到结果：

![](https://images.serverlessfans.com/s-tool/zh/s-platform-init-component.jpg)

其中`-t\--type`的取值包括：

- 组件：Component
- 插件：Plugin
- 应用：Application

## 项目开发

项目开发过程中，您需要严格遵守项目开发文档：

- [组件开发文档](开发文档/Component开发.md)
- [插件开发文档](开发文档/Plugin开发.md)
- [应用开发文档](开发文档/Application开发.md)

> 额外说明，如果您在开发过程中未按照我们的文档来进行相关的规范，应用中心有权在未来的有权屏蔽该package的使用


## 账号登录

如果您已经登陆过账号则可以跳过该步骤，如果您未登陆过账号，您需要在此处进行登录。

此时您可以参考[platform指令文档中的登陆账号部分](../开发者工具/指令相关/Platform指令.md#登陆账号)

您可以通过`s platform login`指令进行登陆操作。

![](https://images.serverlessfans.com/s-tool/zh/s-platform-login.jpg)

在输出的交互选项中，填写自己的平台账号密码即可完成登陆。

当然您也可以直接通过命令式进行登录，例如：

```
s platform login -u username -p password
```

> 如果您没有账号，您需要先进行注册账号：`s platform login --gui`之后，通过选择注册选项即可进行注册

## 发布Package

此时您可以参考[platform指令文档中的发布部分](../开发者工具/指令相关/Platform指令.md#登陆账号)

当您开发完成一个package（组件/插件/应用），您可以通过`s platform publish`将其发布到应用中心：

![](https://images.serverlessfans.com/s-tool/zh/s-platform-publish.jpg)

这里要额外声明：

- 您只要在这里发布了包，就意味着您已经将您的项目发布到了应用中心，是所有人都可以查看到的
- 如果您因为自己意外将私密包发布到应用中心，您需要立即删除其版本，并且马上联系我们官方邮箱，进行残留数据清理
- 如果您因为个人原因将私密包分享到应用中心，造成个人/组织损失，Serverless Devs Tool概不负责

## 不发布Package如何使用

### 组件的使用方法

您如果开发完成项目，不想直接对外开放，仅是想自己使用，您可以通过直接引入项目绝对路径的方法使用。例如：

![](https://images.serverlessfans.com/s-tool/zh/how-to-dev-package-2.jpg)
