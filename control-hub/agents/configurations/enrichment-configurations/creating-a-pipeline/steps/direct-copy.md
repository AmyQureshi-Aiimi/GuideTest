# Direct Copy

This copies items between 2 file system sources. Copy needs to be enabled on the source within Aiimi Insight Engine and the underlying credentials used to access the source need write permissions.

### Limitations

There are a couple of limitation to using direct copy.

* It must be between 2 file system sources.
* It will only work when the service roots are not in use.
* The paths must be directly accessed with no drive mounting.
* The credentials needed for both source and destination are the same.

### Set Up

1. **Destination Source** - Select source to copy the item to.
2. **Destination Location** - Enter the location within the source where the item will be copied to.
   1. This will be source type specific.
3. **Overwrite** - If checked and a file exists in the target location with the same name it will be overwritten.
4. **Delete initial file** - If checked the original item from the original source will be deleted.
   1. The source credentials used must have delete permissions.
5. **Maintain folder path** - If checked the file path from the source will be recreated in the target.
6. **Exclude root location** - If checked the root of the path will be excluded from path creation.

<figure><img src="../../../../../../.gitbook/assets/image (243).png" alt="" width="563"><figcaption></figcaption></figure>

### Advanced Options

1. Select Show Advanced Options
2. Define the maximum number of items to process concurrently in Bounded Capacity.
3. Define the maximum number of items that can be queued.&#x20;

{% hint style="info" %}
Limiting either of these will reduce the memory use but increase the time taken.
{% endhint %}
