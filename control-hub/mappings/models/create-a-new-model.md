# Create a New Model

## Business Area

1. Select Create New Model.
2. **Business Area** - Select a business area from the drop down.
   * Business areas are a way of grouping data models.
3. Select Next.

Or

1. Select '+ Create New' to create a new business area.
2. Enter a name for the new Business Area.
3. Select Next.

<figure><img src="../../../.gitbook/assets/image (87).png" alt="" width="563"><figcaption></figcaption></figure>

***

## Details

1. **ID** - Enter a unique ID for the model. (This must be lowercase and letters only.)
2. **Display Name** - Enter a user friendly name.&#x20;
3. **Description** - Enter a short description.
4. **Default Colour** - If you want to show this model with a specific colour enter a hex code.
5. **Default Icon** - If you want to use a custom icon enter a file name.
   * The icon needs to be within the custom icons directory which is defined in app settings.
6. Select the model type from Standard, Map or Sub Model.
   * Standard
     1. To have any property mappings added to file indices check Applies to Files.&#x20;
     2. To have any property mappings added to file collections check Applies to Collection.
   * Map
     1. To Indicate the top most level of a data map check Root Level Model.
   * Sub Model
     1. Select the related model from the dropdown.&#x20;

<figure><img src="../../../.gitbook/assets/image (88).png" alt="" width="563"><figcaption></figcaption></figure>

***

## Attributes

{% hint style="info" %}
If you are updating to Primo you will need to update your Geo-points attributes to work on the map lens.
{% endhint %}

1. **Attribute ID** - Add a Unique ID for the model attribute. (This must be lowercase letters only.)
2. **Display Name** - Enter a user friendly name for the model.&#x20;
3. **Data Type** - Select a Data Type for this attribute from the dropdown.
4. **Link to: Model** - Link attributes to other data models by selecting the Model from the dropdown.&#x20;
   * This enables data navigation features within the app.
5. **Permissions** - Enter the user groups that can see this attribute.
6. **Notes** - Add notes to the attribute to describe the attribute.

* **Required** - Check if the attribute field is mandatory.
* **Multivalue** - Check if this attribute can have multiple values.
* **Surface on Map Lens** - Check this for geo-point attributes to show on the attribute on the map.
* **Searchable as Text** - Check this to show a text field below for full-text search.
* **Visible** - Check this to show the attribute in the front end.
* **Document Link** - Check this if this attribute is linked to an entity used to show matching documents.

<figure><img src="../../../.gitbook/assets/image (89).png" alt="" width="563"><figcaption></figcaption></figure>

***

## Display

1. Enter the Number of Visible Data Properties that show per data result on page load.
2. Check Show Hit Highlights to Highlight content in the search results.
   * Hit highlights will highlight the terms from your search that match your results.
3. Check Show text on details page to view surface this information within the Details view.

<figure><img src="../../../.gitbook/assets/image (90).png" alt="" width="563"><figcaption></figcaption></figure>

***

## Summary

Review all of the settings within the summary tab before saving.

{% hint style="warning" %}
Once you have published a model you can't edit its attributes.
{% endhint %}

<figure><img src="../../../.gitbook/assets/image (533).png" alt=""><figcaption></figcaption></figure>
