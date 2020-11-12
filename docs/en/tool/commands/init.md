# Init instructions help document

To use the Serverless Devs Tool, create a Yaml file in the project directory. Of course, if you don't have a project yet, you can go directly through `s init `initialize a project.

- [Initialize projects in the Application Center ](#Initialize-projects-in-the-Application-Center)
- [Initialize a Git project ](#Initialize-a-Git-project)
- [Help information ](#Help-information)

## Initialize projects in the Application Center

Serverless Devs Tool is a complete application center. You can search for relevant resources and initialize them in the application center. For details, see [search for applications ](search.md)

For example, at this time, we pass `S search `searched for a `FC `related components:
![](https://images.serverlessfans.com/s-tool/zh/s-search-fc.jpg)

Then we can go directly through `s init fc-event-nodejs10 `initialize a project like this:
![](https://images.serverlessfans.com/s-tool/zh/s-init-fc.jpg)

## Initialize a Git project

For example, we have a project on Github:

```
https://github.com/anycodes/nodejs10_demo
```

At this point, we can go directly through'

```
s init https://github.com/anycodes/nodejs10_demo
```

Perform initialization, for example:
![](https://images.serverlessfans.com/s-tool/zh/s-init-git.jpg)

In the figure, we can see that we have downloaded the project very easily. You have now initialized a project. If the project does not contain Yaml information to describe resources, the resources cannot be deployed smoothly. `Application Center `before deploying the project, you must make sure that the correct resource description is available.

## Help information

Of course, you can also pass `s init `or `s init -h `bring up help document information:
![](https://images.serverlessfans.com/s-tool/zh/s-init-help.jpg)

