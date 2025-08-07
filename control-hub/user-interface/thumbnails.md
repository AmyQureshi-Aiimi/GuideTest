# Thumbnails

{% hint style="warning" %}
This is required for initial set up.
{% endhint %}

There are a few things that need to be configured for thumbnails within Workplace AI. This includes where they are stored. Thumbnails are shown next to as many files shown in a results list as possible. Some documents can't have a thumbnail created so a default is applied. If a file does not have a thumbnail Workplace AI will create one based of the file and the data within it.&#x20;

Any changes made to the settings regarding thumbnails will not work retroactively. Enrichment will need to be re-run for any updates to existing data.&#x20;

## Size and Quality

1. **Enable Thumbnails** - If checked the thumbnails are enabled.
2. **Thumbnail Size** - Select the size of the thumbnails shown on the screen from the dropdown.&#x20;
   * Choose between Tiny, Small, Medium or Large.
3. **Quality** - Use the Quality slider to determine how clear the thumbnail is.
   * The smaller the size the less someone can see so quality can be sacrificed.
4. **Maximum Modified Age (Months)** - Choose to show no thumbnails for files modified over a certain number of months ago.
   * To show all thumbnails despite modified date leave Maximum Modified Age empty.
   * If you enter 6, files last modified within 6 months will show a thumbnail.
5. **Max Degree of Parallelism** - Set this to determine the number of thumbnailing processes that can run at the same time.
   * This is capped at the maximum number of logical processors available in your content agent.

<figure><img src="../../.gitbook/assets/image (206).png" alt=""><figcaption></figcaption></figure>

***

## Processing Mode

Thumbnails can be processed in the content agent when it runs or as an external process. We recommend and default to the InProcess process mode.

If you see issues like runaway memory usage, consistent high CPU usage but no files processed then you should consider changing your Process mode.

<figure><img src="../../.gitbook/assets/image (205).png" alt=""><figcaption></figcaption></figure>

### Change to an External Process

An External Process is slower as it runs the thumbnail and document conversion processes separately. When using an external process it can be stopped by setting memory and runtime limits.

{% hint style="warning" %}
When changing your JSON file remember to keep any existing settings and make all the necessary changes so that it is still valid.
{% endhint %}

1. Select mode and choose ExternalProcess.
2. Set limits to automatically stop the external process.
   * Change the memory limit in GB to suit your needs. By default this is set to 5GB.
   * Change the RunTime limit in seconds to suit your needs. By default this is set to 60 seconds.
3. Open your appsettings.json
4. &#x20;Update the json to point to the external process.&#x20;
   * Add your external process as a contentUtilitesPath.

#### For example:

{% code overflow="wrap" %}
```
"contentUtilitesPath": "C:\\InsightMaker\\Utils\\InsightMaker.ContentUtilities\\InsightMaker.ContentUtilities.exe"
```
{% endcode %}

***

## Storage

Configuring the storage for the Content Retrieval enrichment step happens here. The input folder is an area that holds documents and data that needs a thumbnail. Then there are ContentAgent resources available the files in that root folder will have thumbnails created and stored in the output folder.&#x20;

1. **Input Storage Configuration** - Select the Storage for the queue of documents that should have thumbnails generated from the dropdown.
   * Choose between File System Storage, Azure Storage or Google Storage.
2. **Output Storage Configuration** - Select the storage for the thumbnails from the dropdown.

* Choose between File System Storage, Azure Storage or Google Storage.

You can have a different storage configuration for the input and output. Depending on your chosen storage you will need to populate different information.

### File System Storage

1. **Store Root** - Enter the root path of the folder.&#x20;
2. Reserved Disk Space - Choose the amount of Reserved Disk Space for the folder.&#x20;
   * Enter the reserve amount in bytes.
   * You may want to reserve disk space for the input and output folders. Input only holds temporary data and is removed once the thumbnail is made.
3. **Error On Full Storage** - Check this to get notified if this gets full.&#x20;

<figure><img src="../../.gitbook/assets/image (378).png" alt="" width="563"><figcaption></figcaption></figure>

### Azure Storage

1. **Endpoint Suffix** - Enter the Endpoint Suffix for the storage account.
2. **Account Name** - Enter the name linked to the storage account.
3. **Account Key Type** - Select either Account or SAS from the dropdown.
4. **Credential** - Choose the credential for this storage from the dropdown.
5. **Root Azure Container ID** - Enter the Root Azure Container ID for this storage.&#x20;

<figure><img src="../../.gitbook/assets/image (661).png" alt="" width="563"><figcaption></figcaption></figure>

### Google Storage

1. **Project ID** - Enter the Project ID from the Google Cloud Platform.
2. **Bucket Location** - Enter the Bucket Location from the Google Cloud Platform.
3. **Bucket Prefix** - Enter the prefix that's added to the beginning of all buckets.

<figure><img src="../../.gitbook/assets/image (605).png" alt="" width="563"><figcaption></figcaption></figure>

