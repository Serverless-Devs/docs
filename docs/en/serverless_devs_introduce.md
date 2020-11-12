# Welcome to Serverless Devs.

<div align=center> <img src="https://images.serverlessfans.com/devs-github/logo.jpg" width="100%"/> </div>

<p align="center">
  <span>Use Serverless like a mobile phone</span>
</p>

- [: thumbsup: Project advantage ](#Project-advantages)
- [: iphone: perform Serverless like a mobile phone ](#Perform-Serverless-like-a-mobile-phone)
- [: house_with_garden: the scenario of Serverless ](#Use-scenarios)
- [: heavy_check_mark: quick-in installation and use ](#Fast-entry-installation-and-use)

Serverless Devs is an open-source and Serverless developer platform, dedicated to providing developers with a powerful tool chain system. Through this platform, developers can experience multi-cloud Serverless products in one click and quickly deploy Serverless projects.

Serverless DevTools include Serverless DevTools and Serverless Devs App Store(Serverless Application Center):

&bull; **Serverless Devs Tool **is a tool that can double the development and O & M efficiency for Serverless developers. By using this tool, developers can perform application creation, project development, testing, release, and deployment tasks in a simpler and faster manner, enabling end-to-end management of projects.

&bull; **Serverless Devs App Store **web + is an application center that integrates online search, one-click deployment, and visual editing of Serverless Applications. The application center contains a large number of production-level project and case templates. You can select from these templates and deploy each project to the specified Apsara stack platform with one click.

## Project advantages

### Supports mainstream Serverless services/frameworks

Serverless Devs is a Serverless developer platform with components and plugins. In this platform, each user can pluggable different Serverless services and frameworks, at the same time, each user can participate in the development of components and plugins. In Serverless Devs, both industrial-grade Serverless services and various open-source Serverless frameworks are well supported. Without the need to study and learn about every Serverless tool on the market, developers can get started with mainstream Serverless services and frameworks simply by using Serverless Devs.

### Visual editing and deployment

Serverless Devs is a complete visual editing and deployment process. In the Serverless Devs App Store, users can quickly search for desired application cases or components using keywords, visually edit the project configuration, and complete project deployment with a mouse click.

For project experience, development, and O & M, under the auspices of the application center and visual editing and deployment, the overall deployment time of the Serverless project is nearly doubled. At the same time, Serverless Devs App Store is an open-source co-construction platform for developers. All users can publish their components and applications in the application center for learning, reference, and use by more people.

| (https://images.serverlessfans.com/devs-github/app-store.jpg) | (https://images.serverlessfans.com/devs-github/app-store-edit.jpg) |
| ------ | ------ |

### Flexible and open use

Unlike most developer tools, Serverless Devs can describe resources such as function compute, API Gateway, and OSS during project description, you can also use plugins and hooks provided by Serverless Devs to Install, Build, and Publish code. In addition, Serverless Devs does not restrict the commands for each component. Instead, developers are encouraged to develop different capabilities for different components to cope with more complex scenarios. For example, Alibaba Cloud function Compute components, in addition to deploying and removing functions, function compute also supports custom features such as log query, metric query, local construction, dependency installation, and debugging.

The flexible and open use of Serverless Devs plays an important role in areas such as automated deployment and O & M, and organically integrates Serverless Devs with the full lifecycle of a project, it improves the development and O & M efficiency of Serverless projects by 90%.

## Perform Serverless like a mobile phone

We can use Serverless Devs in the same way as we would use a mobile phone. When using a mobile phone, we need to search and download various applications in the mobile application market and install them in the mobile phone for use. For the Serverless Devs development platform, we can call up the Serverless Devs App Store via quick gui, search and download the components/plugins to the Serverless Devs Tool to start using Serverless, as shown in the figure:

<div align=center> <img src="https://images.serverlessfans.com/devs-github/cli-app-like-phone-v2.png" width="100%"/> </div>

## Use scenarios

Serverless Devs is a multi-cloud and multi-resource end-to-end/lifecycle management platform. With the joint action of componentization and plugin, the platform can participate in the whole process of project creation, development, debugging, deployment, and maintenance. Taking Alibaba Cloud function compute as an example:

<div align=center> <img src="https://images.serverlessfans.com/devs-github/use.png" width="100%"/> </div>

You can use the command line tool or application center to initially create a project. During project development, you can perform local debugging to verify local development; you can debug projects locally, remotely, and through log querying. When deploying projects, you can install dependencies, the process of project construction and so on to build a complete deployment package, the project is deployed; In the later operation and maintenance mitigation, the project health can be checked through the indicator query, you can locate problems by using methods such as log query, release the versions, aliases, and phased release by using the capabilities such as Project release;

## Fast entry installation and use

npm package-based installation: this installation mode is suitable for Windows, Mac, and Linux platforms that already have npm pre-installed.

Run the following command to install the Serverless Devs Tool on Windows, Mac, or Linux.

```shell script
$ npm install @serverless-devs/s -g
```

> Instructions

- If you run this command on Linux or MacOS with the Error message "Error: eaces: permission denied", run the sudo npm install @ serverless-devs/s -g command.
- If the installation process is slow, run npm -- registry = https://registry.npm.taobao.org install @ serverless-devs-g to install the npm repository on Taobao.

After the installation is complete, you can enter `S `and press enter to see if Serverless is printed:

```
jiangyu@B-165MLVDL-0004 ~ % s

Usage: s [options] [command]

  _________                               .__
 /   _____/ ______________  __ ___________|  |   ____   ______ ______
 \_____  \_/ __ \_  __ \  \/ // __ \_  __ \  | _/ __ \ /  ___//  ___/
 /        \  ___/|  | \/\   /\  ___/|  | \/  |_\  ___/ \___ \ \___ \
/_______  /\___  >__|    \_/  \___  >__|  |____/\___  >____  >____  >
        \/     \/                 \/                \/     \/     \/

Welcome to the Serverless Devs Tool.
You can use the corresponding function through the following instructions.


Options:
  -v, --version   Output the version number
  --skip-extends  Skip the extends section
  -h, --help      Display help for command

Commands:
  config          Configure cloud service account.
  gui             Start GUI service.
  init            Initializing a project.
  search          Search the package.
  platform        Publish a(an) Component/Plugin/Application.
  set             Settings for the tool.
```

## Contact us

<div align=center>

| <div align=center>  <img src="https://images.serverlessfans.com/devs-github/wechat-helper.png" width="200px"/> </div> | <div align=center>  <img src="https://images.serverlessfans.com/devs-github/dingtalk-group.png" width="200px"/> </div> |
| ------ | ------ |
| <p align="center"> <span>WeChat scan code to add a small Assistant into the group</span> </p> | <p align="center"> <span>DingTalk scan the code to enter the discussion and communication group.</span> </p> |

</div>

- Other Contact Information:
   - Website:
      - https://www.serverless.cn
      - https://www.serverless-devs.com
   - Email Address: service@serverlessfans.com

