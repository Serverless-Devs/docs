# Component Development Guide

## Preface

Thank you for your contribution to the Serverless Devs Tool.

Currently, many people are hyping up Serverless, but Serverless is still a "promising" product. Vendors are highly bound to it and lack appropriate development tools...... Many developers who have access to Serverless are afraid of many problems. To alleviate this awkward situation, the Serverless Devs community is determined to make a community-driven and fully open-source Serverless tool product, we hope that this tool can be used to expand its ecosystem and provide developers with more learning resources, case resources, best practices, and more resources.

To be more open and Serverless, Alibaba Cloud has launched the application center. In this way, you can share your applications, packages, and plugins with users on more platforms, we thank you very much for your contributions to Serverless. Join us in Serverless and make all of us contributors and promoters of Serverless. Serverless will become even more beautiful thanks to your contributions.

## Development specifications

The following development specifications are only beta versions of the specification (however, subsequent specifications will be compatible with this specification), the specification will be continuously improved in the future, I hope you can give us more comments and suggestions.

The project directory must comply with the following format:

```
|- src
| ├── project code   
|- publish.yaml: the project's resource description   
|- readme.md: Project Description
```

#### publish.yaml

This file is the description document of the project. The system will read this document and enter the relevant information when you publish the resources. Please fill in the information carefully.

```yaml
Type: Component
Name: The database Name.
Provider:
  -Cloud vendor name# Alibaba/Baidu/Huawei/AWS/Google Cloud/Azure/Versel/Tencent
Version: The Version, for example, 0.0.1.
Description: Short Description/Introduction
HomePage: The HomePage of the project.
Tags: # tag details
  -Deploy functions
  -Deploy components
Category: Category# basic cloud services/Web framework/Web application/artificial intelligence/audio and video processing/graphic processing/monitoring alarm/big data/IoT/novice entry/other
Service: # The Service that you want to use.
  -Name: service name# function compute, container service, mirroring service, message queue, workflow, CDN, OSS, table store, MNS, log service, API Gateway, database, DNS, and cloud application/Other
    # Runtime: Python 3.6 if the service is a function, you need to add a Runtime
    Authorities: # permission Description
      -Create the required permissions for the function#.
Commands: # command. The format is command: Command description. For example:
  deploy: deploy the function.
  invoke: invokes the function.
Properties:
  Region: #
    Description: parameter Description
    Required: true# the Required parameter. Valid values: true and false.
    Type: # The Type of the request parameter.
      - String
```

Valid values of some parameters:

* Cloud Vendor:
```Alibaba, Baidu, Huawei, Tencent, AWS, Google, Azure, Vercel, Other```

* Type:
```Basic cloud services, Web framework, full-stack applications, artificial intelligence, audio and video processing, graphic processing, monitoring and alarms, big data, IoT, beginner's start, others```

* Cloud Vendor:
```Function compute, container service, image service, message queue, workflow, CDN, object storage service, table store, MNS, log service, API Gateway, database, resolution service, cloud application, other```

* Runtime:
```Node.JS 12, Node.JS 10, Node.JS 8, Node.JS 6, Python3, Python2, PHP7, PHP5, MNS, Java8, Go, Other```

#### readme.md

This file is a brief introduction to the project. You can write a complete description document for your project through this part so that everyone can use your project more simply, it can be used easily and quickly.

## Develop projects

This example is only a development example. It is intended to describe each development detail for you as soon as possible. If you have any questions, please feel free to contact me at any time (Wechat:anycodes_02)

### Create a project

Execute the following statement in the console: `s platform init -t component `, to create a Component template:

```
$ s platform init -t component

Initializing......
Initialization successfully
$ ls  
src    publish.yaml	    readme.md
```

At this point, we create a directory `SRC `, and in `SRC `create a folder `index.js `of course, if the project itself already exists, this step can be skipped:

```
$ mkdir src && cd src && touch index.js
$ ls
index.js
```

