# Viewer

Set your PDF Tron licence using the Viewer page. Setting this will provide an enhanced preview experience for users in Workplace AI.

This allows users to preview the text content of a document within Workplace AI. Users no longer need to download document or be redirected to open documents in its source location. This means users can review documents for compliance purposes and more gather further insights.&#x20;

## Viewer Configuration

1. Enter the License key for the third party viewer software into the Viewer License Key.&#x20;

<figure><img src="../../.gitbook/assets/image (417).png" alt="" width="563"><figcaption></figcaption></figure>

***

## Preview Cache

1. **Enable Preview Cache** - Check this to enable this feature.
2. **Cache Size Limit** - Set the maximum size of a file that can be cached with the limit slider.
3. **Expiration Window** - Set how long a preview is cached for with the slider.

<figure><img src="../../.gitbook/assets/image (362).png" alt="" width="563"><figcaption></figcaption></figure>

***

## Preview File Size Limits

1. **Default File Size Limit** - Set a size limit for files that can be previewed.&#x20;
   * Enter a Default File Size Limit in bytes.

<figure><img src="../../.gitbook/assets/image (636).png" alt="" width="563"><figcaption></figcaption></figure>

***

## Custom File Size Limits

You can customise the file size limits per extension within custom file size limits.

1. **Extensions** - enter or use the dropdown to select an extension group.
2. **File Size Limit** - Enter the File Size Limit you want to apply to this extension.
3. Select Add Configuration.

<figure><img src="../../.gitbook/assets/image (307).png" alt="" width="563"><figcaption></figcaption></figure>

***

## Redacted Document Storage

Information can be redacted from items within a SAR or a collection. In order for these redacted items to be saved you must configure the document storage.

1. **Redaction Storage Configuration:** Select where redacted documents will be stored from the dropdown.&#x20;
   * Azure Storage, File System Storage, Google Storage

<figure><img src="../../.gitbook/assets/image (181).png" alt="" width="563"><figcaption></figcaption></figure>

#### Azure Storage

1. **Endpoint Suffix:** Enter the suffix for the endpoint suffix for the storage account.&#x20;
2. **Account Name:** Enter the Account Name linked to the storage account.
3. **Access Key Type:** Select either Account or SAS from the dropdown.
4. **Select Credential:** Choose the credential to be used for this storage.
5. **Azure container ID:** Enter the root container ID for this storage.&#x20;

#### File System Storage

1. **Store Root:** Enter the root folder of this File System Storage.
2. **Reserved Disk Space:** Enter the amount of reserved disk space for this storage in bytes. This will reserve space within the storage system for redacted data.
3. **Error on full storage:** Enable this to be notified if this space becomes full.&#x20;

#### Google Storage

1. **Project ID:** Enter the Project ID for the Google Cloud Platform.
2. **Bucket Location:** Select the Google Cloud Platform Bucket Location from the dropdown.
3. **Bucket Prefix:** Enter the prefix for all the buckets in the Google Cloud Platform.

***

## Watermarking

Configure and control the watermarks users are allowed to add to items within Workplace AI. Watermarking can be toggled on and off using the toggle within Control Hub.

1. Select the New Watermark button to create a new watermark.
   * This will open a New Watermark Wizard.

#### Details

1. **Name** - Enter a name for the watermark.
2. **Description** - Add a description of the watermark to help others no what it is for.
3. Select continue to Settings.

#### Settings

You can customise the watermark and choose what it says and how it appears on items. Each setting can vary depending on the placement.

1. **Placement** - Shows where on an item the watermark will show.
2. **Text** - Enter what the watermark should say.
   * The watermark copy must be added to every placement you want this to appear. If a line is left blank the watermark will not appear there.
3. **Colour** - Choose the colour of the watermark by entering a HEX value.
4. **Opacity** - Select how opaque the watermark should be from the drop down.
5. **Font** - Choose the font and size of the watermark.
6. Select Create New Watermark.

***

## Spreadsheet Preview

Determine what files are viewed as a table depending on the extension.

1. **Table View Extensions** - Select all of the extensions that should be viewed as a table.
   * By default .tsv and .csv are enabled.

<figure><img src="../../.gitbook/assets/image (95).png" alt="" width="563"><figcaption></figcaption></figure>
