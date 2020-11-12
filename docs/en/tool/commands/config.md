# Config command help document

The Config directive is used to configure account information. In Serverless Devs Tool, you can use Config to configure global keys for multiple clouds, or you can create or configure temporary key information in the current project directory.

- [config add ](#Config-add-directive)
- [config get ](#Config-get-directive)
- [config delete ](#Config-delete-directive)
- [config update ](#Config-update-directive)
- [Related description ](#Additional-information)
- [Help information ](#Help-information)
- [Cloud vendor key access solution ](#Cloud-vendor-key-access-solution)

## Config add directive

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
[](https://images.serverlessfans.com/s-tool/zh/s-config-add.jpg)

- Enter the corresponding parameters as required.
[](https://images.serverlessfans.com/s-tool/zh/s-config-add-select.jpg)

   > The last content to interact with is an alias. This content is optional. `Default `, in theory `cloud vendor + alias `the combination of is unique.

- Finally, the system will let you preview the results and store the input in the system.
[](https://images.serverlessfans.com/s-tool/zh/s-config-add-select-result.jpg)

### Command addition

By running the add secret information command, you can easily and quickly configure the secret information. Take Alibaba Cloud as an example:
[](https://images.serverlessfans.com/s-tool/zh/s-config-add-direct.jpg)

The following table lists the different settings for different cloud vendors:

```
alibaba: AccountID, AccessKeyID, AccessKeySecret
 aws: AccessKeyID, SecretAccessKey
 baidu: AccessKeyID, SecretAccessKey
 huawei: AccessKey, SecretKey
 tencent: AccountID, SecretID, SecretKey
```

### Other key configuration methods

You can create a project in `access.yaml `file to configure key information, for example:

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

### Query help information about Serverless Workflow

You can run commands `s config add -h `obtain help information:
[](https://images.serverlessfans.com/s-tool/zh/s-config-add-help.jpg)

## Config get directive

By `s config get `instruction to get the account information that has been configured.

- For example, to obtain all key information: `s config get -l`
[](https://images.serverlessfans.com/s-tool/zh/s-config-get-l.jpg)

   > If the format is cloud vendor (identify), the configuration is global, such as Alibaba in the figure. If the format is project, the current project configuration is used.

- For example, to obtain the key information of a cloud vendor: `s config get -p alibaba`
[](https://images.serverlessfans.com/s-tool/zh/s-config-get-provider.jpg)

   > By default, the system generates information about the cmk and the CMK in the current project.

- To obtain the information about a specified key, use the Baidu demo in the preceding figure as an example: `s config get -p baidu -a demo`
[](https://images.serverlessfans.com/s-tool/zh/s-config-get-provider-alias.jpg)

Of course, you can also pass `s config get `or `s config get -h `bring up help document information:
[](https://images.serverlessfans.com/s-tool/zh/s-config-get-help.jpg)

## Config delete directive

By `s config delete `instruction to delete the account information of a specific cloud vendor.

Specify the cloud vendor and alias. If you do not specify the alias, you can use the default alias `default `).

For example, delete `alibaba Cloud `of `release `the key information. Valid values:

```
s config delete -p alibaba -a release
```

Again, for example, delete `alibaba Cloud `the information of the default key for [[[]]] can be either as follows:

```
s config delete -p alibaba -a default
```

> You can only delete the globally configured key information. That is `s config add `you cannot delete a temporary key of the current project.

Of course, you can also pass `s config delete `or `s config delete -h `bring up help document information:
[](https://images.serverlessfans.com/s-tool/zh/s-config-delete-help.jpg)

## Config update directive

By `s config update `instruction, you can update the account information of the specified cloud vendor.

And `s config add `the instruction is similar, `update `methods also have two forms, interactive and imperative.

### Interactive modification

When only a vendor and alias are specified, interactive modification can be invoked:
[](https://images.serverlessfans.com/s-tool/zh/s-config-update-select.jpg)

Here, you can modify the corresponding field information according to the system prompts. If you do not modify the configuration, press enter to skip the configuration.

### Imperative modification

In order to give everyone more convenience, the imperative modification method has also been added here, that is, to specify any other corresponding information while providing Provider (cloud vendor) and Alias (Alias):

```
alibaba: AccountID, AccessKeyID, AccessKeySecret
 aws: AccessKeyID, SecretAccessKey
 baidu: AccessKeyID, SecretAccessKey
 huawei: AccessKey, SecretKey
 tencent: AccountID, SecretID, SecretKey
```

The system will modify the corresponding content. For example, replace `AccessKeyID `to modify:
[](https://images.serverlessfans.com/s-tool/zh/s-config-update-direct.jpg)

Of course, you can also pass `s config update `or `s config update -h `bring up help document information:
[](https://images.serverlessfans.com/s-tool/zh/s-config-update-help.jpg)

## Additional information

### Use Key Information

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

### Key information usage sequence

If you use a cloud vendor, the project contains the temporary key information and the global key information contains the key with the same alias. The system policies are as follows:
[](https://images.serverlessfans.com/s-tool/zh/s-config-extend-sort.jpg)

## Help information

Of course, you can also pass `s config `or `s config -h `bring up help document information:
[](https://images.serverlessfans.com/s-tool/zh/s-config-help.jpg)

## Cloud vendor key access solution

- [Alibaba Cloud ](../../others/access/alibaba_cloud.md)
- [Baidu Cloud ](../../others/access/baidu_cloud.md)
- [AWS ](../../others/access/aws.md)
- [Azure ](../../others/access/azure.md)
- [Google Cloud ](../../others/access/google_cloud.md)
- [Huawei Cloud ](../../others/access/huawei_cloud.md)
- [Tencent Cloud ](../../others/access/tencent_cloud.md)