> Here is an additional explanation, everyone is publishing their own `component `when (I .e. execution `s platform publish `when), the system will pack `SRC `all files in the directory, and upload them to the server. Therefore, do not store sensitive information and data in this directory.
When users use your developed components, they will look `index.js `file, therefore, this file must exist.

### Development components

This component is for testing only. We hope that you can learn something from this component development process.

The first thing to be clear is that our `index.js `basic look:

```javascript
const { Component } = require('@serverless-devs/s-core')
class MyComponent extends Component {
}
module.exports = MyComponent
```

We need to expose the method directly in `MyComponent `for example, I need to expose a `test `method, that is, the output is Hello World, then:

```javascript
const { Component } = require('@serverless-devs/s-core')
class MyComponent extends Component {
    async test(inputs){
        return "hello world"
    }   
}
module.exports = MyComponent
```

All exposed methods have an input parameter by default. The parameter format is as follows:

```json
{
    "Command": "deploy", // name of the method used by the user
    "Project": {
        "ProjectName": "goproject", // The name of your Yaml project, which is unique in the current Yaml file.
        "Component": "website", // name of the Component you use. It is actually the Component you have developed.
        "Provider": "huaweicloud", // your cloud vendor name
        "AccessAlias": "demo" // the alias of the CMK used by the user.
    },
    "Credentials": current account, // key information
    "Properties": Required parameter, /yaml input
    "Args": "" // argument on the command line
}
```

For example, the Yaml format for a user is:

```yaml
HexoComponent:
  Component: hexo
  Provider: alibaba
  Access: release
  Properties:
    Region: 'cn-hangzhou'
    CodeUri: './src'
```

When the user executes `s deploy mytest -a -b abc `, at this point, your `deploy `method, received `inputs `the parameter is:

```
{
    "Command": 'deploy', 
    "Project": {
        ProjectName: 'HexoComponent', 
        Component: 'hexo',
        Provider: 'alibaba',
        AccessAlias:'release'
    },
    "Credentials": {
        "AccountID": "********",
        "AccessKeyID": "********",
        "AccessKeySecret": "********",
    },
    "Properties": {
        "Region": "cn-hangzhou",
        "CodeUri": "./src"
    },
    "Args": "mytest -a -b abc"
}
```

* For more information about Credentials, different cloud vendors will provide different keys, for example:

```
{
  alibaba: ['AccountID', 'AccessKeyID', 'AccessKeySecret'],
  aws: ['AccessKeyID', 'SecretAccessKey'],
  baidu: ['AccessKeyID', 'SecretAccessKey'],
  huawei: ['AccessKeyID', 'SecretAccessKey'],
  azure: ['KeyVault', 'Secret'],
  tencent: ['AccountID', 'SecretID', 'SecretKey'],
  google: ['AccountID', 'PrivateKeyData']
}
```

   If, at this time, the user is using `access.yml `/`access.yaml `the temporary key in the file, then `Key `is the temporary key. For example, although the user configures `Provider: alibaab `, but he used `access.yaml `:

```
# access.yaml

mytest:
  Key1: Value1
  Key2: Value2
```

   At this point, the user also configures `Access `, and `Access: mytest `, then `Credentials `, then:

```
   "Credentials": {
    "Key1": "Value1",
    "Key2": "Value2"
},
```

* About `Args `in the description of the parameters, you receive a string in this part, but in fact you can directly parse it out through an inherited method, for example:

```
   this.args(inputs.Args)
```

   At this point, I enter in the console:

```
   s deploy c-1 c-2 c-3 -a b --cc d
```

   The result of parsing this part is as follows:

```
   { Commands: [ 'c-1', 'c-2', 'c-3' ], Parameters: { a: 'b', cc: 'd' } }
```

   In fact, the this.args() method has three parameters:
   - argsStr: This part is of the String type and is the parameter
   - boolList: This part is of type Array, which indicates which parameters are of type true/false
   - moreList: This part is of type Array, indicating those parameters with spaces during parsing.

   For example, when my boolList is set `['a', 'B'] `, then when I pass in the data `-a 1 -b 2 -c 3`

   The result parsed by the system for me is:

