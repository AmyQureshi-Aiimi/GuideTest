# Data File Cataloguer

Connect your Data File Cataloguer to Workplace AI to make the most of the data.

1. **Source System:** Select Data File Cataloguer from the dropdown.

## **Initial Configuration Steps**

1. **Sources:** Enter the sources the should be crawled for data files.
2. **Sample Rows:** Enter the number of rows that should be run as a test.&#x20;
   * This is the number of sample rows that will be extracted from each data file.
3. **Download folder:** Enter the folder path that will store download files as they are being catalogued.&#x20;
   * This location must be accessible by the machine running the crawl.
   * If left blank or NULL the system temp folder will be used.

***

## Additional Settings

1. **Attempt direct access:** If checked this improves performance of files on a file share.
   * If direct access fails or cannot be used the file will be downloaded locally.
2. **Limit deltas to new or deleted file only:** If checked only new or deleted files will processed. Modified files will not update.&#x20;
   * This improves performance but the accuracy of content can suffer.
3. **Multipart parquet support:** If checked it will process groups of parquet files in a folder as one file with multiple parts.&#x20;
   * Each part must be name "part-(#)-tid-(guide)-(name).parquet" for this to work.
4. **Approximate multipart parquet row count:**&#x20;
   * If checked it will count the first part of a multipart parquet and multiply that by the number of parts.

<figure><img src="../../../../../.gitbook/assets/image (4).png" alt="" width="563"><figcaption></figcaption></figure>
