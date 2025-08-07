# GoogleVaultSAR

<details>

<summary>Prerequisites</summary>

1. You must have a model set up specifically for SARs.
   * This model requires a keyword attribute with the ID "matterId".

For help setting up a model [visit our guide for creating models.](../../../../mappings/models/)

</details>

### Connection settings

1. Select GoogleVaultSAR from the Job Type dropdown.
2. Select the Credentials for the Google Vault.
   * These were from the JSON file downloaded when the service account was created.
3. Enter the Vault user name to be used when accessing Vault via the API.

<figure><img src="../../../../../.gitbook/assets/image (288).png" alt="" width="563"><figcaption></figcaption></figure>

### Search Settings

1. Choose which vault areas will be searched by checking the relevant Search Scope checkbox.
2. Enter a maximum number of items that can be exported from a single query within Single Query Export Limit.
   * This figure is applied before de-duplication.
   * It is checked before Mail items are exported. This is because Drive queries don't support being counted.
   * Drive exports are checked after execution and before importing to Workplace AI.
3. To delete any matter added to Google Vault check Delete Matter After Upload.
   * Turn this off to review what Vault did or to redo an export via Google Vault directly.
4. Limit the size of an export blob by entering the value in Bytes within Processable Export Size Limit.
   * By default this is set to 10MB.
5. Remove files with duplicate IDs by checking Remove Duplicate Files.
   * Helpful for removing emails that appear in sent and inbox folders.
6. Create a CSV report for each export by checking Create Upload Report.
   * This will be added to the import store and SAR Collection the items relate to.

<figure><img src="../../../../../.gitbook/assets/image (560).png" alt="" width="563"><figcaption></figcaption></figure>
