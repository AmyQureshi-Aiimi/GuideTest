# Email Extractor

This step efficiently extracts email addresses from text content.

Select the entity to store internal and external email addresses, and then include any internal email address postfixes.

<figure><img src="../../../../../../.gitbook/assets/image (480).png" alt=""><figcaption></figcaption></figure>

### Advanced Options

1. Select Show Advanced Options
2. Define the maximum number of items to process concurrently in Bounded Capacity.
3. Define the maximum number of items that can be queued.&#x20;

{% hint style="info" %}
Limiting either of these will reduce the memory use but increase the time taken.
{% endhint %}
