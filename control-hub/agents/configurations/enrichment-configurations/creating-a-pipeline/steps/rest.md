# REST

The REST step is used to call external REST enrichment steps. You would have typically set up the Python REST Service which ships with the product, and may be either using some of our out of the box steps or you may have written your own steps.

### Add a process step name

If you have multiple rest steps, each one must have a unique name.

1. Select the enter name text box.
2. Enter a name or description for this step.
3. Select the apply this name button. <img src="../../../../../../.gitbook/assets/image (235).png" alt="Check mark icon" data-size="line">
   * If you need to change this at any point you can select the edit this name button. <img src="../../../../../../.gitbook/assets/image (236).png" alt="" data-size="line">

### Out of the box enrichment steps

* classify - Classify documents based on our machine learning capability.
* phrases - Extract phrases, topics and concepts from text.
* summary - Generate a summary for a document.
* hugginfacener - Extract people, organistions and locations from text.
* entity\_mapper - Map entities to normalised values.
* language - Determine the language of text.
* spacyner  - Extact named entities with spacy.

**Please see the Python REST Service installation and configuration guide for how to configure each step.**

<figure><img src="../../../../../../.gitbook/assets/image (402).png" alt="" width="563"><figcaption></figcaption></figure>

### Advanced Options

1. Select Show Advanced Options
2. Define the maximum number of items to process concurrently in Bounded Capacity.
3. Define the maximum number of items that can be queued.&#x20;

{% hint style="info" %}
Limiting either of these will reduce the memory use but increase the time taken.
{% endhint %}
