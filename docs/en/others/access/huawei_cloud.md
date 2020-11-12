# Obtain the Huawei cloud key

Huawei Cloud official website: https://www.huaweicloud.com/

- Open [huawei Cloud website ](https://www.huaweicloud.com/) to log on to the console. Click my credentials in the upper-right corner and then click access keys in the left-side navigation pane]:
![Obtain key dialog box](https://images.serverlessfans.com/access/huawei-page.jpg)
- Click Add access key. A dialog box appears, verifying the security of the access key. The dialog box appears:
![](https://images.serverlessfans.com/access/huawei-download.jpg)
- You can see your key information after downloading:
![](https://images.serverlessfans.com/access/huawei-access.jpg)

> To ensure account security, we recommend that you change your accesskey on a regular basis and store it properly.

------

## Security suggestion

- Do not create accesskey for Huawei cloud account
You can use a Huawei cloud account to owned Alibaba cloud resources and were charged for resource usage. This account has full access permissions to its resources and cloud services. A password and an accesskey pair (AK or accesskey) are credentials of an account. Accounts are equally authentic. A password is a required credential for you to log on to the console, the accesskey is used for programming calls using development tools. It is the second identity credential. It is optional and auxiliary. To improve account security, we recommend that you only log on to the console with a password and do not create a second identity credential (accesskey) for the account. This avoids information security risks caused by the leakage of accesskey.

- Do not embed access keys in code
When you use development tools such as API, CLI, and SDK to access cloud services, do not embed the accesskey pair in the code to reduce the risk of data leakage.

- Create a separate IAM user
If anyone needs to access the resources in your Huawei cloud account, please do not share the password of the account with them, instead, create a separate IAM user in your account and assign them corresponding permissions. At the same time, as the principal of Huawei cloud account, it is recommended that you not use the account to access Huawei cloud, instead, you can create an IAM user for yourself, and grant management permissions to this user. With management permissions, you can use this IAM user for management tasks and ensure account security.

- Grant minimal permission
The principle of least privilege is standard security advice. You can use the system permissions provided by IAM or create your own custom policies to grant only the permissions that are just needed to complete your work to the users in the account, the principle of least privilege can help you securely control user access to Huawei cloud resources.

   In addition, we recommend that you grant custom policies to the IAM user who accesses cloud services by using development tools such as APIs, CLI, and SDKs. Through fine-grained permission control, reduce the impact of accesskey pair leakage on your account.

- Enable virtual MFA
Multi-Factor Authentication (MFA) is a simple security practice. We recommend that you enable MFA for your Huawei cloud account or for users with higher permissions, it adds an additional layer of protection to the username and password. After MFA is enabled, when the user logs in to the console, the system will ask the user to enter the user name and password (first security factor) and the verification code from their MFA device (second security factor). The multi-factor authentication provides greater security for your account and resources.

   The MFA device can be based on hardware or software. Currently, the system only supports software-based virtual MFA. Virtual MFA is an application that can generate a 6-digit digital authentication code, such applications can run on mobile hardware devices (including smart phones), which is very convenient.

- Set a strong password policy
In the IAM console, set strong password policies. For example, set the minimum password length and the maximum number of consecutive occurrences of a character in a password, and set the password and the previous password at all times.

- Set sensitive operations
After you enable sensitive operations, you or your Alibaba cloud accounts require the password and verification code to verify that they perform sensitive operations, such as deleting resources and generating accesskey pairs, avoid risks and losses caused by misoperations.

- Periodically modify identity credentials
If you do not know that your password or accesskey pair has been disclosed, you can make periodic changes to minimize the risk of accidental disclosure.

   You can set a password validity policy to rotate your password periodically. You and all users under your account must change your password at the specified time. Otherwise, your password will be invalid, IAM will start prompting users to change their passwords 15 days before they expire.
You can rotate access keys by creating two access keys as one master key and one slave key. Then, you can use the primary access key and the secondary access key for a while, then, in the console, delete CMK 1, generate a new one, and rotate it in your application regularly.

- Remove unwanted identity credentials
For IAM users who only need to sign in to the console, do not use access keys, do not create or delete access keys for them in a timely manner. You can also use the last login time of the IAM user to check whether the credentials are no longer needed. For an IAM user that has not logged on for a long period of time, please modify their identity credentials in a timely manner, including changing passwords and deleting access keys. You can also set up an "account deactivation policy" to control the automatic expiration of unused accounts.

