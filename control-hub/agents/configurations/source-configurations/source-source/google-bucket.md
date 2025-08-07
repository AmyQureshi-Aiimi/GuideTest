# Google Bucket

Connect your Google Bucket source to Workplace AI to make the most of the data on your machines. Once you have selected a Source System type more detail will expand to customise this.\


## Source System Settings

1. **Select Credential** - Select a username from the dropdown. This allows you to connect to the network share.&#x20;
   * If left black the share will not be mounted.
   * _For support setting up credentials use_ [_our guide on managing credentials._](../../../../security/credentials.md)
2. **Bucket** - Enter the bucket to be crawled.
   * If you're unsure of the bucket name you wish to crawl, save the configuration and manually start it. This will fetch a list of accessible Buckets. You can then edit the source and select a bucket from a dropdown.
3. **Root path / Prefix** - Enter the Root path or Prefix of folder you wish to crawl.&#x20;
   * Enter where to start the search from if a delimiter is provided.
   * This will be used as a prefix match if no delimter is entered.&#x20;
   * If left empty the whole bucket will be crawled.
4. **Delimiter** - Enter the delimiter used to seperate folders in the bucket.
5. **Batch Quantity** - Enter how many items can be processed at once.
   * Reduce this number if Elastic is failing to bulk update.

<figure><img src="../../../../../.gitbook/assets/image (260).png" alt="" width="563"><figcaption></figcaption></figure>

***

### Crawling Managed Folders

Managed folders are explicitly created in the Google Buckets. Buckets are natively flat in structure, but specific folders can be created.

1. **Root path / Prefix** - Enter the Root path / Prefix of the managed folder you wish to crawl.&#x20;
   * This can be a prefix, which filters items by what they start with. In this scenario, it is best to set it the managed folder to crawl or leave it empty to find all managed folders.&#x20;
2. **Crawl by managed folders** - Check this to crawl managed folders.

***

### Crawling Psuedo Folders

As Buckets are natively flat in structure, folders do not actually exist. Because of this, delimiters can be set to any character.

1. **Root path / Prefix** - Enter a prefix that will filter items by what they start with.&#x20;
   * As the structure is flat, all files with this prefix will be returned.&#x20;

#### Example:&#x20;

Prefix : “allmy” \
Matches: “allmydocs/me.docx” & “allmydogs.txt”&#x20;

***

### Soft Delete

Soft delete preserves objects and buckets that are deleted or overwritten for a certain period of time.&#x20;

Workplace AI crawls buckets and objects that have been soft deleted so we can remove them from our index. Anything past the soft delete retention period will be permanently deleted by Google and cannot be crawled by Workplace AI.
