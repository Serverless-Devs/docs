# Develop the package guide

Thank you for preparing to develop the Serverless Devs Tool Package. We look forward to seeing that you can publish this Package to the application center to help more people.

The basic process of developing a Package is as follows:
[](https://images.serverlessfans.com/s-tool/zh/how-to-dev-package-1.jpg)

- [Initialize a Package ](#Initialize-a-Package)
- [Project Development ](#Develop-projects)
- [Account login ](#Account-login)
- [Publish Package ](#Publish-Package)
- [Use without publishing a Package ](#Use-without-publishing-a-Package)

## Initialize a Package

At this point you can refer [initialization items in the platform directive documentation ](../../tool/commands/platform.md#initialize-a-project)

You can initialize a template, which is the template for publishing applications, components, and plugins to the application marketplace.

For example, I want to initialize a component, I can execute `s platform init -t Component `, get the result:
[](https://images.serverlessfans.com/s-tool/zh/s-platform-init-component.jpg)

Where `-t\--type `valid values for include:

- Component: Component
- Plugins
- Application: Application

## Develop projects

During project development, you must strictly abide by the following project development documents:

- [Component Development documentation ](./devs_docs/component.md)
- [Plugin development documentation ](./devs_docs/plugin.md)
- [Application development documentation ](./devs_docs/application.md)

> Additionally, if you do not follow the relevant specifications in our documentation during the development process, the application center has the right to block the use of the package in the future.

## Account login

If you have already logged in to the account, you can skip this step. If you have not logged in to the account, you need to log in here.

At this point you can refer [login account section in the platform instructions document ](../../tool/commands/platform.md#login-account)

You can use `s platform login `command to log in.
[](https://images.serverlessfans.com/s-tool/zh/s-platform-login.jpg)

In the output of interactive options, fill in your platform account password to complete login.

You can also log on directly by using the command, for example:

```
s platform login -u username -p password
```

> If you do not have an account, you need to register an account first: `s platform login --gui `then, you can register by selecting the registration option

## Publish Package

At this point you can refer [release section in the platform directive document ](../../tool/commands/platform.md#login-account)

After you have developed a package (component/plugin/application), you can use `s platform publish `publish it to Application Center:
[](https://images.serverlessfans.com/s-tool/zh/s-platform-publish.jpg)

Additional statement is required here:

- Once you publish a package here, it means that you have published your project to the application center, which everyone can view.
- If you have accidentally published your private package to the application center, you need to delete the version immediately and contact us at once to clear the residual data.
- If you share the private package to the application center for personal reasons, resulting in personal or organizational losses, Serverless Devs Tool is not responsible

## Use without publishing a Package

### Usage of components

After you create a project, you can import the absolute path of the project to the console. Examples:
[](https://images.serverlessfans.com/s-tool/zh/how-to-dev-package-2.jpg)

