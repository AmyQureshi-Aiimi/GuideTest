# File Extractor

You can control what happens to PST or Zipped files when they are added to a collection. By allowing them to be extracted in a collection users can freely see the files and process them as required.

<details>

<summary>SAR Prerequisites</summary>

The SAR Import settings must be enabled and the storage locations set.

[Use our guide on Importing Data For a SAR for help setting up SAR imports.](../../../../global-settings/sar/importing-data-for-a-sar.md)

* The File Import Size Limit should be the same size or bigger than the maximum archive size set in the job.
* The Source System needs to be a location that both the Agent and Web services can access.
* Within Advanced on the source make sure write, update and delete are checked.

</details>

<details>

<summary>Collection Prerequisites</summary>

You can allow extractions in both normal and redactable collections.

* For collections the destination source must be a Document Store.
* Within the source check Enable for Configurable Collection to allow the source to be selected within the job.
* Within Advanced on the source make sure write, update and delete are checked.

</details>

## Archives

1. **Process Email Archives** - If checked email archives (PST, OST) will be processed as part of this job.
2. **Extract File Archives** - If checked file archives (ZIP, RAR, 7z) will be processed as part of this job.
3. **Maximum Archive Size** - Enter the maximum size of an archive that can be processed in bytes.
   * Set to 0 for no limit.

<figure><img src="../../../../../.gitbook/assets/image (91).png" alt="" width="563"><figcaption></figcaption></figure>

## Email Attachments

1. **Extract Email Attachments** - If checked all email attachments will be extracted and stored as separate files to the email.
2. **Excluded Attachment Names** - Use Regular Expressions to choose what attachments are excluded from processing.&#x20;
   * This is based on the name of the attachment.
   * If left blank all will be processed.&#x20;

<figure><img src="../../../../../.gitbook/assets/image (92).png" alt="" width="563"><figcaption></figcaption></figure>

## Collections

1. Collection Filter - Select what type of collection this feature is enabled on from the dropdown.
   * All - Run the process when an eligible file is added to any collection.
   * Redaction Enabled - Only run the process when an eligible file is added to a collection with redaction enabled.
   * SAR Only -  Only run the process when an eligible file is added to a SAR collection.

### Upload Report

1. **Generate Upload Report** - If checked an upload report for each extracted archive will be generated.

<figure><img src="../../../../../.gitbook/assets/image (93).png" alt="" width="563"><figcaption></figcaption></figure>

