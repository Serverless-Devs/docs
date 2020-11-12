# Search command help document

User is OK `S search `search for related components, applications, and plugins. The source of the search data is Serverless Devs App Store (the application center is a platform that one person can contribute to). You are welcome to contribute to Serverless. For more information, see [Platform instructions document ](Platform instruction. md)).

- [Search capability ](#Search-capability)
- [Help information ](#Help-information)

## Search capability

You can use the CLI to search for an application. For more information about applications, components, and plugins, see [related Documents ](.. /.../others/package/Package. md). For example, you want to search `test `relevant content, we only need to implement `s search test `OK:
[](https://images.serverlessfans.com/s-tool/zh/s-search-test.jpg)

If you need to specify a cloud vendor, you can add the corresponding parameters. Information for different cloud vendors is as follows:

| Cloud Vendor | Name | Shorthand |
| ---- | ---- | ---- |
| Alibaba Cloud Database (DRDS) | Alibaba Cloud | alibaba |
| AWS | AWS | aws |
| Azure | Azure | Azure |
| Baiduyun | Baidu Cloud | baidu |
| Google Cloud | Google Cloud | Google |
| Huawei | Huawei Cloud | Huawei |
| Tencent | Tencent Cloud | Tencent |

We only need to add shorthand for cloud vendors, such as search for Alibaba Cloud `test `application, which can be: `s search test -p alibaba `, the results of the search:
[](https://images.serverlessfans.com/s-tool/zh/s-search-test-alibaba.jpg)

Of course, if we want to search for other content, such as plugins or components, we can add the corresponding parameters. `-t `, for example, we want to search for Alibaba's `test `for more information about the concepts of applications, components, and plugins, see [related Documents ](.. /.../others/package/Package conceptual distinction. md): `s search test -p alibaba -t component `, the result is:
[](https://images.serverlessfans.com/s-tool/zh/s-search-test-alibaba-component.jpg)

## Help information

Of course, you can also pass `S search `or `s search -h `bring up help document information:
[](https://images.serverlessfans.com/s-tool/zh/s-search-help.jpg)

