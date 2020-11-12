# Yaml configuration

The basic Yaml file configuration format of the Serverless Devs Tool is as follows:

```yaml
ProjectName:
  Component: the Component name.
  Provider: cloud vendor
  Properties: parameters defined by the component
```

In other words, when using the Serverless Devs Tool, you must at least make sure that your data format meets the above requirements. The tool also has many advanced parameters. For example, the complete format is:

```yaml
ProjectName:
  Component: the Component name.
  Provider: cloud vendor
  Access: key name
  Extensions:# plugin information
      deploy: # A method supported by the component, such as the deploy method of the component
        -Plugin: stest_plugin# The executed plugin
          Pre: true# run the command before or after the command is run.
        -Hook: pip install # hook content
          Path: . /# Specify the directory where the Hook is run. Optional.
          Pre: true# run the command before or after the command is run.
  Properties: parameters defined by the component
```

According to a relatively complete example, a Yaml can be written as follows:

```yaml
MyExpress:
  Component: express
  Provider: alibaba
  Access: release
  Extends: 
      deploy: 
        - Plugin: TestPlugin
          Pre: true 
        - Hook: npm install
          Path: ./ 
          Pre: true 
  Properties: 
    Region: cn-hangzhou
    CodeUri: ./
```

This Yaml content means:

1. This project is MyExpress
2. This project uses the express component of alibaba.
3. This project uses alibaba.release's key information
4. For this project, run the following commands respectively before running deploy:
   - TestPlugin
   - In the directory. /. Run the command below `npm install`

Of course, a project can also have multiple paragraphs. For example, if I have a project that includes two parts: the front-end and the back-end, then I can write two projects in a Yaml. `WebBackend `and `WebFronted `:

```yaml
WebBackend:
  Component: express
  Provider: alibaba
  Access: release
  Properties: 
    Region: cn-hangzhou
    CodeUri: ./

WebFronted:
  Component: website
  Provider: alibaba
  Access: release
  Properties: 
    Region: cn-hangzhou
    CodeUri: ./
```

When writing Yaml, we can also write some global variables, global variables can be used `Global `to represent, for example:

```yaml
Global:
    Region: cn-hangzhou

WebBackend:
  Component: express
  Provider: alibaba
  Access: release
  Properties: 
    Region: ${Global.Region}
    CodeUri: ./

WebFronted:
  Component: website
  Provider: alibaba
  Access: release
  Properties: 
    Region: ${Global.Region}
    CodeUri: ./
```

In actual projects, two projects often have interdependencies. For example, you have to complete the deployment of a back-end Project, get the back-end Project address, and put it in the front-end Project before you can build, then, the front-end project can be deployed. Therefore, we often have some dynamic parameters, such:

```yaml
Global:
    Region: cn-hangzhou

WebBackend:
  Component: express
  Provider: alibaba
  Access: release
  Properties: 
    Region: ${Global.Region}
    CodeUri: ./

WebFronted:
  Component: website
  Provider: alibaba
  Access: release
  Properties: 
    Region: ${Global.Region}
    CodeUri: ./
    BackedUrl: ${WebBackend.Output.Url[0].Value}
```

The Serverless Devs Tool analyzes the Yaml content and finds that `WebBackend `after the output results are obtained, the output result is `Url[0].Value `assign to project `WebFronted `of `BackedUrl `property, and then deploy `WebFronted `.

In addition to the formats supported by Yaml, more formats supported by Yaml are as follows:

- Obtain the value of the current environment variable ${Env(env)}, for example, `${Env(SecretId)}`.
- The : `{File(path)}` variable is used to obtain the external document. For example, `${File(./path)}`
- Obtain Global variables: variable `{Global.*}`
- Obtain the variables of other projects: `{ProjectName.Properties.*}`
- Retrieve result variables from other projects in the Yaml format: See {ProjectName.Output. *}

If too many projects are included in a Yaml file, the deployment sequence is also analyzed by default:

1. Analyze project dependencies
2. If you have dependencies, click it to deploy the application in the front-to-back mode. If you have no dependencies, click Yaml to deploy the application in the front-to-back mode.
3. Plugin analysis, deploy from top to bottom according to the configuration (if the value of pre is true, it was previously deployed; If the value of pre is false, it was deployed after the component was deployed)

Examples:

```yaml
Global:
    Region: cn-hangzhou

WebBackend:
  Component: express
  Provider: alibaba
  Access: release

  Properties: 
    Region: ${Global.Region}
    CodeUri: ./

WebFronted:
  Component: website
  Provider: alibaba
  Access: release
  Extends: 
      deploy: 
        - Plugin: TestPlugin
          Pre: true 
        - Plugin: TestPluginEnd
          Pre: false 
        - Hook: npm install
          Path: ./ 
          Pre: true 
  Properties: 
    Region: ${Global.Region}
    CodeUri: ./
    BackedUrl: ${WebBackend.Output.Url[0].Value}
```

The entire deployment process is:

1. Deployment sequence for analysis and deployment: WebBackend->WebFronted
2. Deploy WebBackend-express
3. Get the output result of the WebBackend, and return the result `Url[0].Value `assign to webfrontend `BackedUrl`
4. Deploy webfrontend plugins:
   - Run TestPlugin
   - In `./ `directory, run `npm install`
5. Deploy WebBackend-website
6. Deploy webfrontend plugins:
   - TestPluginEnd

