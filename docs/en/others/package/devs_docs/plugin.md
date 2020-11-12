# Plugin Development Guide

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
Type: Plugin
Name: The database Name.
Version: The Version, for example, 0.0.1.
Description: Short Description/Introduction
HomePage: The HomePage of the project.
Tags: # tag details
  -Deploy functions
  -Deploy components
Category: Category# basic cloud services/Web framework/Web application/Artificial intelligence/audio and video processing/graphic processing/monitoring alarm/Big Data/IoT/novice entry/other
```

Valid values of some parameters:

* Type:
```Basic cloud services, Web framework, full-stack applications, artificial intelligence, audio and video processing, graphic processing, monitoring and alarms, big data, IoT, beginner's start, others```

#### readme.md

This file is a brief introduction to the project. You can write a complete description document for your project through this part so that everyone can use your project more simply, it can be used easily and quickly.

## Develop projects

This example is only a development example. It is intended to describe each development detail for you as soon as possible. If you have any questions, please feel free to contact me at any time (Wechat:anycodes_02)

### Create a project

Execute the following statement in the console: `s platform init -t plugin `, to create a Component template:

```
$ s platform init -t plugin

Initializing......
Initialization successfully
$ ls  
src    publish.yaml	    readme.md
```

At this point, we create a directory `src `, and in `src `create a folder `index.js `of course, if the project itself already exists, this step can be skipped::

```
$ mkdir src && cd src && touch index.js
$ ls
index.js
```

> Here is an additional explanation, everyone is publishing their own `plugin `when (I .e. execution `s platform publish `when), the system will pack `SRC `all files in the directory, and upload them to the server. Therefore, do not store sensitive information and data in this directory.
When users use your developed components, they will look `index.js `file, therefore, this file must exist.

### Development components

This component is for testing only. We hope that you can learn something from this component development process.

The first thing to be clear is that our `index.js `basic look:

```javascript
export function plugin(inputs) {
  // Input parameter information
  console.log(JSON.stringify(inputs));
  
  // Return the corresponding results
  // The Returned content here will be used as the input parameter of the component, or the overall return result, so take it seriously
  return inputs;
}
```

When a user uses this plugin, the launcher sends the parameters written by the user to you as inputs. You can simply process the parameters according to your requirements and return them.

Pay additional attention to the parameter format:

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

