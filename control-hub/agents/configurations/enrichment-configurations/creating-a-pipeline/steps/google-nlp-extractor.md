# Google NLP Extractor

This step uses Google natural language processing to extract entities and sentiment from text content.

Note that we also include similar capability based on Huggingface and Spacy as part of the Python REST Service, which ships with the product.

As with the Vision step, provide an endpoint ands then select the entities that you want to store.

_Before using this step ensure you have created your entities in Control Hub. They should all be type keyword for this step._

<figure><img src="../../../../../../.gitbook/assets/image (442).png" alt="" width="563"><figcaption></figcaption></figure>

### Advanced Options

1. Select Show Advanced Options
2. Define the maximum number of items to process concurrently in Bounded Capacity.
3. Define the maximum number of items that can be queued.&#x20;

{% hint style="info" %}
Limiting either of these will reduce the memory use but increase the time taken.
{% endhint %}
