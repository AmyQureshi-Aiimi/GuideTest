# AI Classification

This step allows items to be classified based on the classification configuration. Each classification needs its own enrichment step to be run.

Classifications must be created before creating this enrichment step. For help classification [visit our guide on AI Settings.](../../../../../ai-settings/)

1. **Name:** Enter a name for this enrichment step.&#x20;
   * If there are multiple steps in this enrichment it must be unique.&#x20;
2. **Classifications to apply:** Select a classification from the dropdown to run as part of this enrichment.
3. **Error on model failure:** Check this to receive an error if the AI classification service errors.&#x20;
   * If this is not checked, documents will not be classified and no error will be received.

<figure><img src="../../../../../../.gitbook/assets/image (843).png" alt="" width="413"><figcaption></figcaption></figure>

### Advanced Options

1. Select Show Advanced Options
2. Define the maximum number of items to process concurrently in Bounded Capacity.
3. Define the maximum number of items that can be queued.&#x20;

{% hint style="info" %}
Limiting either of these will reduce the memory use but increase the time taken.
{% endhint %}
