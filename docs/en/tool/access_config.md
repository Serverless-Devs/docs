# Configure key information

In Serverless Devs Tool, you can use two methods to configure the key information.

- [Configuration through commands ](#Configuration-through-commands)
- [Through file configuration ](#Through-file-configuration)
- [Use Key Information ](#Use-Key-Information)
- [Key information usage sequence ](#Key-information-usage-sequence)

## Configuration through commands

Serverless Devs Tool provides a relatively complete and clear, mostly account configuration capabilities, you can configure including Alibaba, Baidu Cloud, Huawei Cloud, AWS, Google Cloud, permanent keys of cloud service providers such as Azure and Tencent Cloud.

> For detailed method and process of configuration, you can see [config Command document ](./commands/config.md)

By `s config add `directive, you can add cloud vendor account information.

Currently, this tool supports the following global configuration vendors (in alphabetical order):

| Cloud Vendor | Name | Shorthand |
| ---- | ---- | ---- |
| Alibaba Cloud Database (DRDS) | Alibaba Cloud | alibaba |
| AWS | AWS | aws |
| Azure | Azure | Azure |
| Baiduyun | Baidu Cloud | baidu |
| Google Cloud | Google Cloud | Google |
| Huawei | Huawei Cloud | Huawei |
| Tencent | Tencent Cloud | Tencent |

### Interactive add

When you enter `s config add `the system then enters the interactive add page where you can select a cloud vendor to add interactively.

- Select Cloud Vendor
![](https://images.serverlessfans.com/s-tool/zh/s-config-add.jpg)

- Enter the corresponding parameters as required.
![](https://images.serverlessfans.com/s-tool/zh/s-config-add-select.jpg)

   > The last content to interact with is an alias. This content is optional. `Default `, in theory `cloud vendor + alias `the combination of is unique.

- Finally, the system will let you preview the results and store the input in the system.
![](https://images.serverlessfans.com/s-tool/zh/s-config-add-select-result.jpg)

### Command addition

By running the add secret information command, you can easily and quickly configure the secret information. Take Alibaba Cloud as an example:
![](https://images.serverlessfans.com/s-tool/zh/s-config-add-direct.jpg)

The following table lists the different settings for different cloud vendors:

```
alibaba: AccountID, AccessKeyID, AccessKeySecret
 aws: AccessKeyID, SecretAccessKey
 baidu: AccessKeyID, SecretAccessKey
 huawei: AccessKey, SecretKey
 tencent: AccountID, SecretID, SecretKey
```

## Through file configuration

However, in some special components, the default Config command may not be able to meet your needs. In this case, you can create a key file in the current project directory, to configure the key:

Examples:

You can create a project in `access.yaml `file, configure key information, you have a project directory:

```
|- Project
| | - access.yaml key configuration file
| | - template.yaml resource description file
| |-other files of the project
```

You can create `access.yaml `configure key information, for example:

```
# access.yaml

Key Information name 1:
    Key1: Value1
    Key2: Value2

Key Information name 2:
    Key1: Value1
    Key2: Value2
```

In this way, you can configure a custom key information, and of course, you can through this method to solve the temporary key information configuration issues.

## Use Key Information

The method of using key information is very simple, you only need to fill in the key name in the project, for example, in the project `MyTest1 `used in `test `component. Then, configure the key information `Provider `specify the cloud vendor (Baidu Cloud is specified here), in `Access `by specifying a key alias in the code:

```yaml
MyTest1:
  Component: test
  Provider: baidu
  Access: demo
  Properties:
    Region: Project Information
```

> If you do not use the alias, `Access `can be left blank, or `default`

> If you need to use the key information of the current project, you can use the key name directly.

## Key information usage sequence

If you use a cloud vendor, the project contains the temporary key information and the global key information contains the key with the same alias. The system policies are as follows:
![](https://images.serverlessfans.com/s-tool/zh/s-config-extend-sort.jpg)

## Cloud vendor key configuration

- [Alibaba Cloud ](../others/access/alibaba_cloud.md)
- [Baidu Cloud ](../others/access/baidu_cloud.md)
- [AWS ](../others/access/aws.md)
- [Azure ](../others/access/azure.md)
- [Google Cloud ](../others/access/google_cloud.md)
- [Huawei Cloud ](../others/access/huawei_cloud.md)
- [Tencent Cloud ](../others/access/tencent_cloud.md)

