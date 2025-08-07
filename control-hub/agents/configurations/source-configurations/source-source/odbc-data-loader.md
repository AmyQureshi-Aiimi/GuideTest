# ODBC Data Loader

If you want to load data structured or unstructured from a ODBC file use the ODBC data loader.

To complete this loader you must have a completed Data Model created to match this data. The Data Model must be published to show in the creation of this Data Loader.

## **Database**

In order to find the files to load you need to complete the Database tab.

1. To determine the driver to use and how to connect to it enter the Connection String.
   * You must specify the Driver and any source specific settings.
   * You can enter Username and Passwords using UID and PWD or choose from the Credentials list.
   * Example String: "Driver=(MySQL ODBC 8.0 Unicode Driver);Server=server;Database=database;MULTI\_HOST=1"
2. Choose the relevant Credential from the dropdown list.
   * _For support setting up credentials use_ [_our guide on managing credentials._](../../../../security/credentials.md)
3. If the database fields are case sensitive check Case Sensitive or the data loader will not be able to differentiate between field names.
4. Build the Query that should be executed. This must return one row for each object that needs to be created.
   * Parameters can be specified with a ? and used to filter the results.
5. Preserve last access date - Where possible, the last access date when they are accessed by system functions will be kept. The service account must have sufficient permissions to update file attributes.
   * This may not be possible with all file systems and they may not allow this.
   * You must also set the enable the content retrieval, preserve last access date for this to function.
6. Enter the Elastic field names in Parameters, that will be used to calculate parameter values via a max aggregation.
   * This field must be DateTIME or Long.
7. When processing a file if an error occurs you can choose what folder the file goes to. Add the Log Path so you can find the errors in the future.
8. You can run a limited number of rows as a test for processing. It will run the process on that number of rows and they will be processed to Aiimi Insight Engine. Enter the number of rows that should be processed to Rows To Process.
   * If left blank all rows will be processed.
   * This is also beneficial of the database has query or row limits.
9. If a file is using something other than Pipes to separate multi-values you can choose it from Multi-value Delimiter.
   * The file will not process unless the delimiter is set correctly.

<figure><img src="../../../../../.gitbook/assets/image (10).png" alt=""><figcaption></figcaption></figure>

## **Core Properties**

For each file property you can choose its type. By default all properties will be undefined, you can choose between: Undefined, Value, Composite, Constant and Calculated. Fields marked with a red asterisk \* require a definition.

1. Select the property you want to define.
2. Choose the property type from the list on the right.
   * Depending on the property type selected you will need to define more.

<table><thead><tr><th width="165">Property Type</th><th>Definition</th></tr></thead><tbody><tr><td>Undefined</td><td>These fields will not be mapped.</td></tr><tr><td>Value</td><td>Select the Column to map this field to.</td></tr><tr><td>Composite</td><td>Create a string using text and numbers within curly brackets {}.<br>Once you have added the components of the string you can select the inputs that will sit in place of the numbers once processed.</td></tr><tr><td>Constant</td><td>This will populate a field with the same text value no matter what.</td></tr><tr><td>Calculated</td><td><p>This will enter either the current date or Current date and time into a field.</p><p>This is the time of the load running.</p></td></tr></tbody></table>

<figure><img src="../../../../../.gitbook/assets/Screenshot 2023-03-03 at 16.49.07.png" alt="" width="563"><figcaption></figcaption></figure>

## **Model Data Attributes**

To connect a field from the file to an attribute in the data model you need to run a file with 3-5 data rows in to the validation.

This will pull in all the field labels from the file. Once run you can then complete the mappings the same way as with core properties.

1. Select the relevant Business Model.
2. Select the property you want to define.
3. Choose the property type from the list on the right.
   * Depending on the property type selected you will need to define more.

<table><thead><tr><th width="165">Property Type</th><th>Definition</th></tr></thead><tbody><tr><td>Undefined</td><td>These fields will not be mapped.</td></tr><tr><td>Value</td><td>Enter the Column name to map this field to.</td></tr><tr><td>Composite</td><td>Create a string using text and numbers within curly brackets {}.<br>Once you have added the components of the string you can select the inputs that will sit in place of the numbers once processed.</td></tr><tr><td>Constant</td><td>This will populate a field with the same text value no matter what.</td></tr><tr><td>Calculated</td><td><p>This will enter either the current date or Current date and time into a field.</p><p>This is the time of the load running.</p></td></tr></tbody></table>

<figure><img src="../../../../../.gitbook/assets/Screenshot 2023-03-03 at 16.50.30.png" alt="" width="563"><figcaption></figcaption></figure>

## **Validate**

Once all features are defined you can run the test file once more. You can then check the fields and data are mapped correctly. If they are not go back to Model Data Attributes or Core Properties to correct them.

1. Drag and drop a file for validation or select Upload Here to find a search for a file.
2. Once loaded select validate.
   * This can be run multiple times until you are happy with the selections.
3. Select Save when you are done.

<figure><img src="../../../../../.gitbook/assets/Screenshot 2023-03-03 at 16.51.23.png" alt="" width="563"><figcaption></figcaption></figure>

