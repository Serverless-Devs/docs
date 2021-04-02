# 命令行使用

当使用者使用命令行工具时，可以通过`s`指令，查看整体帮助信息:

```shell script
$ s

Usage: s [options] [command]

  _________                               .__
 /   _____/ ______________  __ ___________|  |   ____   ______ ______
 \_____  \_/ __ \_  __ \  \/ // __ \_  __ \  | _/ __ \ /  ___//  ___/
 /        \  ___/|  | \/\   /\  ___/|  | \/  |_\  ___/ \___ \ \___ \
/_______  /\___  >__|    \_/  \___  >__|  |____/\___  >____  >____  >
        \/     \/                 \/                \/     \/     \/

Welcome to the Serverless Devs Cli.

Documents: https://www.github.com/serverless-devs/docs

Options:
  -t, --template           Specify yaml document
  --skip-actions           Skip the extends section
  -v, --version            Output the version number
  -h, --help               Display help for command

Commands:
  config                   Configure cloud service account.
  init                     Initializing a project.
  set                      Settings for the tool.
  cli                      Command line operation through yaml free mode.
  exec                     Subcommand execution analysis

```

## config指令

`config`指令是密钥信息相关的指令，包括密钥的配置、密钥的查看以及密钥的修改、删除等。

当我们执行`s config`之后，可以进行相关帮助信息的查看：

```shell script
$ s config

Usage: s config [commands] [options]

You can configure provider accounts, including Alibaba Cloud, Baidu Cloud, Huawei Cloud, Tencent Cloud, etc.

Options:
  -h, --help  Display help for command

Commands:
  add         Add an account.
  get         Get accounts.
  delete      Delete an account.
  update      Update an account.
```

### config add 命令

通过`config add`命令，可以进行密钥的配置，系统会默认为使用者提供部分云厂商的密钥模板，如果无法满足用户使用，可以通过`Custom`选项进行自定义密钥的`Key-Value`设定

通过`-h/--help`可以查看到配置帮助：

```shell script
$ s config add -h

Usage: s config add [options] [name]

You can add an account.

    Example:
        $ s config add
        $ s config add --AccessKeyID ****** --AccessKeySecret ****** --AccountID ******
        $ s config add --AccessKey ****** --SecretKey ******

    Configuration parameters for cloud vendors:
        alibaba: AccountID, AccessKeyID, AccessKeySecret
        aws: AccessKeyID, SecretAccessKey
        azure: KeyVaultName, TenantID, ClentID, ClientSecret
        baidu: AccessKeyID, SecretAccessKey
        huawei: AccessKey, SecretKey
        google: PrivateKeyData
        tencent: AccountID, SecretID, SecretKey

Options:
  -a, --alias-name [name]    Key pair alias, if the alias is not set, use default instead
  --AccountID [value]        Configure the AccountID
  --AccessKeyID [value]      Configure the AccessKeyID
  --AccessKeySecret [value]  Configure the AccessKeySecret
  --SecretID [value]         Configure the SecretID
  --SecretKey [value]        Configure the SecretKey
  --SecretAccessKey [value]  Configure the SecretAccessKey
  --KeyVaultName [value]     Configure the KeyVaultName
  --TenantID [value]         Configure the TenantID
  --ClientID [value]         Configure the ClientID
  --ClientSecret [value]     Configure the ClientSecret
  --PrivateKeyData [value]   Configure the PrivateKeyData
  -h, --help                 Display help for command
```

可以通过`config add`直接进行密钥的添加：

```shell script
$ s config add 

? Please select a provider: (Use arrow keys)
❯ Alibaba Cloud (alibaba) 
  AWS (aws) 
  Azure (azure) 
  Baidu Cloud (baidu) 
  Google Cloud (google) 
  Huawei Cloud (huawei) 
  Tencent Cloud (tencent) 
  Custom (others) 
```

当使用者选择某个选项之后，系统会进行交互式引导：

