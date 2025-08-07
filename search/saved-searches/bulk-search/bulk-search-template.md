# Bulk Search Template

To set up a bulk search you will need a CSV with all of your searches. A bulk search CSV can be used once or as a template for future search processes. There is no limit to the number of searches you can add to a bulk search. The only limitation is the number of results that can be returned. This is limited to 10,000 results.&#x20;

A CSV file is easily created in excel but can be made in notepad or any text editor. It is a file type that separates information with a comma. It is the simplest way for Workplace AI to read multiple searches in an organised way.

## Creating a CSV

{% hint style="warning" %}
When creating your CSV the first column must always be the Search Name. It must have the title "Search Name" or it will fail to upload. You can arrange the rest of the file as you need.
{% endhint %}

<details>

<summary>Create a CSV In Excel</summary>

There is a maximum limit of 50 rows and columns and a size restrictions of 1MB or less per CSV.

1. The first cell (A1) must be Search Name.
   * The file will not upload if it is anything else.

The next rows will contain the details of each search and the terms that will be searched within each field. Each search must be on a separate line.&#x20;

1. Enter a name for the search in column A.
2. In the relevant columns enter the terms to search in that field.
   * Search for multiple terms in the same field by using a pipe (|) between the terms.
   * You can skip a field by leaving the cell blank.
3. In the next row repeat steps 2 & 3 until all your searches are added.

Searches are performed in the order they are in the CSV and notifications will appear in the same order. For example, if your file has 10 searches, row 1 would be completed first and it's notification sent, then row 2 would run and have it's notifications sent and so on

#### Complete Example ![](<../../../.gitbook/assets/image (252).png>)

Once you have added all of your searches save your file as a CSV and continue to Create your bulk search.

[Read how to set up a Bulk Search in Workplace AI.](create-a-bulk-search/)

</details>

<details>

<summary><strong>Create a CSV In a Text Editor</strong></summary>

There is a maximum limit of 50 rows and fields and a size restrictions of 1MB or less per CSV.&#x20;

Each value you add must be followed by a comma (,) with no space after it.

1. The first value of your CSV must be "Search Name,"
   * The file will not upload if it is anything else.
2. The next values in this row should contain the names of all the fields you would like to search followed by a comma (,).
   * Each of these values will be mapped to a field within Workplace AI.
   * These values will vary depending on the data you're searching. They should be descriptive to help set up the bulk search within Workplace AI.

```csv
Example:
Search Name,Business Name,Persons Name,Dates,Address,Contract ID
```

The next rows will contain the details of each search and the terms that will be searched within each field. Each search must be on a separate line.

1. Enter a name for the search as the fist value of a row followed by a comma (,).
2. For each field assigned in the first row enter the terms that will be searched followed by a comma (,).
   * You can search for multiple terms for the same field by using a pipe (|) with no spaces between the terms.
   * You can skip a field by leaving the value blank and adding the next comma.
3. When you have finished a search, the final value does not need a comma (,) at the end.
   * If you are leaving the final field blank the row will end with the comma that would be before the value.
4. Start a new line for every search and repeat steps 2 - 4 until all your searches are added.

Searches are performed in the order they are in the CSV and notifications will appear in the same order. For example, if your file has 10 searches, row 1 would be completed first and it's notification sent, then row 2 would run and have it's notifications sent and so on

```csv
Example Search:
Business Details,Tovicci LTD|Tovicci Limited,Doe,1997,123 Fake Street,C1234
```

```
Complete Example:
Search name,Business Name,Persons Name,Dates,Address,Contract ID
Business Details,Tovicci LTD|Tovicci Limited,,1997,123 Fake Street,C1234
Contacts,,Ann Example,,Aexample@Tovicci.com,
Owners,Tovicci,John Doe|Jon Doe,,456 Fake Street,
```

Once you have added all of your searches save your file as a CSV and continue to Create your bulk search.

[Read how to set up a Bulk Search in Workplace AI.](create-a-bulk-search/)

</details>

### Example CSV

{% file src="../../../.gitbook/assets/Example Bulk Search CSV.csv" %}
