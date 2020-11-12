# Google Cloud key acquisition

Google Cloud website: https://cloud.google.com

- Open [Google Cloud website ](https://cloud.google.com) to sign in, select the project, go to the project:
![Obtain key dialog box](https://images.serverlessfans.com/access/google-console.jpg)
- In the left-side navigation pane, click service accounts]:
[](https://images.serverlessfans.com/access/google-service.jpg)
- Click create service account]:
[](https://images.serverlessfans.com/access/google-add.jpg)
- The corresponding file is downloaded after the file is created]]:
[](https://images.serverlessfans.com/access/google-access.jpg)
- Store the file locally and configure the stored absolute path `S `tools required `PrivateKeyData `medium

> When you use API keys in your app, make sure they are secure during storage and transfer. Public disclosure of credentials may cause your account to be stolen, which may incur unexpected charges to your account. To help secure your API keys, follow these best practices:

- Do not embed the API key directly in your code. API keys embedded in code may be accidentally disclosed to the public. For example, you may forget to remove the key from the shared code. Instead of embedding the API key in your app, you can store the API key in an environment variable or in a file outside your app's source tree.
- Do not store API keys in files within your app's source tree. If you store the API key in a file, keep the file outside your app's source tree, which helps ensure that the key does not end up in the source control system. This is especially important if you use a public source control system such as GitHub.
- Set up applications and [API key restriction ](https://cloud.google.com/docs/authentication/api-keys#api_key_restrictions). By adding restrictions, you can reduce the impact of API key theft.
- Remove unwanted API keys to minimize the risk of attack.
- The API key is periodically regenerated. You can [credentials page ](https://console.cloud.google.com/apis/credentials? _ga = 2.119850376.1642904664.1603769673-1032325965.1594091682), click regenerate key for each key to regenerate the API key. Then update your app to use the newly generated key. After generating the replacement key, the old key will expire after 24 hours.
- Before you publish your code, make sure your code does not contain an API key or any other private information, and then publish it.

