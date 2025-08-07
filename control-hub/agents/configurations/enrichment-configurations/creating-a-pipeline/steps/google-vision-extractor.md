# Google Vision Extractor

This step integrates with the Google Vision cloud service to add labels to image content, therefore making it easy to search and discover image content.

_Before using this step ensure you have created your entities in Control Hub._

* Endpoint - This is the GCP endpoint including your API key. You will need to create a GCP account and configure the endpoint and billing. Please see GCP documentation.
* Max Entities - The maximum  number of entities to extract.
* Label Annotation Entity Name - The entity to store descriptive labels in (type keyword).
* Web Entities Entity Name - The entity to store [web entities](https://cloud.google.com/vision/docs/detecting-web) in (type keyword).
* Text Detection Entity Name - The entity to store text that is detected in (type text).
* Document Text Detection - Check this to enable document text detection (i.e. for OCR).
* Append Entities to Text Content - Check this to append the entities found to the text content in the Aiimi Insight Engine index.
* Language Hints - You can provide language hints in the form of language codes.

<figure><img src="../../../../../../.gitbook/assets/image (687).png" alt="" width="563"><figcaption></figcaption></figure>

### Advanced Options

1. Select Show Advanced Options
2. Define the maximum number of items to process concurrently in Bounded Capacity.
3. Define the maximum number of items that can be queued.&#x20;

{% hint style="info" %}
Limiting either of these will reduce the memory use but increase the time taken.
{% endhint %}