```shell script
s config add 

? Please select a provider: Alibaba Cloud (alibaba)

Config document: https://github.com/Serverless-Devs/docs/blob/master/zh/others/provider-config

? AccountID **********
? AccessKeyID **********
? AccessKeySecret **********
? Please create alias for key pair. If not, please enter to skip default
```

也可以通过命令式直接进行密钥的添加：
```shell script
$ s config add --AccessKeyID ****** --AccessKeySecret ****** --AccountID ******
```

- 常见云厂商密钥配置内容

```
alibaba:    AccountID, AccessKeyID, AccessKeySecret,
aws:        AccessKeyID, SecretAccessKey,
baidu:      AccessKeyID, SecretAccessKey,
huawei:     AccessKeyID, SecretAccessKey,
azure:      KeyVaultName, TenantID, ClientID, ClientSecret,
tencent:    AccountID, SecretID, SecretKey,
google:     PrivateKeyData
```

- 通过环境变量获取密钥方法： 这一部分可能会根据不同的文档有不同的可能性，所以需要参考对应的文档进行环境变量对应的`Key-Value`确定。

- 常见云厂商密钥获取地址：
    - [阿里云](./others/provider-config/alibabacloud.md)
    - [百度云](./others/provider-config/baiducloud.md)
    - [AWS](./others/provider-config/aws.md)
    - [Azure](./others/provider-config/azure.md)
    - [Google Cloud](./others/provider-config/gcp.md)
    - [华为云](./others/provider-config/huaweicloud.md)
    - [腾讯云](./others/provider-config/tencentcloud.md)


### config get 命令

通过`config get`指令，您可以获得配置过的账号信息。

通过`-h/--help`可以查看到配置帮助：

```shell script
$ s config get -h

Usage: s config get [options] [name]

You can get accounts.
 
     Example:
        $ s config get -l
        $ s config get -a demo
 

Options:
  -a, --alias-name [name]  Key pair alia, if the alias is not set, use default instead
  -l, --list               Show user configuration list
  -h, --help               Display help for command
```

### config delete 命令

通过`config delete`指令，您可以删除配置过的账号信息。

通过`-h/--help`可以查看到配置帮助：

```shell script
$ s config delete -h

Usage: s config delete [options] [name]

You can delete an account.

     Example:
        $ s config delete -a demo


Options:
  -a , --alias-name [name]  Key pair alia, if the alias is not set, use default instead
  -h,--help                 Display help for command
```

### config update 命令

通过`config update`指令，您可以修改配置过的账号信息。

通过`-h/--help`可以查看到配置帮助：

```shell script
$ s config update -h

Usage: s config  update [options] [name]

You can update an account.
 
     Example:
        $ s config update -a demo
        $ s config update -a demo --AccountID ************


Options:
  -a , --alias-name [name]   Key pair alia, if the alias is not set, use default instead
  --AccountID [value]        Configure the AccountID
  --AccessKeyID [value]      Configure the AccessKeyID
  --AccessKeySecret [value]  Configure the AccessKeySecret
  --SecretID [value]         Configure the SecretID
  --SecretKey [value]        Configure the SecretKey
  --SecretAccessKey [value]  Configure the SecretAccessKey
  --KeyVaultName [value]     Configure the KeyVaultName
  --TenantID [value]         Configure the TenantID
  --ClientID [value]         Configure the ClientID
  --ClientSecret [value]     Configure the ClientSecret
  --PrivateKeyData [value]   Configure the PrivateKeyData
  -h, --help                 Display help for command
```

## init指令

`init`指令是初始化Serverless项目的脚手架。

当我们执行`s init -h`之后，可以进行相关帮助信息的查看：

```shell script
$ s init -h

Usage: s init [options] [name | url]

Initialize a new project based on a template. You can initialize the application that conforms to the serverless devs project specification through GitHub, or you can initialize the application provided by the source by configuring the source.

    Example:
        $ s init
        $ s init project
        $ s init git@github.com:foo/bar.git
        $ s init https://github.com/foo/bar.git    

Options:
  -d, --dir [dir]            Where to output the initialized app into (default: ./<ProjectName> )
  -r, --registry [url]       Use specify registry  
  -h, --help                 Display help for command
```

