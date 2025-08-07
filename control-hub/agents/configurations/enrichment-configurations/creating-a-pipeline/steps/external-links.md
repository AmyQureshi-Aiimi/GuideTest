# External Links

This extracts links from PPTX, DOCX and XLSX files. It then stores them in the metadata field **externalLinks**.

The metadata field must exist as a **keyword** in the entities section of control hub before this step can be run.

<figure><img src="../../../../../../.gitbook/assets/image (241).png" alt="" width="563"><figcaption></figcaption></figure>

### Advanced Options

1. Select Show Advanced Options
2. Define the maximum number of items to process concurrently in Bounded Capacity.
3. Define the maximum number of items that can be queued.&#x20;

{% hint style="info" %}
Limiting either of these will reduce the memory use but increase the time taken.
{% endhint %}
