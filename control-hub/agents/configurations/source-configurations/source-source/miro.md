# Miro

Connect Miro to Workplace AI to make the most of your data.

## Initial Configuration Steps

1. **Select Credential:** Select the secret-only credential with a valid OAuth token from the dropdown.&#x20;
   * This token must be valid for an enterprise team.&#x20;
   * We recommend ContentAdminPermissions are enabled so all boards can be crawled.
   * _For support setting up credentials use_ [_our guide on managing credentials._](../../../../security/credentials.md)
2. **Miro Security Sync:** Select the ID of a configured Miro Security sync.
   * This allows Workplace AI to manage and match Miro user groups to its users after crawling.
3. **Text of Unusual Size:** Enter the smallest font size that should be considered a header.
4. **Minimum Tag Frequency:** Set the minimum number of times a word must be used on a board to become a tag.
   1. Common words like A, The, And, etc. are ignored.
5. **Maximum Board Items to Retrieve:** Enter The maximum number of items that can be returned per board element.
   * Setting this to -1 (no limit) will return all items.&#x20;
   * Limiting this can improve crawl times for larger boards, but might mean truncating text content.&#x20;

<figure><img src="../../../../../.gitbook/assets/image (9).png" alt="" width="563"><figcaption></figcaption></figure>

***

## Completed the Source section&#x20;

1. Once you have completed this section, select Crawl. [Learn how to complete the source Crawl set up.](../source-crawl.md)
