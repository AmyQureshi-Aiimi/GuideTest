# Tika Text Extraction

Tika Text Extraction converts native documents to plain text, this is what is indexed in Workplace AI.

* Endpoint - The endpoint for the Tika service.
  * There is usually an instance running on each enrichment server.
* Timeout - How long to let a text conversion run before it is cancelled.
* Text Content Types - Enter file extensions that are already text, and can be skipped.
*   Email Content Types - Enter the file types for emails.

    * This can be left as default in most instances. If you're not sure, please reach out to your contact at Aiimi.



    <figure><img src="../../../../../../.gitbook/assets/image (231).png" alt="" width="563"><figcaption></figcaption></figure>



    ### Advanced Options

    1. Select Show Advanced Options
    2. Define the maximum number of items to process concurrently in Bounded Capacity.
    3. Define the maximum number of items that can be queued.&#x20;

    {% hint style="info" %}
    Limiting either of these will reduce the memory use but increase the time taken.
    {% endhint %}
