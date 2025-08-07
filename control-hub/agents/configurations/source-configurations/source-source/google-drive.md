# Google Drive

Connect your Google Drive system to Workplace AI to make the most of the data.

{% hint style="info" %}
Public and Private Google Drives must be configured separately.
{% endhint %}

## Prerequisites

Your Google Cloud environment must be configured to allow the connector access to various APIs, services and scopes. Before running the Google Drive Connector these 5 things must be in place.&#x20;

<details>

<summary>Google Cloud Project</summary>

Workplace AI's Google Drive Connector needs a project. A Google Cloud Project is required for Google Cloud Services such as managing APIs and resource permissions.

For information on creating a project [see Google's documentation on creating and managing projects](https://cloud.google.com/resource-manager/docs/creating-managing-projects). ([https://cloud.google.com/resource-manager/docs/creating-managing-projects](https://cloud.google.com/resource-manager/docs/creating-managing-projects))

</details>

<details>

<summary>Required APIs</summary>

Workplace AI's Google Drive Connector requires 3 APIs to be enabled on the relevant project.

1. Activity API
2. Google Drive API
3. Admin SDK API

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

**Further Information**

Any role intended to be Organisation Unit specific can only include the following privileges:

1. Users
2. User Security Management
3. Organizational Units
4. Chrome Management
5. Shared device settings

**Personal Google Drives** - The delegated user will be limited to Personal Google Drives within their Organisational Unit. This ensures only the intended drives are discovered and crawled by Workplace AI.

**Shared/Team Drives** - The delegated user must be a member with at least "Viewer" level access of each drive. This ensures only the intended drives are discovered and crawled by Workplace AI.&#x20;

**For last access dates** -  There are 3 additional settings needed on the service account to track Google Last Access Dates.  The Admin SDK API must be enabled for your Service Account. It must have a new custom role with Admin Console privilege of Reports. It must have read only access to the audits. [https://www.googleapis.com/auth/admin.reports.audit.readonly](https://www.googleapis.com/auth/admin.reports.audit.readonly)

_Please note, these capabilities will be ignored if Calculate Last Accessed Date for Deltas is not enabled._

**For file actions such as Delete** - The delegated user must be a "Manager" of the relevant drive. Only "Managers" are able to delete files from a Shared Google Drive. This ensures that only the Shared Drives connected to Workplace AI can have files deleted.

For more information on service accounts [see Google's documentation on Creating a service account](https://developers.google.com/identity/protocols/oauth2/service-account#creatinganaccount). ([https://developers.google.com/identity/protocols/oauth2/service-account#creatinganaccount](https://developers.google.com/identity/protocols/oauth2/service-account#creatinganaccount))

</details>

<details>

<summary>API Secret Key</summary>

Your service account requires an API secret key for a secure connection. The secret key is used as a secret-only credential in Workplace AI.

* _We recommend you download the key as a JSON file when prompted._

Once generated your private key will be downloaded to your machine. You must store this securely as Google does not store it and you cannot regenerate it.

Once the JSON is downloaded, use its contents to create a secret-only credential in Workplace AI.

_For support setting up a secret-only credential_ [see our guide on creating secret-only credentials.](../../../../security/credentials.md)

_For more information on assigning keys_ [see Google's documentation on Creating a service account](https://developers.google.com/identity/protocols/oauth2/service-account#creatinganaccount). ([https://developers.google.com/identity/protocols/oauth2/service-account#creatinganaccount](https://developers.google.com/identity/protocols/oauth2/service-account#creatinganaccount))

</details>

<details>

<summary>Client Domain-Wide Delegation</summary>

To get the most out of your connection, the service account must have domain-wide delegation and the correct scopes authorised.

A super admin must delegate domain-wide authority ensuring the correct Client ID is used for the service account.

**Required Scopes:**

1. [https://www.googleapis.com/auth/drive](https://www.googleapis.com/auth/drive)
2. [https://www.googleapis.com/auth/drive.readonly](https://www.googleapis.com/auth/drive.readonly)
3. [https://www.googleapis.com/auth/admin.directory.user.readonly](https://www.googleapis.com/auth/admin.directory.user.readonly)
4. [https://www.googleapis.com/auth/admin.directory.group.readonly](https://www.googleapis.com/auth/admin.directory.group.readonly)
5. [https://www.googleapis.com/auth/drive.activity.readonly](https://www.googleapis.com/auth/drive.activity.readonly)

For more information on delegating authority [see Google's documentation on Delegating domain-wide authority](https://developers.google.com/identity/protocols/oauth2/service-account#delegatingauthority) ([https://developers.google.com/identity/protocols/oauth2/service-account#delegatingauthority](https://developers.google.com/identity/protocols/oauth2/service-account#delegatingauthority))

</details>

<details>

<summary>Entity Mapping Prerequisites</summary>

1. The Drive Labels API must be enabled within your Google Cloud Project.
2. Ensure the following scope is added to your API Domain Wide Delegation
   * &#x20;[https://www.googleapis.com/auth/drive.labels.readonly](https://www.googleapis.com/auth/drive.labels.readonly)
3. Check you have the entities you need within Workplace AI and create new ones where needed.&#x20;
   * _For support setting up entities use_ [_our guide on entity creation and management_](../../../../mappings/entities/)_._



</details>

<details>

<summary>Calculate Last Accessed Dates Prerequisites</summary>

**Calculate Last Accessed Date for Deltas:**

There are a couple of additional requirements to calculate the last access date.

1. The Reports API must be enabled on the relevant project.&#x20;
2. The below scope must be added to the Service Account.
   * [https://www.googleapis.com/auth/admin.reports.audit.readonly](https://www.googleapis.com/auth/admin.reports.audit.readonly)

</details>

***

{% hint style="info" %}
The GoogleDirectory security must be configured before. [See our guide on Configuring the Google Directory Security.](../../security-configurations/security-source/google-directory.md)
{% endhint %}

1. **Source System:** Select Google Drive Public or Google Drive Personal from the dropdown.

## Connection

1. **Select Credential:** Select the credential with the service account details for your Google Drive project.&#x20;
2. **Delegated User:** Enter the username of the Service Account user used for domain level operations.

<figure><img src="../../../../../.gitbook/assets/image (773).png" alt=""><figcaption></figcaption></figure>

***

## Security Synchronisation

1. **Security Configuration:** Select the security configuration the crawler will use to synchronise Google Directory and Workplace AI users.
   * [See our guide on Configuring the Google Directory Security.](../../security-configurations/security-source/google-directory.md)

<figure><img src="../../../../../.gitbook/assets/image (776).png" alt="" width="563"><figcaption></figcaption></figure>

***

## Drives

#### Indexing

1. **Use Delta Tokens:** Check this to only crawl files that have changed. If unchecked, the crawl will include all files, this may cause performance issues.
2. **Calculate Last Accessed Date for Deltas:** Check this to update the last known accessed dates during a delta crawl.

{% hint style="info" %}
There are additional service account and API requirements for this. See the service account and entity mapping prerequisites sections above for more details
{% endhint %}

* This date is only kept by Google for 180 days. We revert to the last modified date if this date is empty.
* Enabling this will impact performance.

1. **Crawlable Drives List:** Add all the Google Drives that will be crawled.
   * Add usernames for personal drives. For example user@domain.com.
   * Add the drive IDs for public drives.
2. **Uncrawlable Drives List:** Add the Google Drives that will not be crawled.&#x20;
   * Add usernames for personal drives. For example user@domain.com.
   * Add the drive IDs for public drives.

### Deleting

1. **Remove Data From Missing Drives:** Check this to remove previously crawled Google Drives that are no longer accessible from Workplace AI.
2. **Enable Soft Delete:** Check this to move files with Content Management Delete Actions on them to the Google Drive recycle bin.
   * By default Google Drive recycling bins permanently delete items that have been in them for 30 days.
   * If not checked, files will be permanently deleted.&#x20;

<figure><img src="../../../../../.gitbook/assets/image (895).png" alt="" width="563"><figcaption></figcaption></figure>

### Mappings

When mappings are in place and a crawl is run, files will be indexed with relevant Google Drive Labels mapped as Entities.

1. **Add new item** - Select this to add a new entity mapping between Workplace AI and Google Drive.
2. **Left column** - Enter the Workplace AI entity name. e.g. entities.project.code
   * This is case-sensitive.
3. **Right column** - Enter the Google Drive label and field name. e.g. MyDriveLabel.MyDriveLabelField
   * This is case-sensitive and must match Google Drive exactly.
   * Labels and fields must be unique in their naming convention, with no duplicate names.
4. **Alternative Name For Empty Fields** - Enter the value shown when a file has a label but no related field selected.&#x20;
   * If left blank, the label name will be used.

***

## Advanced

### Parallelism

1. **Parallel Drive Crawling:** Enter the maximum number of drives that should be crawled at once.
2. **Parallel Folder Crawling:** Enter the maximum number of folders, from one drive, that should be crawled at once.
3. **Parallel Folder Query:** Enter the number of Elastic queries, from one drive, that should be crawled at once. This can impact the Elastic performance.
4. **Parallel Drive Deletion:** Enter the number of folders that can be deleted at once. This can impact the Elastic performance.

### Frequency

1. **Results Per Page:** Choose how many files and folders can be retrieved in one call.&#x20;
   * This is defaulted to 100 but must be between 100 and 1000.
   * Increasing this can impact performance. A higher number means fewer calls but requires more memory.

<figure><img src="../../../../../.gitbook/assets/image (829).png" alt="" width="543"><figcaption></figcaption></figure>
