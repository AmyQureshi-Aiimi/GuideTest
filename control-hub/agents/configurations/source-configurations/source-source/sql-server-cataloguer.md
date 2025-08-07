# SQL Server Cataloguer

Connect your SQL Server to Aiimi Insight Engine to make the most of the data in your business. Once you have selected a Source System type more detail will expand to customise this.

1. Enter the address of the SQL server you want to access in Server Address.
2. Enter the name of any databases to crawl within Databases.
3. Select the username and password from the Select Credential dropdown for this server.
   * _For support setting up credentials use_ [_our guide on managing credentials._](../../../../security/credentials.md)
4. Enter the number of Sample Rows to use.
   * Enter the number of sample rows to extract from each table.
   * If set to 0 no sample will be generated.
   * Existing samples will be preserved where possible.
5. Enter a Max Text Length.
   * This is the maximum number of characters that will be taken from a text column.
6. Check Include Views to include views and tables in the catalogue.

<figure><img src="../../../../../.gitbook/assets/image (13).png" alt="" width="563"><figcaption></figcaption></figure>
