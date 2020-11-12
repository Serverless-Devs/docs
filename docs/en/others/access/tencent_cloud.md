# Retrieve Tencent Cloud key

Tencent Cloud official website: https://cloud.tencent.com/
Obtain key information page: https://console.cloud.tencent.com/cam/capi

- Open [obtain key dialog box ](https://console.cloud.tencent.com/cam/capi) obtain the key:
![Obtain key dialog box](https://images.serverlessfans.com/access/tencent-access.jpg)

> Your Alibaba Cloud Account Key provides unrestricted access to your Tencent cloud resources. The disclosure of your Alibaba Cloud account key may cause losses to your cloud assets! We strongly recommend that you reference [best practices ](https://cloud.tencent.com/document/product/598/10592) stop using your Alibaba Cloud account to log on to the console or use your Alibaba Cloud account secret to access cloud APIs. Use your Alibaba Cloud account as a Ram user to perform operations on resources. [Create a Ram user ](https://cloud.tencent.com/document/product/598/13674)

------

## Security suggestion

- Enable MFA protection
To enhance account security, we recommend that you bind an MFA device to all accounts and enable the login protection and sensitive operation protection for both the primary account and its sub-accounts. We strongly recommend that you perform secondary MFA verification for accounts that support email login and WeChat login. After MFA is enabled, Account login and sensitive operations require secondary verification. For related settings, see: [set up security for collaborators ](https://cloud.tencent.com/document/product/598/36626), [set up security protection for a Ram user ](https://cloud.tencent.com/document/product/598/36383).

- Access Tencent cloud using a Ram user
If possible, do not use the identity credentials of the Alibaba Cloud account to access Tencent Cloud or share the identity credentials with other users. Generally, you must create a Ram user for all Tencent Cloud users and grant the Ram user administrative permissions. For related settings, see: [user type ](https://cloud.tencent.com/document/product/598/13665).

- Use groups to assign permissions to sub-accounts
Define groups based on job responsibilities and grant administrative permissions to the groups. Assign the user to a group. In this way, when you modify the permissions of the group, the permissions of the relevant users in the group are changed immediately. In addition, when the organizational structure changes, it only needs to update the relationship between users and groups. For related settings, see: [user Group ](https://cloud.tencent.com/document/product/598/14985).

- Minimum permission principle
The principle of least privilege is a standard security principle. That is, only the minimum permissions required to execute the task are granted. Do not grant more irrelevant permissions. For example, if a user is only a user of the CDN service, you do not need to grant resource access permissions (such as COS read and write permissions) for other services to this user.

- Manage users, permissions, and resources through child accounts
We recommend that you use different Ram users to manage users, permissions, and resources. You should allow sub-accounts to manage users and sub-accounts to manage other cloud resources.

- Rotate identity credentials regularly
It is recommended that you or CAM users regularly rotate their login passwords or cloud API keys. This limits the time for the leakage of identity credentials.
For more information about how to set a primary account password, see: [account password ](https://cloud.tencent.com/document/product/378/14623).
For subaccount password settings, see: [reset password ](https://cloud.tencent.com/document/product/598/36260).

- Remove unwanted certificates and permissions
Delete certificates and permissions that the user no longer needs. Minimize security risks caused by leakage of access credentials.

- Enhance Security with policy conditions
Define more detailed conditions for the policy as much as possible, restrict the scenario where the policy takes effect, and enhance the security. For example, users must perform certain operations at a specified time or on a specified server.
For related settings, see: [element reference condition ](https://cloud.tencent.com/document/product/598/10603#6. -.E7.94.9F.E6.95.88.E6.9D.A1.E4.BB.B6.EF.BC.88condition.EF.BC.89).

