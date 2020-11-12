# Platform instructions documentation

Platform is the bridge between the command line tools and the application center, you can use the commands in the Platform to publish, upgrade, delete related components, plugins, applications (about applications, for the concepts of components and plugins, see [related Documents ](../../others/package/package_type.md).

- [Login account ](#Login-account)
- [Initialize a project ](#Initialize-a-project)
- [Release package ](#Release-package)
- [Delete a package ](#Drop-a-package)
- [Help information ](#Help-information)

## Login account

You can use `s platform login `command to log in.
[](https://images.serverlessfans.com/s-tool/zh/s-platform-login.jpg)

In the output of interactive options, fill in your platform account password to complete login.

You can also log on directly by using the command, for example:

```
s platform login -u username -p password
```

Of course, you can also pass `s platform login -h `bring up help document information:

[](https://images.serverlessfans.com/s-tool/zh/s-platform-login-help.jpg)

> The difference between the account password and the password configured in the Config section is as follows:

- The account password for the Platform login is the account password for the Serverless Devs Platform. `s platform publish `command to publish/update a package, you can also `s platform delete `instruction to delete the specified package. If you do not want to contribute to the Serverless Devs Tool/Serverless Devs, you can ignore this capability;
- The key configured in the Config is a cloud vendor's key information. Information that you need when using the widget.

## Initialize a project

You can initialize a template here that refers to the template for publishing applications/Components/plugins to the application Mall (you can refer to developing applications/Components/plugins [related Documents ](../../others/package/package_dev.md).

For example, I want to initialize a component, I can execute `s platform init -t Component `, get the result:

[](https://images.serverlessfans.com/s-tool/zh/s-platform-init-component.jpg)

Where `-t\--type `valid values for include:

- Component: Component
- plugins
- Application: Application

Of course, you can also pass `s platform init -h `bring up help document information:

[](https://images.serverlessfans.com/s-tool/zh/s-platform-init-help.jpg)

> On software applications, applications, components, and plugin the concept of View [related Documents ](../../others/package/package_type.md).

## Release package

After you have developed a package (component/plugin/application), you can use `s platform publish `publish it to Application Center:
[](https://images.serverlessfans.com/s-tool/zh/s-platform-publish.jpg)

Additional statement is required here:

- Once you publish a package here, it means that you have published your project to the application center, which everyone can view.
- If you have accidentally published your private package to the application center, you need to delete the version immediately and contact us at once to clear the residual data.
- If you share the private package to the application center for personal reasons, resulting in personal or organizational losses, Serverless Devs Tool is not responsible

Of course, you can also pass `s platform publish -h `bring up help document information:
[](https://images.serverlessfans.com/s-tool/zh/s-platform-publish-help.jpg)

## Drop a package

You can delete a published Package.

You need to specify the following information when you delete the bucket:

- `-nv\--name-version `: Package name @ version, for example `fc-jiangyu@0.0.19`
- `-t\--type `: The package type, including Component, Plugin, and Application.
- `-p\--provider `: cloud vendor

Examples:

I want to delete, I have released Ali Cloud's `fc-jiangyu `component, version is `0.0.19 `, I can write:

```
s platform delete -nv fc-jiangyu@0.0.19 -p alibaba -t component
```

Response:
[](https://images.serverlessfans.com/s-tool/zh/s-platform-delete-content.jpg)

Of course, you can also pass `s platform delete -h `bring up help document information:
[](https://images.serverlessfans.com/s-tool/zh/s-platform-delete-help.jpg)

## Help information

Of course, you can also pass `s platform `or `s platform -h `bring up help document information:

[](https://images.serverlessfans.com/s-tool/zh/s-platform-help.jpg)

