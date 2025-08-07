# General

There are a number of settings that can be configured on the General page of Global Settings.

## Document Recommendations

Fine tune what items are returned as document recommendations.

* **Max Query Terms** - Enter the maximum number of terms that will be used to find similar results.
  * Increasing this value will give more accurate results but the search will take longer.
* **Minimum Term Frequency** - Enter the minimum number of times a term must appear in a result to be used in further recommendation searches.
* **Minimum Document Frequency** - Enter the minimum number of items a term must appear in to be used in further recommendation searches.
* **Maximum Document Frequency** - Enter a maximum number of items a term can appear in before it is ignored. Eg. 'The', 'And', etc.
* **Score Threshold** - Enter a minimum score items must have to be returned as a recommendation.
  * Items are given a score to indicate how similar they are.

<figure><img src="../../.gitbook/assets/image (878).png" alt="" width="563"><figcaption></figcaption></figure>

***

## Searchable PDF Storage

This must be configured for Searchable PDF's to work. Set up the storage location for searchable PDF files. These are hidden files that are cached for the lifetime of the original file.&#x20;

<figure><img src="../../.gitbook/assets/image (254).png" alt="" width="563"><figcaption></figcaption></figure>

* **Searchable PDF Storage Configuration** - Select the storage type to use from the dropdown.
  * Choose between AzureStorage, FileSystemStorage, GoogleStorage.

<details>

<summary>Azure Storage</summary>

1. **Endpoint Suffix** - Enter the Endpoint Suffix for the storage account.
2. **Account Name** - Enter the name linked to the storage account.
3. **Access Key Type** - Select either Account or SAS from the dropdown.
4. **Credential** - Choose the credential for this storage from the dropdown.
5. **Root Azure Container ID** - Enter the Root Azure Container ID for this storage.&#x20;

</details>

<details>

<summary>File System Storage</summary>

1. **Store Root** - Enter the root folder of this File System Storage.
2. **Reserved Disk Space** - Choose the Reserved Disk Space for this storage in bytes.
3. **Error On Full Storage** - Check this to get notified if this gets full.&#x20;

</details>

<details>

<summary>Google Storage</summary>

1. **Project ID** - Enter the Project ID from the Google Cloud Platform.
2. **Bucket Location** - Enter the Bucket Location from the Google Cloud Platform.
3. **Bucket Prefix** - Enter the prefix that's added to the beginning of all buckets.

</details>

***

## Versioning

Some source types allowing users to search for older versions of data with Versioning. Check Versioning to enable this feature.

{% hint style="info" %}
You need to configure a source to allow versioned documents for this to work. [See our guide for Versioned Document Store to help set up versioning](../agents/configurations/source-configurations/source-source/versioned-document-store.md).
{% endhint %}

<figure><img src="../../.gitbook/assets/image (879).png" alt="" width="563"><figcaption></figcaption></figure>

***

## Results

1. **File Sizes** - Check File Sizes Enabled to show data and document sizes within the results view.
   * For sources with lots of data or web pages this can be irrelevant and use more memory.
2. **Show Result Location** - Check this to show the location of a result under it's file name.
   * Selecting a file location will copy it to the clipboard. Selecting a URL will open the location in a new tab.
3. **Mark as Sensitive** - Check Mark as Sensitive to allow users to mark results and apply a sensitive status.&#x20;
   * Depending on the status of a document they may or may not be visible in future searches.
4. **Missing Information Fields** - Check Show Missing Information Fields to show missing information within a data table.
5. **Result Sources Tab** - Uncheck Result Sources Tab to disable the result sources tab shown within Search.&#x20;
   * By default this feature is on.

***

## Marking Useful Results

This allows users to mark data or documents as useful. This indicates to other users who found what items useful. You can personalise the use case of this feature to fit your business needs.

<figure><img src="../../.gitbook/assets/image (48).png" alt="" width="563"><figcaption></figcaption></figure>

1. **Enabled** - Check this to turn on this feature.
2. **Select Component Icon** - Select the icon you want to signify this action from the dropdown.

***

## Folder Browsing

Folder Browsing allows users to navigate data by browsing subfolders. Users can share information and add items to collections or SARs from here too.

<figure><img src="../../.gitbook/assets/image (886).png" alt="" width="563"><figcaption></figcaption></figure>

* **Enabled** - Check this to enable users to browse hierarchical data and document stores in a Windows Explorer style interface.&#x20;

***

## Cascading Search

This allows users to create custom searches. They can add entities surfaced as part of a search to an existing search query or to a new one. They can build up a search progressively by finding new entities or create a new one based off entities surfaced.

<figure><img src="../../.gitbook/assets/image (887).png" alt="" width="563"><figcaption></figcaption></figure>

* **Enabled** - Check enabled to allow users to create cascading searches.&#x20;

***

## Checksum

Checksums are used to identify duplicate records in your systems. SHA512 is the industry standard way to create these and is used by default in enrichment.&#x20;

MD5 is the old way of creating Checksums and is no longer recommended. We only recommend enabling Legacy MD5 for older systems that have lots of MD5 checksums already.

<figure><img src="../../.gitbook/assets/image (42).png" alt="" width="563"><figcaption></figcaption></figure>

* Legacy MD5 enabled - Check this to use SHA512 and Legacy MD5 for checksums.&#x20;
  * Legacy MD5 should only be enabled for older systems that have lots of MD5 checksums already.

***

## Search Suggestions

Show users suggested searches as they browse. Search suggestions use Elasticsearch to generate suggestions during the indexing process.

<figure><img src="../../.gitbook/assets/image (888).png" alt="" width="563"><figcaption></figcaption></figure>

1. **Enabled** - Check this to enable search suggestions for users.
2. **Number of Shingles** - Choose the number of shingles that are created from a search to create suggestions.&#x20;

***

## Miscellaneous

1. **Maximum Text Content Size** - Enter a Maximum Text Content Size for indexed content in bytes to limit the size of a text based file.&#x20;
2. **Entity Groups Hidden From Document Details** - Add entity groups to hide them from all documents details.
   * By default PCI and PII entity groups are hidden, you can add to or remove these groups.
3. **Enable Permissions for Entities, Metadata and Attributes** - Check this to hide protected attributes from users who don't have access.
4. **Show Matching Contact List** - Check this to show contacts who match a search within the results.
5. **Respect Newline Characters in Data Item Hits** - Check this to respect new lines within hit highlights displayed in an item.

<figure><img src="../../.gitbook/assets/image (889).png" alt="" width="563"><figcaption></figcaption></figure>
