# OcrRest

The OcrRest step communicates with your OCR Agent to perform OCR tasks. To use this you will need to have configured an OCR Agent engine.

* OCR Engine ID - Select a configured OCR Engine.
* Timeout - The number of minutes before the OCR process is timed out.
* File Extensions - Choose which file extensions will go through the OCR process.
* Only process files if no existing text content - If checked files that already have text content are not passed.
* Throw OCR engine exceptions - If checked show if errors occur during the OCR process.&#x20;
  * It will show an error and mark the item as errored.
* Create searchable PDF - If checked PDF files will show entities and metadata in the preview.
  * The storage settings must be configured within the OCR Configuration for this to work.

<figure><img src="../../../../../../.gitbook/assets/image (258).png" alt="" width="563"><figcaption></figcaption></figure>

### Advanced Options

1. Select Show Advanced Options
2. Define the maximum number of items to process concurrently in Bounded Capacity.
3. Define the maximum number of items that can be queued.&#x20;

{% hint style="info" %}
Limiting either of these will reduce the memory use but increase the time taken.
{% endhint %}
