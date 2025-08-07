# Slack

Connect Slack to Workplace AI to make the most of the knowledge shared in conversations.

<details>

<summary>Prerequisites</summary>

### Model Initialisation

You must initialise the model for this source before it is created. If you add the model mapping after the source has been crawled it will need to be reindexed.

You can initialise this model with IndexUtils:\
`{AIE_Dir}\utils\InsightMaker.IndexUtilities\InsightMaker.IndexUtilities.exe initialise --slack --publish`

</details>

## General

1. **Source System:** Select Slack from the dropdown.
2. **Mapped Data Model:** Select the Slack model for this source from the dropdown.
   * The model must be initialised before the source is created.

***

## Security Configuration

1. **Select Credential:** Select the secret only credential from the dropdown that matches this key.
   * _For support setting up credentials use_ [_our guide on managing credentials._](../../../../security/credentials.md)
2. **Slack Security Sync:** Select the ID configured for your Slack security sync.
   * The security sync allows Workplace AI to manage user groups from Slack and link them to Workplace AI users. This ensures the user permissions more closely match Slack.

<figure><img src="../../../../../.gitbook/assets/image (802).png" alt="" width="563"><figcaption></figcaption></figure>

***

## What to Crawl

1. **Channels to Include:** Enter the name of any channels to include in the crawl.&#x20;
   1. Leave this blank to crawl all channels the credential has access to.&#x20;
2. **Accepted Message Subtypes: Enter any additional message subtypes to be crawled.**&#x20;
   * Standard user messages are always enabled.&#x20;
   * Refer to Slacks support documentation for more information on subtypes. [https://api.slack.com/events/message#subtypes](https://api.slack.com/events/message#subtypes)
3. **Ignore Bot Messages:** Check this to not index messages from any bots or integrations.
4. **Ignore Slackbot Messages:** Check this to not index messages from the Slackbot user.&#x20;
   * This includes automated messages configured by users.
5. **Include Private:** Check this to index messages from private channels the authenticated user has access to.
   * These messages will only be visible to members of the private channel.
6. **Maximum Messages Per Channel:** Enter the maximum number of messages to index per channel. Messages are indexed from newest to oldest and any messages over the maximum are ignored.&#x20;
   * Set to 0 to index all messages.
7. **Minimum Messages Length:** Enter the minimum number of characters in a message before it is indexed. &#x20;
   * Messages with less characters will not be indexed.
8. **Always Perform Full Crawl:** Check this to always crawl messages from all time.
   * This will increase the length of a crawl but ensure edited messages are updated in Workplace AI.
   * If not checked, the crawl will only check for new messages since the last crawl.

<figure><img src="../../../../../.gitbook/assets/image (807).png" alt="" width="563"><figcaption></figcaption></figure>

***

## Completed the Source section&#x20;

1. Once you have completed this section, select Crawl. This will take you to the Crawl section for this source. [Learn how to complete the source Crawl set up.](../source-crawl.md)
