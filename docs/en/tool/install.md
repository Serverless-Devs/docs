# Installation instructions

This topic describes how to install the Serverless Devs Tool.

- [Mac/Linux Quick installation ](#Quick-installation)
- [Npm based installation ](#Npm-based-installation)

## Quick installation

Only for Mac/Linux

```bash
curl -o- -L http://cli.so/install.sh | bash
```

## Npm based installation

For Mac/Linux/Windows

npm package-based installation: this installation mode is suitable for Windows, Mac, and Linux platforms that already have npm pre-installed.

Run the following command to install the Serverless Devs Tool on Windows, Mac, or Linux.

```
$ npm install @serverless-devs/s -g
```

> Instructions

- If you run this command on Linux or MacOS with the Error message "Error: EACCES: permission denied", run the sudo npm install @ serverless-devs/s -g command.
- If the installation process is slow, run npm -- registry = https://registry.npm.taobao.org install @ serverless-devs-g to install the npm repository on Taobao.

After the installation is completed, run the s command in the control terminal to view version information.

```
s -v
```

