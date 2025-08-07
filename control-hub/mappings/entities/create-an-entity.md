# Create an Entity

Entities live within groups and are labels that can be associated with data and documents. They help discover, link and visualise information in Workplace AI.

## Add an Entity

1. Select a Group for the new entity to sit within.
2. Select New Entity.

***

## **Details**

1. **Friendly Name** - Enter a user friendly name for the entity.
   * We recommend a brief description of the entity.
2. **Name** - Enter a Name for the entity.
   * This will be displayed under the friendly name.
3. **Type** - Select the data type from the dropdown
   * Choose between Keyword, Long, Double, DateTime GeoPoint, Text, Float, User or Uri.
4. **Enabled** - Check this to allow this entity to be used.
5. **Lower Case Value** - Check this if the case of the entity does not matter.&#x20;
   * This is used by document links.
6. **Search Suggestions** - Check this for entities of this type to appear in search suggestions. &#x20;

### Type Variables

Depending on the type selected you can determine if it's searchable as text or keyword. If the field value appears in text content or data, you won't need to make the field searchable.

* Searchable as Text - If checked, users can find this field using a text query.
* Searchable as Keyword - If checked, users can find this field as a non case-sensitive keyword.
* Surface on Timeline Lens - If checked, users can surface this field as a date on the Timeline Lens.
* Surface on Map Lens - If checked, this field is surfaced on the Map lens.

7. Select Next.

<figure><img src="../../../.gitbook/assets/image (590).png" alt="" width="375"><figcaption></figcaption></figure>

***

## Permissions

1. In most cases the permission can be left empty.&#x20;
   * Reach out to your Aiimi contact for more information.
2. Select Next.

***

## Extraction

#### Trie Entity Extractor or PCI Extractor

If you are using a Trie Entity Extractor or PCI Extractor you need to configure extraction properties for the entity.&#x20;

{% hint style="info" %}
If you are populating this entity with an enrichment step, skip this and select Next.
{% endhint %}

* **List of Terms** - Select this to extract using a dictionary of terms. You can upload your list or add the terms manually.
* **Regex** - Select this if you have one or more regular expression to use for extraction. You can upload your Regular Expressions or add them manually.&#x20;
  * You can also add proximity terms to confirm the regex extraction. Add those proximity terms to the List of Terms.
* **Model** - Select this if the lookup terms exist in a data model. Then select the model and the model property to use.

{% hint style="warning" %}
A property with a large number of unique values will take a long time to start.
{% endhint %}

<figure><img src="../../../.gitbook/assets/image (615).png" alt="" width="375"><figcaption></figcaption></figure>

***

## Summary

Review the entity making sure it is correct and then select Save. Please note you can't change the ID or data type of an entity once created.
