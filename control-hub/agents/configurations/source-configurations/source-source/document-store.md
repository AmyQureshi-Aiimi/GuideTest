# Document Store

Connect your DocumentStore source to Aiimi Insight Engine to make the most of the data. You can either set up your DocumentStore using the storage root folder location or a storage plugin like Azure Storage.

1. **Source System:** Select Document Store from the dropdown.

## Storage Root Folder

1. **Use Storage Plugin:** This should not be checked to use a root folder.&#x20;
2. **Document Store Root:** Enter folder location where documents managed by this will be stored.
3. Continue to the Crawl Tab.

<figure><img src="../../../../../.gitbook/assets/image (8).png" alt="" width="563"><figcaption></figcaption></figure>

***

## Use a Storage Plugin

1. **User Storage Plugin:** This should be checked to use a storage plugin.&#x20;
2. **Choose a Storage Plugin:** Select the Storage Plugin you want to use from the dropdown.
   * Choose between AzureStorage, FileSystemStorage, GoogleStorage.

### Azure Storage

1. **Endpoint Suffix:** Enter the Endpoint Suffix for the storage account.
2. **Account Name:** Enter the Account Name linked to the storage account.
3. **Access Key Type:** Select the key type from the dropdown, either Account or SAS.
4. **Select Credential:** Choose a credential for this from the dropdown.
   * _For support setting up credentials use_ [_our guide on managing credentials._](../../../../security/credentials.md)
5. **Azure Container ID:** Enter the root Azure Container ID for this storage.&#x20;
6. **Add content-types to blobs:** If checked you will see the content types when accessing the blobs outside of Aiimi Insight Engine.
7. **Enable for Configurable Collection:** Check this to show this source in the configurable collections wizard.
   * If this source if selected in the configurable collection wizard imported documents will be stored here.
8. Continue to the Crawl Tab.

<figure><img src="../../../../../.gitbook/assets/image (7).png" alt="" width="563"><figcaption></figcaption></figure>

### File System Storage

1. **Store Root:** Enter the root folder of this File System Storage.
2. **Reserved Disk Space (Bytes):** Choose the reserved disk space for this storage in bytes.&#x20;
   * This will reserve space within the storage system for SAR data.
3. **Error on full storage:** Check to get notified if this space becomes full.&#x20;
4. Continue to the Crawl Tab.

<figure><img src="../../../../../.gitbook/assets/image (6).png" alt="" width="563"><figcaption></figcaption></figure>

### Google Storage

1. **Project ID:** Enter the Project ID from the Google Cloud Platform.
2. **Bucket Location:** Enter the Bucket Location from the Google Cloud Platform.
3. **Bucket Prefix:** Enter the Bucket Prefix to be added to the beginning of all buckets.
4. Continue to the Crawl Tab.

<figure><img src="../../../../../.gitbook/assets/image (5).png" alt="" width="563"><figcaption></figcaption></figure>

***

## Configuring Storage for Imported Items

To allow users to import items to a collection the storage for these must be configured first. This can only be done via a Document Store Source.

1. **Enable for Configurable Collection:** Check this to allow imported items to be stored in this source.&#x20;
   * This can be found in Google, Azure and File System storage plugins.
   * This source will appear as an available source within the configurable collections wizard. If it is selected in the collection config this source will be used to store imported items.
2. Within the Advanced Tab the Allow Add, Delete and Update action checkboxes must be checked.

<figure><img src="../../../../../.gitbook/assets/image (169).png" alt="" width="563"><figcaption></figcaption></figure>
