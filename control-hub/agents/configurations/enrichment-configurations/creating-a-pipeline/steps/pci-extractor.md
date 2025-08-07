# PCI Extractor

This step extracts payment card information from the content. It is usually used when configuring a compliance solution in Aiimi Insight Engine.

{% hint style="info" %}
You will need to create the PCI entity group in Control Hub to use this step. Please see index utilities and the create and initialise feature for PCI and PII entities.
{% endhint %}

* **Max Entity Values** - Enter the maximum number of values that can be extracted for each entity.&#x20;
  * If more values are found, an exemption will be raised.&#x20;
  * Set the value to 0 to disable the check.
* **Entity Linkage Enabled** - If this is enabled then logic will run to link PCI entities for the purpose of validating that the entities found are indeed PCI.
* **Bi-directional Linkage** - Are linked entities uni-directional or bi-directional.
* **Validate Bank Details** - If enabled modulus validation is attempted on the bank details.
* **Exclude URI** - Whether to include the items URI in the extraction process.
* **Enable Linked Entity Proximity Requirement** - If this is enabled, proximity checking between entities is included (see next parameter).
* **Linked Entity Proximity** - The distance in characters between linked entities.
* **Account Number Entity** - The account number entity (must be in the PCI group).
* **Sort Code Entity** - The sort code entity (must be in the PCI group).
* **Add an Entity** - Any other entities in the PCI group that you want to include.

<figure><img src="../../../../../../.gitbook/assets/image (568).png" alt="" width="563"><figcaption></figcaption></figure>

### Advanced Options

1. Select Show Advanced Options
2. Define the maximum number of items to process concurrently in Bounded Capacity.
3. Define the maximum number of items that can be queued.&#x20;

{% hint style="info" %}
Limiting either of these will reduce the memory use but increase the time taken.
{% endhint %}
