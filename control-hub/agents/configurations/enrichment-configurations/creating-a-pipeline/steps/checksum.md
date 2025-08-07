# Checksum

A checksum is a value that represents the number of bits in a transmission message. It is used to detect high-level errors within data transmissions. Prior to transmission, every piece of data has a checksum value assigned to it before transmission. The Checksum value is sent to the receiving party for the data before it is delivered. This value can then be compared with the data received to check for corruption or tampering.&#x20;

Compute and store the checksum as a metadata field on the item. This is can be used to identify duplicates.&#x20;

* Target - Select the target type, content (binary) or text.
* Algorithm - Currently only supports MD5.

<figure><img src="../../../../../../.gitbook/assets/image (411).png" alt=""><figcaption></figcaption></figure>

### Advanced Options

1. Select Show Advanced Options
2. Define the maximum number of items to process concurrently in Bounded Capacity.
3. Define the maximum number of items that can be queued.&#x20;

{% hint style="info" %}
Limiting either of these will reduce the memory use but increase the time taken.
{% endhint %}
