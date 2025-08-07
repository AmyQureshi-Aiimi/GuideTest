# Versioned Document Store

Connect your Version Document Store source to Aiimi Insight Engine to make the most of the data. You can set up your Versioned Document Store using the storage plugin like Azure Storage.

1. **Source System:** Select Versioned Document Store from the dropdown.
2. **Choose a Storage Plugin:** Select the Storage Plugin you want to use from the dropdown.
   * Choose between AzureStorage, FileSystemStorage, GoogleStorage.

<figure><img src="../../../../../.gitbook/assets/image (396).png" alt=""><figcaption></figcaption></figure>

### Azure Storage

1. **Endpoint Suffix:** Enter the Endpoint Suffix for the storage account.
2. **Account Name:** Enter the Account Name linked to the storage account.
3. **Access Key Type:** Select the key type from the dropdown, either Account or SAS.
4. **Select Credential:** Choose a credential for this from the dropdown.
   * _For support setting up credentials use_ [_our guide on managing credentials._](../../../../security/credentials.md)
5. **Azure Container ID:** Enter the root Azure Container ID for this storage.&#x20;
6. **Add content-types to blobs:** If checked you will see the content types when accessing the blobs outside of Aiimi Insight Engine.
7. Continue to the Crawl Tab.

<figure><img src="../../../../../.gitbook/assets/image (551).png" alt=""><figcaption></figcaption></figure>

### File System Storage

1. **Store Root:** Enter the root folder of this File System Storage.
2. **Reserved Disk Space (Bytes):** Choose the reserved disk space for this storage in bytes.&#x20;
   * This will reserve space within the storage system for SAR data.
3. **Error on full storage:** Check to get notified if this space becomes full.&#x20;
4. Continue to the Crawl Tab.

<figure><img src="../../../../../.gitbook/assets/image (511).png" alt=""><figcaption></figcaption></figure>

### Google Storage

1. **Project ID:** Enter the Project ID from the Google Cloud Platform.
2. **Bucket Location:** Enter the Bucket Location from the Google Cloud Platform.
3. **Bucket Prefix:** Enter the Bucket Prefix to be added to the beginning of all buckets.
4. Continue to the Crawl Tab.

<figure><img src="../../../../../.gitbook/assets/image (519).png" alt=""><figcaption></figcaption></figure>

