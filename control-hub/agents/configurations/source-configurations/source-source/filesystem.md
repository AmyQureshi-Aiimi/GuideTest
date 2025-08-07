# Filesystem

Connect your filesystem source to Aiimi Insight Engine to make the most of the data on your machines. Once you have selected a Source System type more detail will expand to customise this.\
Source System Settings.

<details>

<summary>Preserving Last Accessed Dates</summary>

You can preserve the last accessed date of files to help them identify files that have not been used for a specified period. There are some required permissions that allow Insight Engine to preserve this date attribute. If you don't want Aiimi Insight Engine to preserve the last accessed date the standard read permissions are ok.

### Additional Permissions

On an NTFS filesystem to preserve last accessed dates the following advanced permissions need to be enabled:

* List folder / read data
* Read Attributes
* Read extended attributes
* Write attributes
* Read permissions

![](<../../../../../.gitbook/assets/image (870).png>)

We recommend testing content retrieval on a small sub-set of your documents or a dedicated test area to ensure no errors occur in the Insight Engine Source Agent logs. If the Source Agent is unable to set the last accessed date, then this attribute will be lost for all files crawled and set to the last crawl date.

## Aiimi Insight Engine Configuration

1. Within your Source configuration ensure 'Preserve last access date' is checked.&#x20;
   * This setting is on the Source tab under Retrieval Options.
2. Within your Enrichment content retrieval step config ensure 'Preserve last access date" is checked.&#x20;
   * This setting is on the Steps tab, within a content retrival step.
3. Run your Source Agent and Enrichment pipeline.
   * If the permissions have not been set correctly you will see a warning in the Source Agent log.

</details>

## Source System Details

1. You need to enter a starting point for the crawl within File System Root. This should be a path rooted on locally mounted drive or a UNC path.
2. Discovery and Content agents use an alternative path within Service Root. This allows SAN/NAS/NFS backup partitions to be crawled but still display the address.
3. If left empty the File SystemRoot will be used.
4. Select a username from the Select Credential dropdown. This will allow you to connect to the network share.
   * If left black the share will not be mounted.
   * _For support setting up credentials use_ [_our guide on managing credentials._](../../../../security/credentials.md)
5. A free drive letter will be used to mount the drive if credentials are added.
6. If the network share password changes a system restart is needed on the Network Share system. This ensures all new configurations are persistent.
7. You can choose to crawl specific folders within a filesystems root. Enter any folder names into the Root Folders field.
8. If left blank all folders in the root will be crawled.

<figure><img src="../../../../../.gitbook/assets/Screenshot 2023-02-16 at 15.09.35.png" alt="" width="563"><figcaption></figcaption></figure>

***

## Linux Specific Options

These settings will be used when mounting to a Linux environment and will be ignored for a windows connection.

1. Select the Mount Filesystem Type from the dropdown.
   * At the moment CIFS is the only available option.
2. Enter the Filesystem type version to use when mounting in a Linux environment.
   * If blank, the latest supported version will be used.
   * Format versions 0.0.0 or 0.0.

<figure><img src="../../../../../.gitbook/assets/image (733).png" alt="" width="563"><figcaption></figcaption></figure>

***

## Permissions Lookup

1. If the hosting agent servers are not members of or trusted by the domain uncheck "Use direct domain lookup for security identifiers." For all other servers this should remain checked.
2. You can adjust the number of permission threads that are run along side the indexes. By default we recommend 4.

<figure><img src="../../../../../.gitbook/assets/Screenshot 2023-02-16 at 15.09.54.png" alt="" width="563"><figcaption></figcaption></figure>

***

## Crawl Options

* Is the file system case sensitive - Check this if your filesystem is case sensitive.
* Folder only crawl - Check to only crawl folders within the source.
* Enable FileSystem watcher - Check to enable a smart Crawl. Achieve an optimal crawl time by driving crawls directly from changes to target.
  * This is dependent on your file system, network and if it is supported and enabled.
  * The performance of a large NAS/SAN systems may be impacted if enabled.

<figure><img src="../../../../../.gitbook/assets/image (132).png" alt="" width="563"><figcaption></figcaption></figure>

***

## Retrieval Options

* Preserve last access date - Where possible, the last access date when they are accessed by system functions will be kept. The service account must have sufficient permissions to update file attributes.
  * This may not be possible with all file systems and they may not allow this.
  * You must also set the enable the content retrieval, preserve last access date for this to function.

<figure><img src="../../../../../.gitbook/assets/image (283).png" alt="" width="563"><figcaption></figcaption></figure>

***

## Local Database

1. To enable a local database check used local database.
2. Enter the location within local database location. This location must not be used by another local database.

<figure><img src="../../../../../.gitbook/assets/Screenshot 2023-02-16 at 15.10.54.png" alt="" width="563"><figcaption></figcaption></figure>

***

## Folder Permissions

1. Check Store Folder Permissions to store NTFS ACLs.&#x20;
   * This will store them for each folder in the Elastic index. This is used for ACL monitoring solutions and increases the Elastic document size.

<figure><img src="../../../../../.gitbook/assets/image (743).png" alt="" width="240"><figcaption></figcaption></figure>

***

## Content Management

Allow Aiimi Insight Engine to change a read-only flag on an item before deleting it. The read-only field will be changed as part of a delete action.

If this it not enabled, items flagged as read-only will remain on the course system and will not be deleted. &#x20;

{% hint style="info" %}
The crawlers service account must have permission to change file attributes and delete.
{% endhint %}

1. Check Delete read-only files.
   * The service account must have permission to change file attributes for this to work.

<figure><img src="../../../../../.gitbook/assets/image (745).png" alt=""><figcaption></figcaption></figure>
