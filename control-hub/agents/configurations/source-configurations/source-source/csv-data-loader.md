# CSV Data Loader

If you want to load structured or unstructured data from a CSV use the CSV data loader. Connect a BIM360 source to Workplace AI to make the most of your data.&#x20;

{% hint style="info" %}
To complete this you must have a published Data Model for this data.
{% endhint %}

1. **Source System:** Select CSV Data Loader from the dropdown.

## Input Files

In order to find the CSV files to load you need to complete the Input Files tab.

1. **Folder Path:** Enter the folder path for the CSV files location.
2. **File Pattern:** Enter a naming convention to when looking for CSV files.
   * You can use a wildcard to load multiple files within a path. For example entering \*.csv will load all files with the extension .CSV from the folder path.
3. **Complete Folder Path:** Enter the folder where completed CSV files should be moved to.
   * Set to done by default.
4. **Error Folder Path:** Enter the folder where failed CSV files should be moved to. This makes it easy to find and investigate failed files.
   * Set to error by default.
5. **Rows To Process:** To run a limited number of rows as a test enter a limit.
   * If left blank all rows will be processed.
6. **Field Delimiter:** Select the field delimiter used for these files. Choose between Comma, Tab, Pipe or Semicolon.
   * The file will not process unless this is set correctly.
7. **Multi-Value Delimiter:** Select the multi-value delimiter for these files. Choose between Comma, Tab, Pipe or Semicolon.
   * The file will not process unless this is set correctly.
   * This must be different to the Field Delimiter.

<figure><img src="../../../../../.gitbook/assets/Screenshot 2023-03-02 at 16.17.33.png" alt="" width="563"><figcaption></figcaption></figure>

***

## Core Properties

You can configure the type for each file property. By default all properties will be undefined, you can choose between: Undefined, Value, Composite, Constant and Calculated.&#x20;

{% hint style="info" %}
Properties marked with a red asterisk \* require definition.
{% endhint %}

1. **Core Property List:** Select the property you want to define.
2. **Property Details:** On the right, choose the property type from the dropdown.

Depending on the property type selected you may need to define more.

<table><thead><tr><th width="139">Property</th><th>Definition</th></tr></thead><tbody><tr><td>Undefined</td><td>These fields will not be mapped.</td></tr><tr><td>Value</td><td>Select the Column to map this field to.</td></tr><tr><td>Composite</td><td><em>Create a string using text and numbers within curly brackets {}.</em><br>Add the components of the string and select the inputs that will sit in place of the numbers once processed.</td></tr><tr><td>Constant</td><td>This populates a field with the same text value no matter what.</td></tr><tr><td>Calculated</td><td><p>This enters either the current date or Current date and time into a field.</p><p>This is the time of the load running.</p></td></tr></tbody></table>

<figure><img src="../../../../../.gitbook/assets/Screenshot 2023-03-02 at 16.18.06.png" alt="" width="563"><figcaption></figcaption></figure>

***

## Model Data Attributes

To connect a field from the file to an attribute in a data model you need to run a file with 3-5 data rows for validation. This will pull in all the field labels from the file. Once run you can then complete the mappings the same way as core properties.

1. **Business Model:** Select the relevant Business Model.
2. **Property List:** Select the property you want to define.
3. **Property Type List:** Choose the property type from the list on the right.
   * Depending on the property type selected you will need to define more.

<table><thead><tr><th width="139">Property</th><th>Definition</th></tr></thead><tbody><tr><td>Undefined</td><td>These fields will not be mapped.</td></tr><tr><td>Value</td><td>Select the Column to map this field to.</td></tr><tr><td>Composite</td><td><em>Create a string using text and numbers within curly brackets {}.</em><br>Add the components of the string and select the inputs that will sit in place of the numbers once processed.</td></tr><tr><td>Constant</td><td>This populates a field with the same text value no matter what.</td></tr><tr><td>Calculated</td><td><p>This enters either the current date or Current date and time into a field.</p><p>This is the time of the load running.</p></td></tr></tbody></table>

<figure><img src="../../../../../.gitbook/assets/Screenshot 2023-03-02 at 16.19.01.png" alt="" width="563"><figcaption></figcaption></figure>

***

## Validation

Once everything is defined you can run the test file once more to check the fields and data are mapped correctly. If they are not go back to Model Data Attributes or Core Properties to correct them.

1. **Upload:** Drag and drop a file for validation or select Upload Here to find a search for a file.
2. **Validate:** Once loaded, select validate.
   * This can be run multiple times until you are happy with the selections.

<figure><img src="../../../../../.gitbook/assets/Screenshot 2023-03-02 at 16.21.58.png" alt="" width="563"><figcaption></figcaption></figure>

### Completed the Source section&#x20;

1. Once you have completed this section, select Crawl. [Learn how to complete the source Crawl set up.](../source-crawl.md)
