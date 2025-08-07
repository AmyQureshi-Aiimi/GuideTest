# Data Rule Processor

This copies the data properties to entities, metadata and text content. It's helpful when creating unified labels.&#x20;

If you have 2 sources with the same data but the properties are named differently. \
Source A has a property called 'Invoice Number'. Source B has one called 'Invoice No'. Map them both to one entity called 'Invoice Number'.

1. Enter the model ID to read the value from in Data Model ID.
2. Enter the attribute to read the value of in Data Attribute
3. Select an entity from the Entities to Populate dropdown.

<figure><img src="../../../../../../.gitbook/assets/image (393).png" alt="" width="375"><figcaption></figcaption></figure>

### Advanced Options

1. Select Show Advanced Options
2. Define the maximum number of items to process concurrently in Bounded Capacity.
3. Define the maximum number of items that can be queued.&#x20;

{% hint style="info" %}
Limiting either of these will reduce the memory use but increase the time taken.
{% endhint %}
