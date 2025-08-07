# Microsoft Vision Extractor

This step uses the Microsoft Vision API to extract tags and descriptions from images.

_Before doing this step ensure you have created your entities in Control Hub._

* Endpoint - The endpoint (address) for the API (you can find this in the Azure portal)
* Subscription Key - Your subscription key for this API.
* Max Entities - The maximum number of entities to extract.
* Tags Entity Name - The entity to use for tags (type keyword).
* Description Entity Name - The entity to use for the description (type text).

<figure><img src="../../../../../../.gitbook/assets/image (363).png" alt="" width="563"><figcaption></figcaption></figure>

### Advanced Options

1. Select Show Advanced Options
2. Define the maximum number of items to process concurrently in Bounded Capacity.
3. Define the maximum number of items that can be queued.&#x20;

{% hint style="info" %}
Limiting either of these will reduce the memory use but increase the time taken.
{% endhint %}
