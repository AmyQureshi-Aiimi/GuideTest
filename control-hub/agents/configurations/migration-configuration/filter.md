# Filter

Filtering your migration data means you can migrate what you need and leave everything else where it is.

1. Create a list of File Extensions you would like to exclude or include from your migration.
   * Select an extension type from the dropdown list it will add all the extensions for that type below.
   * or type an extension and select the add button.
   * You can remove or edit an extension from the list using delete and edit button.
2. Choose if the file extension list is included or excluded using the allowlist or denylist checkbox.
   * Check Include Files with No Extension to Include them within your list.
3. You can limit the documents migrated by entering the size range into File Size (B).&#x20;
   * You can remove blank documents or large files using this.
4. Choose the files included within a migration by entering a Modified Date Range. By entering a date range files outside of this will not be migrated.
5. Build an elastic query string using elastic syntax to select specific documents.
6. You can enter a list of statuses that will be included within the migration.&#x20;
   * If no statuses are add all statuses will be included.&#x20;
7. Choose what actions are performed during migration. By entering actions into the File Action field these actions will be applied to the relevant field with this action tagged.&#x20;
8. Check Regenerate Thumbnails to create thumbnails for documents with no thumbnails or files that need to be updated.

<figure><img src="../../../../.gitbook/assets/image (296).png" alt="" width="563"><figcaption></figcaption></figure>
