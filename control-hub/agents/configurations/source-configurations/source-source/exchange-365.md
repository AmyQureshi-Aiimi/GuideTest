# Exchange 365

Connect your Exchange 365 source to Workplace AI to make the most of the data.

## **Initial Configuration Steps**

1. **Graph API Endpoint:** Change the Graph API Endpoint if different to the Microsoft default.
2. **Directory (Tenant) ID:** Enter the Directory or Tenant ID from azure.
   * This can be found on the Azure Enterprise Application configuration pages.
3. **Authentication Endpoint:** Change your Authentication Endpoint if different to the Microsoft default.
4. **Select Credentials** Choose a credential and secret for Exchange 365 from the dropdown.&#x20;
   * You can find your credentials in the Azure Enterprise Application configuration pages.
   * _For support setting up credentials use_ [_our guide on managing credentials._](../../../../security/credentials.md)

<figure><img src="../../../../../.gitbook/assets/Screenshot 2023-03-01 at 11.18.36.png" alt="" width="563"><figcaption></figcaption></figure>

***

## Mailboxes

1. **Priority Mailbox Filters:** Enter an OData filter to pick the mailboxes processed first.&#x20;
   * If left blank no mailboxes will be prioritised.
   * Any changes will only be applied to new crawls.
   * Find OData filters in Microsoft Graph API documentation. [https://learn.microsoft.com/en-us/azure/search/search-query-odata-filter](https://learn.microsoft.com/en-us/azure/search/search-query-odata-filter)
2. **Standard Mailbox Filters:** Enter an OData filter to pick the part of mailbox that is processed.
   * If left blank all mailboxes will be processed.
   * Any changes will only be applied to new crawls.
   * Find OData filters in Microsoft Graph API documentation. [https://learn.microsoft.com/en-us/azure/search/search-query-odata-filter](https://learn.microsoft.com/en-us/azure/search/search-query-odata-filter)

<figure><img src="../../../../../.gitbook/assets/Screenshot 2023-03-01 at 11.19.05.png" alt="" width="563"><figcaption></figcaption></figure>

***

## Messages

1. **Excluded Root Folders:** Enter the folders that should not be processed.
   * Select the Edit (pencil) to edit any items in the list.
   * Select the Delete (trash can) to remove items in the list.
2. **Exclude Message Subjects:** Enter any subjects that mean a message is excluded.
   * Use a Regular Expression to exclude the subjects.
   * If left blank all subjects will be processed.
3. **Excluded Attachment Names:** As a regular expression enter any attachment names that should be excluded.&#x20;
   * Use a Regular Expression to exclude the subjects.
   * If left blank all attachments will be processed.
4. **Blank Subject Default:** Enter a subject to be used in place of any messages with a blank subject.&#x20;
5. **Blank Attachment Name:** Enter an attachment name to be used if an attachment has no name.
6. **Store BCC as Metadata:** Check this to extract and store all BCC addresses. This applies to sent and received emails.
7. **Extract Attachments:** Check this to extract and store all attachments as separate files.

<figure><img src="../../../../../.gitbook/assets/Screenshot 2023-03-01 at 11.19.54.png" alt="" width="563"><figcaption></figcaption></figure>

***

## **Advanced**

### Parallelism

Decide how many different task's are run at once.

**Parallel Mailbox Crawling:** Enter the maximum number of mailboxes that should be crawled at once.

**Parallel Folder Crawling:** Enter the maximum number of folders, from one mailbox, that should be crawled at once.

**Parallel Folder Query:** Enter the number of Elastic queries, from one mailbox, that should be crawled at once. This can impact the Elastic performance.

**Parallel Mailbox Deletion:** Enter the number of folders that can be deleted at once. This can impact the Elastic performance.

### Logging

Select the Trace Level of the connection.

* None - Do not log graph calls
* Calls - Log URLs and status codes
* All - Log URLs, status codes, request forms and JSON responses

Change the Stats Logging Interval (Seconds) to determine how often anything is logged.

* This includes logging the total number of calls, call rates, HTTP errors and 429 errors.
* You can disable stats logging by setting this to 0.

### Performance

When scanning a source you can choose the number of results that will be retrieved in a request. To change the number of results change it on Result Page Size.

 Some endpoints will ignore this and revert to defaults.

 Search 'odata.maxpagesize' in the Microsoft Graph API documentation.

<figure><img src="../../../../../.gitbook/assets/Screenshot 2023-03-01 at 11.20.30.png" alt="" width="563"><figcaption></figcaption></figure>
