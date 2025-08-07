# Google Directory

The Google Directory Secondary Security Sync ensures users and groups from Google mean something to Aiimi Insight Engine. Running this sync will give users visibility of the files they have access to in Google Drive.

It takes the user aliases and groups from Google and indexes this in a secondary set of security indices. These indices are used during permission trimming for files, not for authentication.

<details>

<summary>Google Cloud Project</summary>

Aiimi Insight Engine's Google Drive Connector needs a project. A Google Cloud Project is required for Google Cloud Services such as managing APIs and resource permissions.

For information on creating a project [see Google's documentation on creating and managing projects](https://cloud.google.com/resource-manager/docs/creating-managing-projects). ([https://cloud.google.com/resource-manager/docs/creating-managing-projects](https://cloud.google.com/resource-manager/docs/creating-managing-projects))

</details>

<details>

<summary>Required APIs</summary>

Aiimi Insight Engine's Google Drive Security Sync requires 1 API to be enabled on the relevant project.

1. Admin SDK API

For information on enabling APIs [see Google's documentation on enabling an API in your Google Cloud project](https://cloud.google.com/endpoints/docs/openapi/enable-api). ([https://cloud.google.com/endpoints/docs/openapi/enable-api](https://cloud.google.com/endpoints/docs/openapi/enable-api))

</details>

<details>

<summary>Service Account and Delegated User</summary>

A service account associated with the relevant project is needed to perform tasks for the connector. The delegated user used in conjunction with the Service Account Credentials need 2 custom roles. These roles will need relevant Admin privileges granted.

**Custom role examples:**

Google Drive Connector Role\
This can be Organisational Unit specific.\
Admin API Privileges - Users - Read

Google Drive Connector Groups\
This is for all Organisational Units. Groups are domain wide and not limited to a unit.\
Admin API Privileges - Groups - Read

</details>

<details>

<summary>API Secret Key</summary>

Your service account requires an API secret key for a secure connection. The secret key is used as a secret-only credential in Aiimi Insight Engine.

* _We recommend you download the key as a JSON file when prompted._

Once generated your private key will be downloaded to your machine. You must store this securely as Google does not store it and you cannot regenerate it.

Once the JSON is downloaded, use its contents to create a secret-only credential in Aiimi Insight Engine.

_For support setting up a secret-only credential_ [see our guide on creating secret-only credentials.](../../../../security/credentials.md)

_For more information on assigning keys_ [see Google's documentation on Creating a service account](https://developers.google.com/identity/protocols/oauth2/service-account#creatinganaccount). [https://developers.google.com/identity/protocols/oauth2/service-account#creatinganaccount](https://developers.google.com/identity/protocols/oauth2/service-account#creatinganaccount)

</details>

<details>

<summary>Client Domain-Wide Delegation</summary>

To get the most out of your connection, the service account must have domain-wide delegation and the correct scopes authorised.

A super admin must delegate domain-wide authority ensuring the correct Client ID is used for the service account.

**Required Scopes:**

1. [https://www.googleapis.com/auth/admin.directory.user.readonly](https://www.googleapis.com/auth/admin.directory.user.readonly)
2. [https://www.googleapis.com/auth/admin.directory.group.readonly](https://www.googleapis.com/auth/admin.directory.group.readonly)

For more information on delegating authority [see Google's documentation on Delegating domain-wide authority](https://developers.google.com/identity/protocols/oauth2/service-account#delegatingauthority) ([https://developers.google.com/identity/protocols/oauth2/service-account#delegatingauthority](https://developers.google.com/identity/protocols/oauth2/service-account#delegatingauthority))

</details>

## Configure a Google Directory Security Sync

#### **Security**

1. **Security System:** Select GoogleDirectory from the dropdown.
2. **Select Credential:** Select the credential with the service account details for your Google Drive project.&#x20;
3. **Delegated User:** Enter the username of the Service Account user used for domain-level operations.

<figure><img src="../../../../../.gitbook/assets/image (830).png" alt="" width="543"><figcaption></figcaption></figure>

#### **Mappings**

1. **Match Users On:** Choose how Google and Aiimi Insight Engine usernames are linked.&#x20;
   * Exact match - Both usernames match exactly.&#x20;
   * Alternative Domain - The domain in your Google Directory if different to Aiimi Insight Engine.
2. **Alternative Domain:** If you select an alternative domain, enter the domain your Google Directory uses to identify users.
3. **Groups when synchronising users:** Check this to allow group access.
4. Continue to the Sync tab and configure the settings for your security source.
   * [How to complete your security sync.](../security-sync.md)

<figure><img src="../../../../../.gitbook/assets/image (831).png" alt="" width="543"><figcaption></figcaption></figure>

#### Advanced

**Frequency**

1. **Results Per Page:** Choose how many users and groups can be retrieved in one call.&#x20;
   * This is defaulted to 100 but must be between 100 and 500.
   * Increasing this can impact performance. A higher number means fewer calls but requires more memory.

<figure><img src="../../../../../.gitbook/assets/image (832).png" alt="" width="543"><figcaption></figcaption></figure>
