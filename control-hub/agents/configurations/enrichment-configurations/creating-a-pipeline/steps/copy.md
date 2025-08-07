# Copy

This copies items from one source to another. Copy needs to be enabled on the source within Aiimi Insight Engine and the underlying credentials used to access the source need write permissions.

<details>

<summary>Hardcoded Strings and Placeholders</summary>

Destination Location, Folder Path and File Name can be constructed of hardcoded strings,  placeholders that are replaced at runtime or a combination.

### Placeholders

Placeholders can be a core property, metadata value or an entity value that exist against an indexed file.&#x20;

You can use entities and metadata within Aiimi Insight Engine as placeholders (use the prefix "entities." or "metadata."). You can use nested properties by referencing the path. Ffor example, {entities.pii.emailAddress} would replace the placeholder with the emailAddress property from the PII Entity group.

There is an option to have a safe fallback on the placeholder for if the value is null, this can be achieved using a pipe within the placeholder, for example {metadata.important|"unimportant"} - this will look for a metadata field named important, if it exists the property will be used, otherwise it will use unimportant as the value.

#### Core Properties

| core.id               | core.uri              | core.statusDate     |
| --------------------- | --------------------- | ------------------- |
| core.objectId         | core.location         | core.crawlDate      |
| core.version.number   | core.relativeLocation | core.enrichmentDate |
| core.version.fromDate | core.name             | core.createdDate    |
| core.version.toDate   | core.extension        | core.modifiedDate   |
| core.type             | core.size             | core.accessedDate   |
| core.sourceType       | core.SHA512           | core.owner          |
| core.sourceId         | core.status           |                     |

</details>

* **Destination Source** - Select source to copy the item to.
* **Destination Location** - Enter the location within the source where the item will be copied to.
  * This will be source type specific.
  * This can be constructed with hardcoded strings or using placeholders that are replaced at runtime or a combination.
* **Folder Path** - Enter a custom folder path to determine the folder structure for the items in the source location.
  * {core.relativeLocation} will recreate the folder structure from the original source in the destination location. Alternatively you can set a static name to create one folder for everything to live in.
  * This can be constructed with hardcoded strings or using placeholders that are replaced at runtime or a combination.
* **File Name** - Enter a custom naming convention for the copied items.
  * {core.name} will maintain the files name.&#x20;
  * This can be constructed with hardcoded strings or using placeholders that are replaced at runtime or a combination.
* **Duplicate Handling** - Select how duplicates are processed in the destination system from the dropdown.
  * Error - This fails the file, marks it in an Error state and continues processing.
  * Overwrite - This overwrites the existing file in the destination location.
  * Deduplicate - This creates files with an incrementing number in the name for uniqueness.
    * For example if MyFile.pdf exists, the new copied file will be named MyFile(2).pdf, then MyFile(3).pdf and so on.

<figure><img src="../../../../../../.gitbook/assets/image (28).png" alt="" width="375"><figcaption></figcaption></figure>

### Advanced Options

1. Select Show Advanced Options
2. Define the maximum number of items to process concurrently in Bounded Capacity.
3. Define the maximum number of items that can be queued.&#x20;

{% hint style="info" %}
Limiting either of these will reduce the memory use but increase the time taken.
{% endhint %}
