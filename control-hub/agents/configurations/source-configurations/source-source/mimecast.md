# Mimecast

Mimecast is an email security company that protects emails from threats like spam, malware, and phishing. Workplace AI connects to their cloud email archive service.

## Prerequisites

<details>

<summary>Mimecast Service Account</summary>

Workplace AI requires a Mimecast Service Account. For information on creating a Service account [see Mimecast's documentation on creating a service account user.](https://community.mimecast.com/s/article/api-integrations-managing-api-1-0-for-cloud-gateway#Creating-a-service-account-user)

</details>

<details>

<summary>Service Account Roles</summary>

Your service account requires certain roles to allow Workplace AI to crawl Mimecast. For information on service account permissions [see Mimecast's documentation on Granting API Service Account User Permissions.](https://community.mimecast.com/s/article/api-integrations-managing-api-1-0-for-cloud-gateway#Granting-API-Service-Account-User-Permissions)

**We require the following roles to be assigned:**

* Archive Menu - Search - Read & Search Content View
* Directories Menu > Internal > Read

</details>

<details>

<summary>2.0 API Key</summary>

Workplace AI requires the Mimecast 2.0 API.

For information on generating an API key [see Mimecast's video explaining how to generate an API Key.](https://video.mimecast.com/watch/SmxPgxFWfoXPh4Jw2NrNG5?)

**The API requires the following products:**

<mark style="color:red;">If these products are not added you may see a 403 error when using the Util tool.</mark>

* Email Security Cloud Gateway
* Domain Management
* Data Retention
* Connector
* User and Group Management
* Awareness Training
* Threat Management
* Policy Management
* Threats
* Security Events and Data for CG
* Audit Events
* Security Events
* Account Management

</details>

<details>

<summary>Credentials</summary>

The Mimecast connector requires a Client ID and Secret credential. For support setting up a credential [see our guide on creating Client ID and Secret credentials.](../../../../security/credentials.md)

</details>

## Connection

1. **Mimecast API Endpoint:** Enter the Mimecast endpoint to use for API requests.
2. **Authentication Endpoint:** Enter the Mimecast endpoint used to authenticate requests.
3. **Select Credential:** Choose the Mimecast Client ID and Secret from the dropdown.&#x20;
   * For support setting up credentials use [our guide on managing credentials.](../../../../security/credentials.md)
4. Select the Domains tab.

<figure><img src="../../../../../.gitbook/assets/image (156).png" alt="" width="563"><figcaption></figcaption></figure>

***

## Domains

1. **Included Domains:** Choose to crawl specific domains only. Enter the domain names you want to crawl using Regular Expression.&#x20;
   * If blank, all domains will be crawled.
2. **Include local domains:** If checked, local domains will also be processed.
   * This depends on the filtered domains.

<figure><img src="../../../../../.gitbook/assets/image (157).png" alt="" width="563"><figcaption></figcaption></figure>

***

## Mailboxes

1. **Included Mailboxes:** Choose to crawl specific mailboxes only. Enter the email addresses you want to crawl using Regular Expression.&#x20;
   * If blank, all mailboxes will be crawled.
2. **Excluded Mailboxes:** Choose to exclude specific mailboxes only. Enter the email addresses you don't want to crawl using Regular Expression.&#x20;
   * If blank, all included mailboxes will be crawled.

<figure><img src="../../../../../.gitbook/assets/image (158).png" alt="" width="563"><figcaption></figcaption></figure>

***

## Messages

1. **Start Date:** Select the earliest date messages should be retrieved from when crawling a mailbox for the first time.
   * This also applies if Ignore Delta Tokens is checked.
2. **End Date:** Select the date of the latest message to retrieve.&#x20;
   * Leave this empty for ongoing delta crawls.
3. **Ignore delta tokens:** Check this to ignore delta tokens and re-crawl all messages.
   * Use this to find missing messages, if the Start Date is changed, or to process deleted messages.&#x20;
   * This is slower than a standard delta crawl.
4. **Excluded Message Subjects:** Limit the emails processed depending on their subject. Enter the subjects you don't want processed using regular expressions.&#x20;
   * If blank, all messages will be processed.&#x20;
5. **Blank Subject Default:** Enter a default subject for any messages processed without one.

<figure><img src="../../../../../.gitbook/assets/image (159).png" alt="" width="563"><figcaption></figcaption></figure>

***

## Attachments

1. **Extract Attachments:** Check this to extract and store attachments and email separately.&#x20;
2. **Excluded Attachment Names:** Limit the attachments processed. Enter the attachment names you don't want to process using regular expressions.
   * If blank, all attachments will be processed.&#x20;
3. **Blank Attachment Name:** Enter a default name for any attachments processed without one.

<figure><img src="../../../../../.gitbook/assets/image (161).png" alt="" width="563"><figcaption></figcaption></figure>

***

## Advanced

### Parallelism

1. **Parallel Mailbox Crawling:** Enter the maximum number of mailboxes that should be crawled at once.
2. **Parallel Folder Query:** Enter the maximum number of Elastic queries that can be processed at once.
   * This may impact Elastic performance.
3. **Parallel Mailbox Deletion:** Enter the maximum number of mailboxes that can be deleted at once.&#x20;
   * This may impact Elastic performance.

### Logging

1. **Trace Level:** Select the connection trace level from the dropdown.
   * None - Do not log graph calls
   * Calls - Log URLs and status codes
   * All - Log URLs, status codes, request forms and JSON responses
2. **Stats Logging Interval (Seconds):** Choose how often the Graph API call stats are logged in seconds.&#x20;
   * This includes the total number of calls, call rates, HTTP errors and 429 errors.
   * Set this to 0 to disable stats logging.

### Performance

1. **Results Page Size:** Enter the maximum number of results retrieved in a single request.&#x20;
2. **Retry After Multiplier:** Enter a multiplier to pause processing after receiving a 'retry after' message. The multiplier will be multiplied by the 'retry after' value.
   * Retry after values are typically between 1 and 3. A multiplier of 1000 will convert the value to that number of seconds.
3. **Delta Token Offset (Minutes):** Enter the number of minutes to overlap that is applied to a saved delta token.&#x20;
   * This allows time zones to be accounted for.
   * Negative values are subtracted.
4. **Authentication Token Offset (Seconds):** Enter an offset in seconds that is applied to the authentication token expiry.&#x20;
   * Negative values are subtracted.

<figure><img src="../../../../../.gitbook/assets/image (828).png" alt="" width="563"><figcaption></figcaption></figure>