当我们直接执行`s init`，可以进入初始化引导功能：

```shell script
$ s init
? Hello, serverlessor.
  Which template do you like? … 

 ⊙ Hello World Example
❯ Node.js 12 HTTP : An Alibaba Cloud FC example
  Node.js 12.x HTTP : An AWS Lambda example
  Node.js 12 HTTP : A Tencent Cloud SCF example

 ⊙ Web Framework Example
  Express : A Express example for Alibaba Cloud FC
  Flask : A Flask example for Alibaba Cloud FC
  Midway-FaaS : A front and rear integration example for Alibaba Cloud FC

 ⊙ Serverless Dev template
  Application : Serverless Devs application template
  Component : Serverless Devs component template
  Plugin : Serverless Devs plugin template
```

## cli指令

`cli`指令是去Yaml化的命令行模式，即可以通过命令行直接使用Serverless Devs的组件，而不需要依赖Yaml文件。

当我们执行`s cli -h`之后，可以进行相关帮助信息的查看：

```shell script
$ s cli -h

Usage: s cli [component] [command] [options]

Directly use serverless devs to use components, develop and manage applications without yaml configuration

    Example:
        $ s cli fc list-service
        $ s cli fc list-function --service-name my-service
        $ s cli fc deploy -p "{/"function/": /"function-name/"}" --service-name my-service

Options:
  -p, --param [component-config]     Component props which in Yaml file
  -h, --help                         Display help for command
```

## exec指令

`exec`是执行组件的子命令的指令。

当我们执行`s exec -h`之后，可以进行相关帮助信息的查看：

```shell script
$ s exec -h

Usage: s exec [service-name] [options] -- [component-sub-command] [options]

Run a component sub command on an app

    Example:
        $ s exec fc -t test.yaml -- log --tail
        $ s exec fc -- deploy

Options:
  -h, --help                         Display help for command
```

一般情况下该指令可以进行有效的简化，例如：`s exec fc -- deploy`可以简化为`s fc deploy`，但是当存在Serverless Devs开发者工具和组件某些参数冲突时则不能简化，例如`s exec fun -t test.yaml -- -t template.yaml`

## set指令

`set`指令是对工具进行相关配置的指令。

当我们执行`s set -h`之后，可以进行相关帮助信息的查看：

```shell script
$ s set -h

Usage: s set [commands] [options]

You can make some default settings for the tool here.

Options:
  -h, --help    Display help for command

Commands:
  color         Control color output
  language      Output language switch
  analysis      Upload your usage habits to help us improve our products
  registry      Config registry for Serverless Devs
```

### set color 命令

配置输出颜色，通过`-h/--help`可以看到效果：

```shell script
$ s set color -h

Usage: s set color [options]

Control color output.

     Example:
        # Default color output：
          $ s set color enable
        # System color output: 
          $ s set color disable

Options:
  -h, --help  Display help for command
```

### set language 命令

配置语言，通过`-h/--help`可以看到效果：

```shell script
$ s set language -h

Usage: s set language [language]

Set language.

     Example:
        $ s set language zh
        $ s set language en

Options:
  -h, --help  Display help for command
```

### set analysis 命令

配置数据上报习惯，通过`-h/--help`可以看到效果：

```shell script
$ s set analysis -h

Usage: s set analysis [options]

Upload your usage habits to help us improve our products

    Example:
        # Upload your usage habits:
            $ s set analysis enable
        # Do not upload your usage habits: 
            $ s set analysis disable

Options:
  -h, --help  Display help for comman
```

### set registry 命令

配置源，通过`-h/--help`可以看到效果：

```shell script
$ s set registry -h

Usage: s set registry [options]

Upload your usage habits to help us improve our products

    Example:
        $ s set registry default
        $ s set registry https://registry.serverlessfans.cn/

Options:
  -h, --help  Display help for comman
```


