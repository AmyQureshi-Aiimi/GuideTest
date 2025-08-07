# Text Cleaner

The text cleaner cleans up any text that has been produced by an OCR process. It checks for excessive character runs and other configured text content restraints.&#x20;

1. Select all the methods you want to use from the Cleaning Process dropdown.
   * Remove Long Strings - Strings over a certain length will be removed from the text.
   * Remove Null Characters - Any blank characters will be removed.
   * Remove Non ASCII Characters - Any characters not in the American Standard Code for Information Interchange will be removed.
   * OCR Cleanup - Improve the accuracy of your OCR process by defining rules for cleaning.
   * Remove Blank Lines - Any blank lines will be removed.

<figure><img src="../../../../../../.gitbook/assets/image (302).png" alt="" width="257"><figcaption></figcaption></figure>

### Remove Long Strings

1. When selected a Maximum Continuous Characters must be set.&#x20;
   * Any text longer than this with no spaces or delimiters will be removed.&#x20;
2. Enter any delimiters to be used other than full stops. These will be used to determine the length of a sentence.

### OCR Cleanup

1. In OCR Cleanup Dictionary File path enter the dictionary Path yo use when word checking.
   * Aiimi can provide a dictionary set if required.
2. Check ignore proper nouns to ignore the ignore their spelling within an OCR.
3. Check Only Clean If OCR Metadata Present to only check documents that have passed OCR.
4. &#x20;Within Words to Ignore for OCR Cleanup, enter any words that should be ignored from the spellcheck.&#x20;
   * There is no limit to the number of words you can add.
   * You can remove and edit words in the list using the edit or delete buttons next to the word.

<figure><img src="../../../../../../.gitbook/assets/image (225).png" alt="" width="375"><figcaption></figcaption></figure>

### Advanced Options

1. Select Show Advanced Options
2. Define the maximum number of items to process concurrently in Bounded Capacity.
3. Define the maximum number of items that can be queued.&#x20;

{% hint style="info" %}
Limiting either of these will reduce the memory use but increase the time taken.
{% endhint %}
