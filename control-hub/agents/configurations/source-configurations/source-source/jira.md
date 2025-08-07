# Jira

Connect a Jira source to Aiimi Insight Engine to make the most of your data. This includes the ability to be able to connect to Jira Service Desk.

1. **Source System:** Select Jira from the dropdown.

## &#x20;Initial Configuration Steps

1. **Select Credential:** Search and select the credential that will be used to connect to Jira from the dropdown.
   * _For support setting up credentials use_ [_our guide on managing credentials._](../../../../security/credentials.md)
2. **jira Security Sync:** Enter the ID of a configured Jira security sync.
   * This sync allows Aiimi Insight Engine to connect user groups from Jira and Aiimi Insight Engine users. This helps ensure the permissions from Jira are upheld.
3. **Worspace ID of the Jira Space:** Enter the base URL of the Jira workspace that should be crawled.
   * Example - https://yourworkspaceid.atlassian.net/
4. **Board Name of the Jira project:** Enter the name of the Jira project board that should be crawled.
5. **Board ID of the Jira project:** Enter the board ID of the board that should be crawled.

<figure><img src="../../../../../.gitbook/assets/image (139).png" alt="" width="563"><figcaption></figcaption></figure>

***

## Completed the Source section&#x20;

1. Once you have completed this section, select Crawl. [Learn how to complete the source Crawl set up.](../source-crawl.md)
