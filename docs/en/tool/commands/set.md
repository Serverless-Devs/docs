# Set instructions help document

By `s set `instruction to configure Serverless Devs Tool features. This includes but is not limited:

- [Set language ](#Set-language)
- [Set output color ](#Set-output-color)
- [Configure Data Reporting ](#Configure-Data-Reporting)
- [Help information ](#Help-information)

## Set language

### Set language usage

You can use `s set language `to set the default language for the command line tool. Currently, the system supports two languages:

|  | Directive |
| ---- | ---- |
| Chinese | zh |
| Name | en |

For example, if you want to set this tool as the default Chinese output, you can use:

```
s set language zh
```

Similarly, if you want to set the English output as follows:

```
s set language en
```

### Query help information about Serverless Workflow

You can run commands `s set language -h `obtain help information:
![](https://images.serverlessfans.com/s-tool/zh/s-set-language-help.jpg)

## Set output color

### Set output color usage

Currently, the output of the command line tool is colored by default. Different colors indicate different information. For example, blue/purple indicates output information, and white indicates log information, the yellow or orange part indicates a warning message, the red part indicates an error message, and the green part indicates a successful message.

However, many command line tools are not friendly to color output, and some users will add background color to the command line themselves. At this time, adding color output will cause additional confusion, therefore, no color output and color output modes are provided.

If you want to set no color output, you can:

```
s set output-color disable
```

If you want to set color output, you can:

```
s set output-color enable
```

### Query help information about Serverless Workflow

You can run commands `s set output-color -h `obtain help information:
![](https://images.serverlessfans.com/s-tool/zh/s-set-output-color-help.jpg)

## Configure Data Reporting

### Method for setting data reporting

To better understand the usage habits of each user, we have conducted some tracking in the tool to count the usage habits of users, so that we can better improve the product.

The usage habits here absolutely do not include the personal sensitive data used, for example, the key information is definitely not included!

These habits usually include the total number of times users use commands, the configured cloud vendor name, and the number of times commands are used.

Of course, we also consider that some users do not want us to collect some of their behavioral data, we provide this data reporting setup solution.

If you do not want us to collect and report your behavior data, run the following command:

```
s set analysis disable
```

If you are willing to help us improve our product, you can turn on the report function so that we can better improve the tool:

```
s set analysis enable
```

### Query help information about Serverless Workflow

You can run commands `s set analysis -h `obtain help information:
![](https://images.serverlessfans.com/s-tool/zh/s-set-analysis-help.jpg)

## Help information

Of course, you can also pass `s set `or `s set -h `bring up help document information:
![](https://images.serverlessfans.com/s-tool/zh/s-set-help.jpg)

