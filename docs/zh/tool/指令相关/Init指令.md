# Init指令帮助文档

如果您想使用Serverless Devs Tool，您可以直接在项目目录创建对应的Yaml。当然，如果您还没有一个项目，您可以直接通过`s init`指令出初始化一个项目。

- [应用中心初始化项目](#应用中心初始化项目)
- [初始化Git项目](#初始化Git项目)
- [帮助信息](#帮助信息)

## 应用中心初始化项目

Serverless Devs Tool是有着完整的应用中心系统的，您可以在应用中心搜索相关的资源并且初始化。详情可参考[应用中心的搜索能力](Search指令.md)

例如我们此时，通过`s search`搜索了一个`fc`的相关组件：

![](https://images.serverlessfans.com/s-tool/zh/s-search-fc.jpg)

然后我们就可以直接通过`s init fc-event-nodejs10`初始化这样一个项目：

![](https://images.serverlessfans.com/s-tool/zh/s-init-fc.jpg)

## 初始化Git项目

例如，我们在Github上有一个项目，地址是：

```
https://github.com/anycodes/nodejs10_demo
```

此时，我们可以直接通过`

```
s init https://github.com/anycodes/nodejs10_demo
```

进行初始化，例如：

![](https://images.serverlessfans.com/s-tool/zh/s-init-git.jpg)

在图中，可以看到，我们已经非常轻松地将项目下载下来。此时您就已经完成了一个项目的初始化操作。当然，如果项目中没有对应的Yaml信息，用来描述资源，您依旧没办法顺利部署，所以在非`应用中心`项目部署的时候，还需要您确定是否有正确的资源描述文档。

## 帮助信息

当然，您还可以通过`s init`或者`s init -h`调出帮助文档信息：

![](https://images.serverlessfans.com/s-tool/zh/s-init-help.jpg)