# AccessMiner

This step extracts schema definitions and sample data from Microsoft Access databases and stores a text representation in the text content. It is useful for making access databases discoverable.

* Temporary File Path - A temporary folder that is required for the extraction process.
* Max Column Size - Any column greater than this length will be truncated.
* Number Of Rows To Take - The number of rows to that should be used for a sample.
* Ignore Tables Without Text - If checked tables that contain numerical data alone should be ignored.
* Extract Schema Definition
* Extract Sample Data

<figure><img src="../../../../../../.gitbook/assets/image (457).png" alt="" width="563"><figcaption></figcaption></figure>

### Advanced Options

1. Select Show Advanced Options
2. Define the maximum number of items to process concurrently in Bounded Capacity.
3. Define the maximum number of items that can be queued.&#x20;

{% hint style="info" %}
Limiting either of these will reduce the memory use but increase the time taken.
{% endhint %}
