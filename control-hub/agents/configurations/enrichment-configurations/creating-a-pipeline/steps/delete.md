# Delete

This step deletes items from their source. This step is used in conjunction with SAR or migration configuration.

This step has no configuration and relies on upstream configuration to operate.

* The source needs to be configured with credentials that allow deletion.
* You need to enable deletion on the source in Aiimi Insight Engine. This is disabled by default.
* Configure an appropriate 'File Action' on the pipeline, such as 'delete'. The pipeline will only run on things that are marked for 'delete'.

<figure><img src="../../../../../../.gitbook/assets/image (242).png" alt="" width="563"><figcaption></figcaption></figure>

### Advanced Options

1. Select Show Advanced Options
2. Define the maximum number of items to process concurrently in Bounded Capacity.
3. Define the maximum number of items that can be queued.&#x20;

{% hint style="info" %}
Limiting either of these will reduce the memory use but increase the time taken.
{% endhint %}
