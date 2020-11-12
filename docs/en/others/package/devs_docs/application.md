# Application Development Guide

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
Type: Application
Name: The database Name.
Provider:
  -Cloud vendor name# Alibaba/Baidu/Huawei/AWS/Google Cloud/Azure/Versel/Tencent
Version: The Version, for example, 0.0.1.
Description: Short Description/Introduction
HomePage: The HomePage of the project.
Tags: # tag details
  -Deploy functions
Category: Category# basic cloud services/Web framework/Web application/Artificial intelligence/audio and video processing/graphic processing/monitoring alarm/Big Data/IoT/novice entry/other
Service: # The Service that you want to use.
  -Name: service name# function compute, container service, mirroring service, message queue, workflow, CDN, OSS, table store, MNS, log service, API Gateway, database, DNS, and cloud application/Other
    # Runtime: Python 3.6 if the service is a function, you need to add a Runtime
    Authorities: # Permissions
      -Create the required permissions for the function#.
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

## Application development

This example is only a development example. It is intended to describe each development detail for you as soon as possible. If you have any questions, please feel free to contact me at any time (Wechat:anycodes_02)

### Create a project

Execute the following statement in the console: `s platform init -t application `, to create an Application template:

### Write a project

In `SRC `directory, compile your application. For example, you can provide an example of audio and video processing or a hello world example.

In fact, the application is more of a well-written project, you can share it with others by packaging code + Yaml, and the sharing method can be implemented through the Serverless Devs App Store.

> Here is an additional explanation, everyone is publishing their own `component `when (I .e. execution `s platform publish `when), the system will pack `src `all files in the directory, and upload them to the server. Therefore, do not store sensitive information and data in this directory.

### Test project

The project test method is very simple, only need `SRC `directory, run `template.yaml `the instruction in. For example, the Alibaba Cloud function compute component used in the sample is run `s deploy `can be normally deployed.

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

