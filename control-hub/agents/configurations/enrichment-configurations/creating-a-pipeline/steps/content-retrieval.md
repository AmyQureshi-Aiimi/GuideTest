# Content Retrieval

Content retrieval gets document content in its native format from sources.

* Retrieve Content - In most cases you will want to just fetch the content if it is missing.
* Process Timeout - How long to wait between retrying for content in seconds.
* Retries - How many times to try retying for content.
* REST Call Timeout - How long to wait for the source to return the content in seconds.
* Skip Thumbnails - Whether to skip generating thumbnails.
* Preserve last access date - Where possible, the last access date of a file being enriched will be kept. This must be enabled per source and some do not support this.
  * You must enable the FileSystem preserve last access date within the source configuration for this to function.

<figure><img src="../../../../../../.gitbook/assets/image (301).png" alt="" width="424"><figcaption></figcaption></figure>

### Advanced Options

1. Select Show Advanced Options
2. Define the maximum number of items to process concurrently in Bounded Capacity.
3. Define the maximum number of items that can be queued.&#x20;

{% hint style="info" %}
Limiting either of these will reduce the memory use but increase the time taken.
{% endhint %}
