# Trie Entity Extractor

This step extracts keywords from text based on either regular expressions or dictionaries of terms (single or multi-word).

It uses a trie data structure to store the text and lookup values. It improves the speed and efficiency of an entity extraction. This works with entity definitions that are set up in Control Hub. We recommend you are familiar with these configurations before using this step.

* Normalise White Space - Assume any white space is a space in the text.
* Proximity Disabled File Types - Enter any file types that will not include proximity words to help validate regular expression extracted terms.&#x20;
* Include File Name - If checked, entities will be extracted from the filename.
* Include File Location - If checked, entities will be extracted from the file location.
* Whitespace Characters - Enter any characters that should be considered as whitespace.
* Entities - Select the entities to extract. What is extracted is defined in the entities section of Control Hub.

<figure><img src="../../../../../../.gitbook/assets/image (627).png" alt="" width="563"><figcaption></figcaption></figure>

### Advanced Options

1. Select Show Advanced Options
2. Define the maximum number of items to process concurrently in Bounded Capacity.
3. Define the maximum number of items that can be queued.&#x20;

{% hint style="info" %}
Limiting either of these will reduce the memory use but increase the time taken.
{% endhint %}
