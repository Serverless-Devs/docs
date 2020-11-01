# 简介

**Serverless Devs App Store** 是一个集 Serverless 应用在线搜索，一键部署以及资源可视化编辑于一体的应用中心产品。该应用中心拥有海量的生产级项目模板、案例模板，开发者可以自由选择，并将项目一键部署到指定的云平台上

您在[安装Serverless Devs Tool](../Serverless-Devs-Tool/其他文档/工具安装.md)之后，可以通过`s gui`唤起该页面。当然，您也可以通过一些子命令进行该页面的唤起，例如：

- 在`s search`的时候，可以通过`s search --gui`唤起GUI页面进行搜索；
- 在`s init`的时候，可以通过`s init --gui`唤起GUI页面进行初始化；

整个应用中心的页面首页：

![](https://images.serverlessfans.com/s-gui/docs/app-store-index.jpg)

可以点击每个组件/插件/应用的标题（关于三者区别[可以查看文档](../Serverless-Devs/Package相关/Package概念区分.md)），进入到详情:

![](https://images.serverlessfans.com/s-gui/docs/app-store-content.jpg)

当然，我们也可以通过点击快速部署等按钮，进入到可视化Yaml编辑页面：

![](https://images.serverlessfans.com/s-gui/docs/app-store-yaml.jpg)

在这个页面，您可以通过左侧的表单内容填写，来对Yaml进行可视化编写，所见即所得，当我们完成编辑之后，可以点击保存，保存Yaml到本地，也可以直击部署：

![](https://images.serverlessfans.com/s-gui/docs/app-store-demo.jpg)


-----

- 更多链接
  - 一个相对完整的例子：[入门案例](./快速开始.md)    
  - 更多应用/组件/插件汇总：[Package汇总](./Package汇总.md)    



