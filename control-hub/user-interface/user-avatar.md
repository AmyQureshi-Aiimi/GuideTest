# User Avatar

There are many proven benefits to user avatars. They improve communication by associating tasks and comments with recognisable faces. This visual distinction aids in project management and accountability. Additionally, they enhance engagement and can boost team morale.&#x20;

## Enabling Custom Avatars

1. Enable Custom Avatar using the Enable/Disable Custom Avatar toggle.

## Storage Configuration

To allow users to customise their avatars a storage system for these must be configured. This can be Azure, File System or Google storage

1. **Avatar Storage Configuration:** Select the storage type to use from the dropdown.
   * Azure Storage
   * File System Storage
   * Google Storage

### Azure Storage

1. **Endpoint Suffix:** Enter the Endpoint Suffix for the storage account.
2. **Account Name:** Enter the Account Name linked to the storage account.
3. **Access Key Type:** Select the key type from the dropdown, either Account or SAS.
4. **Select Credential:** Choose a credential for this from the dropdown.
5. **Azure Container ID:** Enter the root Azure Container ID for this storage.
6. **Add content-types to blobs:** Check this to show content types when this blob is accessed outside of Workplace AI.

<figure><img src="../../.gitbook/assets/image (839).png" alt="" width="563"><figcaption></figcaption></figure>

### File System Storage

1. **Store Root:** Enter the root folder of this File System Storage.
2. **Reserved Disk Space (Bytes):** Choose the reserved disk space for this storage in bytes.
   * This will reserve space within the storage system for avatar images.
3. **Error on full storage:** Check to get notified if this space becomes full.

<figure><img src="../../.gitbook/assets/image (840).png" alt="" width="563"><figcaption></figcaption></figure>

### Google Storage <a href="#google-storage" id="google-storage"></a>

1. **Project ID:** Enter the Project ID from the Google Cloud Platform.
2. **Bucket Location:** Enter the Bucket Location from the Google Cloud Platform.
3. **Bucket Prefix:** Enter the Bucket Prefix to be added to the beginning of all buckets.
   1. This must start and end with a number or letter and only contain lowercase letters, numbers, -, \_ and .
   2. It cannot start with 'goog' or contain the word 'google' or any other common misspellings of it.

<figure><img src="../../.gitbook/assets/image (842).png" alt="" width="563"><figcaption></figcaption></figure>
