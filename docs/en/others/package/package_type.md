# Components, applications, and plugins

In the Serverless Devs Tool and application center, we have three interesting concepts: components, applications, and plugins.

First of all, for sure, Serverless devtool is a project where components and plugins coexist. Therefore, the differences between components and plugins are:

|  | Component | Plugin |
| ---- | ---- | ---- |
| Can be used independently | Granted | Not granted |
| Whether there is dependency | Dependent projects | Item |

Well, such a simple table may be difficult to describe clearly, so we will use a practical example:
![](https://images.serverlessfans.com/s-tool/zh/component-application-plugin-1.jpg)

In this Yaml, we can see that there is a project here that is `Projectname `, this project depends on the component `stest `, in the project execution `deploy `method (this method is `stest `component defined by the component itself, perform a `stest_plugin `component. The relationships among components, plugins, and Yaml files are as follows:
![](https://images.serverlessfans.com/s-tool/zh/component-application-plugin-2.jpg)

In other words, a Yaml file can support the deployment of multiple projects. Each project corresponds to a component that is used to deploy each project. However, some components may not be able to complete a task better in some cases, so plugins/hooks are required at this time. For example, when we deploy a static website project, we can put this static website project through `Website `the component is deployed online, but if the project is a Vue project, we may want `npm build `at this time we can be in `Website `add a plugin on the component. When the component is deployed, the plugin is executed first. This method will actually play an interesting role in our project engineering or CICD process.

So, what is an application? In fact, the definition of an application is quite extensive. You can think of an application as a Yaml file that includes the code that comes with the Yaml file and includes the resource description file (Yaml file). Etc. In general, it is as follows:
![](https://images.serverlessfans.com/s-tool/zh/component-application-plugin-3.jpg)

We can think of an application `hello_world `an audio and video processing case, deploy an online transcoding capability, deploy a......

The concepts of components, applications, and plugins are not complex. Take a common example as an example:

An application is a mobile phone APP that takes photos. This APP has many components, such as the component for opening a camera, the component for taking photos, and the component for storing photos, when we store photos, we need to extract some features from the photos taken by the user by default, such as extracting the shooting time and location. However, these capabilities are not provided by the photo storage component, in this case, we can put a plugin that extracts the shooting time and location before storing the photo.

In fact, there are certain differences between components, plugins and applications, but in some extreme cases, there is no very clear difference, so you don't have to worry too much about the specific and meticulous differences in these contents: It's easy to use, it's OK to use, it's easy to use, simple and fast, it's OK.

