# Source - Crawl

Enter the details to locate folders and files that need syncing. You can choose the type, location or size of a file to pull into Aiimi insight Engine.

1. To add extensions to an Include or Exclude list type them into the File Extensions box.
   * To add types of files you can use the drop down to remove a predetermined group of extensions.
   * You can edit an extension by selecting the Edit Pencil icon or delete it using the Delete Bin icon.
2. Once you have added File Extensions to the Crawl you can choose if you are creating an allow or exclude list.
   * If you want to exclude items from your Crawl check Denylist.
   * If you want to include items from your Crawl check Allowlist.
3. Enter the name of any specific files that you want to exclude within Excluded Files as a RegEx.

<figure><img src="../../../../.gitbook/assets/Screenshot 2023-02-15 at 10.11.50.png" alt="" width="563"><figcaption></figcaption></figure>

4. To exclude an entire folder from the Crawl enter the file name as a RegEx into Excluded Folders.
5. Stop certain Users and Groups from being indexed by adding them to the Excluded Users and Groups. This must be written as a RegEx.
6. Determine the size of files that will be crawled by adding a minimum and maximum to the File Size (B) field. This can be helpful if you want to avoid empty files.
   * Leaving this as 0 - 0 will Crawl all files no matter the size.
7. To set files as sensitive based on an entity choose from the drop down list under Sensitive Entities.
   * For example, you may want to mark all files with PCI or PII data as sensitive.

<figure><img src="../../../../.gitbook/assets/Screenshot 2023-02-15 at 10.13.11.png" alt="" width="563"><figcaption></figcaption></figure>
