# Microsoft Teams

Connect your Microsoft Teams source to Aiimi Insight Engine to make the most of your data. Once you have selected a Source System type more detail will expand to customise.

<details>

<summary>Prerequisites</summary>

### Required Permissions

Aiimi Insight Engine requires access to a few applications so the permissions for these need to be granted within Teams. This list may vary if you are crawling only Chats or only Channels.

For support granting permissions [see Microsofts guide for Microsoft Graph Permissions Tab.](https://learn.microsoft.com/en-us/microsoftteams/platform/tabs/how-to/authentication/tab-sso-graph-api?tabs=dotnet)

The API permission type for these must be Application not Delegated.

1. Channel.ReadBasic.All
2. ChannelMember.Read.All
3. ChannelMessage.Read.All
4. Chat.Read.All
5. Files.Read.All
6. Group.Read.All
7. Sites.Read.All
8. Team.ReadBasic.All
9. TeamMember.Read.All
10. TeamSettings.Read.All
11. User.Read.All

### Model Initialisation

You must initialise the model for this source before it is created. If you add the model mapping after the source has been crawled it will need to be reindexed.

You can initialise this model with IndexUtils:

`{AIE_Dir}\utils\InsightMaker.IndexUtilities\InsightMaker.IndexUtilities.exe initialise --teams --publish`

</details>

## General

1. **Mapped Data Models:** You must select the Teams model from the dropdown list.
   * The model must be initialised before the source is created.

***

## Connection

1. **Graph API Endpoint:** Change the Graph API Endpoint if different to the Microsoft default.
2. **Directory (Tenant) ID:** Enter the Directory or Tenant ID from azure.
   * This can be found on the Azure Directory page on the following URL: [https://portal.azure.com/#settings/directory](https://portal.azure.com/#settings/directory)
3. **Authentication Endpoint:** Change your Authentication Endpoint if different to the Microsoft default.
   * This is used to authenticate the requests.
4. **Select Credentials** Choose a credential and secret for Microsoft Teams from the dropdown.&#x20;
   * You can find your credentials in the Azure Enterprise Application configuration pages.
   * _For support setting up credentials use_ [_our guide on managing credentials._](../../../../security/credentials.md)

<figure><img src="../../../../../.gitbook/assets/image (144).png" alt="" width="563"><figcaption></figcaption></figure>

***

## Chats

1. **Crawl Chats:** Check this to ensure chats are crawled.
2. **Excluded Users:** Enter the name or group of any users you want to exclude from crawls.
   * If an excluded user is involved in another chat it will also be excluded.
3. **Excluded Chats:** Enter the Unique ID for the chats you want to exclude.
4. **Chat Filter:** Using an OData filter choose the chats that should be crawled.
   * If this is changed it will be applied to the next new crawl, not any continuations.&#x20;
5. **Chat Message Name Format:** Enter the string for how message names should display on Aiimi Insight Engine.
   * If available the Chat name will be used if not the users present in the chat will.

<figure><img src="../../../../../.gitbook/assets/image (146).png" alt="" width="563"><figcaption></figcaption></figure>

***

## Channels

1. **Crawl Channels:** Check this to ensure Channels are crawled.
2. **Excluded Teams:** Enter the name of any teams you want to exclude from crawls.
3. **Excluded Channels:** Enter the name of any channels that should be excluded.
4. **Channel Filter:** Using an OData filter choose the channels that should be crawled.
   * If this is changed it will be applied to the next new crawl, not any continuations.&#x20;
5. **Channel Post Name Format:** Enter the string for how Channel Posts should display on Aiimi Insight Engine.

<figure><img src="../../../../../.gitbook/assets/image (147).png" alt="" width="563"><figcaption></figcaption></figure>

***

## Messages

1. **Extract Attachments:** If checked attachments will be extracted and stored separately.&#x20;
2. **Excluded Attachments:** As a regular expression enter any attachment names that should be excluded.&#x20;
   * Use a Regular Expression to exclude the subjects.
   * If left blank all attachments will be processed.
3. **Blank Attachment Name:** Enter an attachment name to be used if an attachment has no name.

<figure><img src="../../../../../.gitbook/assets/image (149).png" alt="" width="563"><figcaption></figcaption></figure>

***

## Advanced

### Parallelism

1. **Parallel Chat/Channel Crawling:** Enter the maximum number of chats or channels that can be crawled at once.
2. **Parallel Chat/Channel Deletion:** Enter the maximum number of chats or channels that can be deleted at once.

### Logging

1. **Trace Level:** Select the Trace Level of the connection from the dropdown.
   * None - Do not log graph calls
   * Calls - Log URLs and status codes
   * All - Log URLs, status codes, request forms and JSON responses
2. **Stats Logging Interval (Seconds):** Enter how often anything is logged in seconds.
   * This includes logging the total number of calls, call rates, HTTP errors and 429 errors.
   * You can disable stats logging by setting this to 0.

### Performance

1. **Result Page Size:** Choose the number of results that will be retrieved in a single request.
   * Some endpoints will ignore this and revert to defaults.
   * Search 'odata.maxpagesize' in the Microsoft Graph API documentation.

<figure><img src="../../../../../.gitbook/assets/image (143).png" alt="" width="563"><figcaption></figcaption></figure>

***
