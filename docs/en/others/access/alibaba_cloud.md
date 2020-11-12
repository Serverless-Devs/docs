# Obtain an Alibaba Cloud accesskey

Alibaba Cloud official website: https://www.aliyun.com
AccountId retrieval page: https://account.console.aliyun.com/#/secure
Obtain key information page: https://usercenter.console.aliyun.com/#/manage/ak

- Open [AccountId retrieval page ](https://account.console.aliyun.com/#/secure) get the AccountId:
![AccountId retrieval page](https://images.serverlessfans.com/access/aliyun-accountid.jpg)

- Open [obtain key dialog box ](https://usercenter.console.aliyun.com/#/manage/ak) obtain the key information:
![Obtain key dialog box](https://images.serverlessfans.com/access/aliyun-access.jpg)

> Your Alibaba Cloud account AccessKey is used to access Alibaba Cloud APIs. You must keep your account AccessKey properly! Do not pass any means (e. G. Release the AccessKey to external channels to prevent unauthorized use of the AccessKey. [Security threats ](https://help.aliyun.com/knowledge_detail/54059.html? spm=5176.2020520153.0.0.57f1336a8PQ1KR).
It is strongly recommended that you follow [best security practices of Alibaba Cloud ](https://help.aliyun.com/document_detail/102600.html? spm = 5176.2020520153.0.0.57 f1336a8PQ1KR) using the RAM sub-users AccessKey to make the API call.

----

## Security suggestion

- Create separate RAM users.
You require only one Alibaba Cloud account. You can create separate RAM users for your employees. Then, you can attach different policies to the RAM users. This ensures fine-grained access control. You do not need to use your Alibaba Cloud account for daily permission management.

   For more information, see [create a RAM user ](https://help.aliyun.com/document_detail/93720.html? spm=a2c4g.11186623.2.15.c79a1723Vwyvig#task-187540).

- Separate console users from API users.
We recommend that you do not create a login password for console operations and an AccessKey pair for API operations for a RAM user at the same time.

   To allow an application to access cloud resources by calling API operations, you only need to create an AccessKey pair for the application.
To allow an employee to manage cloud resources by using the console, you only need to set a login password for the employee.
For more information, see [create a RAM user ](https://help.aliyun.com/document_detail/93720.html? spm=a2c4g.11186623.2.16.c79a1723Vwyvig#task-187540).

- Create and group RAM users.
If your Alibaba Cloud account has multiple RAM users, you can group the RAM users based on their responsibilities and grant permissions to the groups.

   For more information, see [create User Group ](https://help.aliyun.com/document_detail/93724.html? spm=a2c4g.11186623.2.17.c79a1723Vwyvig#task-187540).

- Grant the minimum permissions to different RAM user groups.
You can attach system policies to RAM users or RAM user groups. You can also create custom policies and attach them to RAM users or RAM user groups for fine-grained access control. By granting the minimum permissions to different RAM users or RAM user groups, you can better manage access permissions on cloud resources.

   For more information, see [create a custom policy ](https://help.aliyun.com/document_detail/93733.html? spm=a2c4g.11186623.2.18.c79a1723Vwyvig#task-glf-vwf-xdb).

- Configure strong login password policies.
You can configure login password policies that specify the minimum length, mandatory characters, and validation period for RAM users in the RAM console. If you authorize a RAM user to change the login password, the RAM user must create a strong login password and rotate the password or AccessKey pair on a regular basis.

   For more information, see [set RAM user security policies ](https://help.aliyun.com/document_detail/116414.html? spm=a2c4g.11186623.2.19.c79a1723Vwyvig#task-188786).

- Enable an MFA device for your Alibaba Cloud account.
You can enable a multi-factor authentication (MFA) device for your Alibaba Cloud account to enhance the account security. After you enable an MFA device, the following two security factors are required when a RAM user logs on to Alibaba Cloud:

   Username and password
Verification code provided by the MFA device
For more information, see [configure an MFA device for an Alibaba Cloud account ](https://help.aliyun.com/document_detail/28635.html? spm=a2c4g.11186623.2.20.c79a1723Vwyvig#task-u2b-ww2-xdb).

- Enable SSO for RAM users.
After single sign-on (SSO) is enabled, all the internal accounts of your enterprise will be authenticated. Then, RAM users can log on to Alibaba Cloud to access resources only by using an internal account.

   For more information, see [SSO overview ](https://help.aliyun.com/document_detail/93684.html? spm=a2c4g.11186623.2.21.c79a1723Vwyvig#concept-etn-fjc-mfb).

- Do not create an AccessKey pair for your Alibaba Cloud account.
Your Alibaba Cloud account has full permissions on your resources. The AccessKey pair of your Alibaba Cloud account has the same permissions as the login password. The AccessKey pair is used for programmatic access whereas the login password is used to log on to the console. To prevent information leaks due to the disclosure of the AccessKey pair, we recommend that you do not create an AccessKey for your Alibaba Cloud account.

   You can create an AccessKey pair for your RAM users and grant the RAM user the relevant permissions.

   For more information, see [create an accesskey pair for a RAM user ](https://help.aliyun.com/document_detail/116401.html? spm=a2c4g.11186623.2.22.c79a1723Vwyvig#task-188766).

- Specify the condition element in policies to enhance security.
You can specify the condition element in a policy to allow RAM users to use your resources only when the condition is met. For example, you can specify that the RAM user must use a secure channel (for example, SSL), use a specified source IP address, or use your resources within a specified period of time.

   For more information, see [basic elements of a permission policy ](https://help.aliyun.com/document_detail/93738.html? spm=a2c4g.11186623.2.23.c79a1723Vwyvig#concept-xg5-51g-xdb).

- Manage permissions on your cloud resources.
All your resources are in your Alibaba Cloud account. The RAM users of your Alibaba Cloud account can use the resources, but do not own the resources. This allows you to manage instances or other resources created by the RAM users.

   If you no longer require an existing RAM user, you can delete the RAM user to revoke all permissions granted to the RAM user.
If you require a new RAM user, you can create a RAM user, set a login password or AccessKey pair for the RAM user, and then grant the RAM user the relevant permissions.
For more information, see [grant permissions to a RAM user ](https://help.aliyun.com/document_detail/116146.html? spm=a2c4g.11186623.2.24.c79a1723Vwyvig#task-187800).

- Use STS to grant temporary permissions to RAM users.
Security Token Service (STS) is an extended authorization service of RAM. You can use STS tokens to grant temporary permissions to RAM users and specify the permission and automatic expiration time of the tokens.

   For more information, see [what is STS? ](https://help.aliyun.com/document_detail/28756.html? spm=a2c4g.11186623.2.25.c79a1723Vwyvig#concept-ong-5nv-xdb).