```
   {
  Commands: [ '1', '2' ],
  Parameters: {
    a: true,
    b: true,
    c: '3'
  }
}
```

   For another example, when our moreList is set `['start-time'] `after that, when I passed in `-a 1 2 3 --start-time 4 5 6`

   The result parsed by the system for me is:

```
   {
  Commands: [ '2', '3' ],
  Parameters: {
    a: '1',
    start-time: '4 5 6'
  }
}
```

In fact, during the execution of the entire component, you can think of it as executing a script.

Where log output can be used `console.log() `, if it is some final results, show to the user, can `return object `.

### What to do next

#### State storage

State storage and reading are actually commonly used in projects. With this function, we can store simple states.

> For example, when you deploy a hexo component but you do not specify a function name, a random function name is generated for the user, we need to detect the details of a function name with the user last time and update it, instead of creating a new operation. In this case, you need to use state storage to store some additional states;
For another example, the serviceId of the unique Key of Tencent Cloud API Gateway, then this Id will only be obtained after we have deployed it, so we have to save this Id after the deployment is complete, specify this Id when redeploying the API rather than creating a new API Gateway service.

Perform partial initialization first:

```
await this.init()
```

Then proceed to read the state and store the state:

Read status:

```
const state = this.state
```

Storage Status:

```
this.state = {}
this.save()
```

#### Load and call components

Dependency between components. For example, you may need to use a certain basic component when using this component. In this case, you can use this component.

For example, when I am doing a Component, I need to import the fc Component, then:

```
const fc = await this.load('fc', 'Component', 'alibaba');
```

The load parameter has the following three parameters:

- componentName: the name of the component.
- componentAlias: alias.
- provider: the provider of the component.

#### Documentation

In some multi-level instructions, help documents may need to be output within the component, so this method can be used.

To add the inputs and help information of the s launcher, perform the following operations:

```
this.help(inputs, {
    "description": "This is the help document",
    "commands": [{
          "name": "Directive 1",
          "desc": "Instruction 1 description",
        },{
          "name": "Directive 2",
          "desc": "instruction 2 description",
        }],
        "args": [{
          "name": "Parameter 1",
          "desc": "parameter 1 description",
        },{
          "name": "Parameter 2",
          "desc": "parameter 2 description",
    }],
})
```

When the user executes `s deploy -h/--help `when:

```
This is the help documentation


  Commands: 
      Instruction 1: Instruction 1 description
      Instruction 2: instruction 2 description

  Args: 
      Parameter 1: parameter 1 description
      Parameter 2: parameter 2 description
```

#### How to test components locally

The method of testing the Component locally is very simple. We only need to write the local path in the Component, that is, through this path, we can find it directly. `index.js `file. Examples:

```
HexoComponent:
  Component: /Users/jiangyu/Desktop/components/fc/src
  Provider: alibaba
  Properties:
    Region: 'cn-hangzhou'
    CodeUri: './src'
```

## Publish a widget

For publishing components, see [Package Development Guide ](../package_dev.md)

## Additional notes

* The package type + package name + cloud vendor + version are unique identifiers of the package, and they must be globally unique;
* If you share a package, it means that you can download and use it by others. If you do not want to be used by others, or the shared package contains sensitive information, please delete the package version, etc. in a timely manner;
* When the package owner is the first package publisher, the package is bound to the developer's account system after the package publisher releases the package. Only the user can delete and upgrade the package, unless the developer deletes all versions of the package;
* The package publisher can only publish each version once. After the package is published, it cannot be modified. If modification is required, upgrade the package version;
* If you fail to publish a package, you can publish the package again without upgrading the version;
* The preceding additional instructions may be revised or corrected during subsequent system upgrades. You can check the Serverless Devs website without notice;

## The contact information of the sub-account user.

Project official website: `serverless.cn `,

Email address: `service@serverlessfans.com`

