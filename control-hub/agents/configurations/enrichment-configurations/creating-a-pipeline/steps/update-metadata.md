# Update Metadata

Workplace AI's enrichment capabilities can turn data and documents into actionable insights. It can extract known and unknown entities from text and classify documents based on its name or its contents.&#x20;

You can write the new information back to the source with an Update Metadata enrichment step. Making those insights available and actionable outside of Workplace AI.  &#x20;

{% hint style="info" %}
This is currently only available for Sharepoint and Content Server.
{% endhint %}

<details>

<summary>Prerequisites</summary>

1. A Sharepoint or Content Server source configuration must be in place for this.
   * For more help with this [see our guide on Configuring sources.](../../../source-configurations/)
   * Within this source on the advanced tab, the Allow Update Actions must be enabled.
   * The credential associated with this source must have the correct permissions to make these changes to the source.
2. Enrichment steps are set up to identify additional information that can be written back to the source.

</details>

1. **Source Field Name** - Select the Workplace AI field that will be written back.
2. **Target System Field Name** - Enter the field name from the target system to map it to.&#x20;
   * This field is formatted differently depending on the source.&#x20;
     * Content Server format: `<category name>:<attribute name>`
     * Sharepoint format: `<column name>`

<figure><img src="../../../../../../.gitbook/assets/image (853).png" alt="" width="563"><figcaption></figcaption></figure>

### Supported field types

* Date (Calendar/Field/Popup) with or without time
* Flag (Checkbox)
* Integer (Field/Popup)
* Text (Field/Multiline/Popup)
* Single and multi-value fields are supported

If any provided value does not match the Content Server attribute definition, the whole update will be failed. For example, providing 10 values for an attribute that only allows 5 or a 50 character string to an attribute that is capped at 32 characters.

### Advanced Options

1. Select Show Advanced Options
2. Define the maximum number of items to process concurrently in Bounded Capacity.
3. Define the maximum number of items that can be queued.&#x20;

{% hint style="info" %}
Limiting either of these will reduce the memory use but increase the time taken.
{% endhint %}
