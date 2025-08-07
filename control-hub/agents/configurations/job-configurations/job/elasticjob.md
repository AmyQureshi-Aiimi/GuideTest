# ElasticJob

1. Enter the Elastic Command directly into the Elastic Command box.
   * This should be written in Elastic Query DSL.
   * You can find information about this on Elastics website.  [https://www.elastic.co/guide/en/elasticsearch/reference/current/query-dsl-query-string-query.html](https://www.elastic.co/guide/en/elasticsearch/reference/current/query-dsl-query-string-query.html)
2. Select the credential to use for this Job.
   * These will be used instead of the default Elastic username.
3. Check Use Task API to track tasks using Task Management API.
   * This is best for long term tasks like snapshot, reindex, restore and large update-by-queries.
   * If not enabled jobs will run but the Job Results returned may not be correct.
4. Check Retry to retry tasks that have stopped unexpectedly.

<figure><img src="../../../../../.gitbook/assets/image (514).png" alt=""><figcaption></figcaption></figure>
