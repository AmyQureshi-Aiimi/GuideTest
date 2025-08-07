# Set Document Risk

This step is used to set a documents or data items risk based on the entities present on the item. It can factor in data subject count, PII diversity and visibility.&#x20;

This step is typically used in a compliance scenario and Aiimi will provide guidance with the specific settings for your scenario.

<figure><img src="../../../../../../.gitbook/assets/image (645).png" alt="" width="563"><figcaption></figcaption></figure>

### Advanced Options

1. Select Show Advanced Options
2. Define the maximum number of items to process concurrently in Bounded Capacity.
3. Define the maximum number of items that can be queued.&#x20;

{% hint style="info" %}
Limiting either of these will reduce the memory use but increase the time taken.
{% endhint %}
