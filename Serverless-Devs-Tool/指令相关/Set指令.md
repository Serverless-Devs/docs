# Set指令帮助文档

通过`s set`指令，您可以对Serverless Devs Tool做一些特性化的设置。这其中包括但是不限于：

- [设置语言](#设置语言)
- [设置输出颜色](#设置输出颜色)
- [设置数据上报](#设置数据上报)
- [帮助信息](#帮助信息)

## 设置语言

### 设置语言使用方法

您可以通过`s set language`来设置命令行工具的默认语言。目前系统支持两种语言：

|    | 指令  | 
|  ----  | ----  | 
| 中文  | zh |
| 英文  | en | 

例如您如果想将本工具设置成默认中文输出，您可以使用：

```
s set language zh
```

同理，如果您想设置成英文输出，则可以是：

```
s set language en
```

### 获取帮助信息

您可以通过指令`s set language -h`获取帮助信息：

![](https://images.serverlessfans.com/s-tool/zh/s-set-language-help.jpg)

## 设置输出颜色


### 设置输出颜色使用方法

目前命令行工具的输出是默认带有颜色的，不同的颜色表示不同的信息，例如蓝色/紫色表示的是输出信息，白色表示的是日志信息，黄色/橙色的表示的是警告信息，红色的是表示错误信息，绿色表示的是成功信息。

但是有很多命令行工具对颜色输出并不友好，同时也有一些用户会自己给命令行增加背景颜色，此时如果增加颜色输出会造成额外的困惑，所以提供了无颜色输出以及有颜色输出模式。

如果您想设置无颜色输出，您可以：

```
s set output-color disable
```

如果您想设置有颜色输出，您可以：

```
s set output-color enable
```

### 获取帮助信息

您可以通过指令`s set output-color -h`获取帮助信息：

![](https://images.serverlessfans.com/s-tool/zh/s-set-output-color-help.jpg)


## 设置数据上报

### 设置数据上报使用方法

为了更加了解每个用户的使用习惯，我们在工具中进行了部分的埋点，用来统计用户的使用习惯，以便我们更好的改进产品。

当然，这里的使用习惯绝对不包括用的个人敏感数据，例如绝对不包括密钥信息等！

这些使用习惯通常包括：用户的总使用次数，配置的云厂商名称，以及指令的使用次数等。

当然，我们也考虑到有一些用户并不希望我们搜集他的一些行为数据，我们就提供了这个数据上报的设置方案。

如果您不想我们搜集并上报您的行为数据，可以执行：

```
s set analysis disable
```

如果您愿意帮助我们改善产品，您可以开启上报行为的功能，以便我们更好地完善工具：

```
s set analysis enable
```

### 获取帮助信息

您可以通过指令`s set analysis -h`获取帮助信息：

![](https://images.serverlessfans.com/s-tool/zh/s-set-analysis-help.jpg)

## 帮助信息

当然，您还可以通过`s set`或者`s set -h`调出帮助文档信息：

![](https://images.serverlessfans.com/s-tool/zh/s-set-help.jpg)