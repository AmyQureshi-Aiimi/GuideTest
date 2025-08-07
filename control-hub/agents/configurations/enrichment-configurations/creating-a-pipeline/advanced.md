# Advanced

### Status Definition

1. **Success Status:** Enter the status to apply to items that are successfully enriched.
2. **Error Status:** Enter the status to apply to items that fail enrichment.

<figure><img src="../../../../../.gitbook/assets/image (785).png" alt="" width="563"><figcaption></figcaption></figure>

### Enrichment Limitations

1. **Initial Buffer Capacity:** Choose the amount of work to queue at the start of the pipeline.
   * 50 by default. This should be fine in most situations.
2. **Update Maximum Degree of Parallelism:** Enter the maximum number of messages that can be processed by the pipeline at the same time.
   * -1 by default. This should be fine in most situations.
3. **Update Bounded Capacity:** Enter the maximum number of messages that can be queued when updating Elastic.
   * 50 by default. This should be fine in most situations.
   * Reducing this will reduce the memory used but may impact the time taken to complete.
4. **Scroll Windows:** Enter many minutes the scroll windows is kept in memory for.
   * 15m by default. This should be fine in most situations.
5. **Scroll Size:** Enter the number of items to retrieve per scroll request.
   * 100 by default. This should be fine in most situations.
6. **Queue Rate:** Enter the maximum number of items that can be queued per-minute.
   * 0 by default. This should be fine in most situations.
   * 0 is unlimited items, it allows the pipeline to calculate.&#x20;
7. **Rest Window:** Enter how long to wait before checking for a new query, in minutes.
   * 1m by default. This should be fine in most situations.
8. **Log File Events:** Check this to index file events.
   * Disabling this prevents the pipeline from logging events for the enrichment stats page.&#x20;
9. **Clear Text Content on Enrichment Failure?:** If checked, when enrichment fails the text content of a file will be removed but the item will remain.

<figure><img src="../../../../../.gitbook/assets/image (786).png" alt="" width="563"><figcaption></figcaption></figure>

### Batch Processing

1. **Enable Batched Updates:** Check this to index enrichment results for this pipeline in batches instead of as they complete.
2. **Update Batch Size:** Enter the number of enrichment results to write into Elastic per batch.&#x20;
   * This setting is applied on a per-source basis.
3. **Maximum Update Batch Age:** Enter the maximum time between batches in minutes.
   * If a batch starts and the maximum size isn't reached within this time it will be batched as is. This will stop batches building up and being delayed.&#x20;

<figure><img src="../../../../../.gitbook/assets/image (789).png" alt="" width="563"><figcaption></figcaption></figure>

### Common Error Handling

If you are regularly getting errors or a large number of errors in enrichment the following settings may help.&#x20;

1. **Enable Circuit Breaker:** Check this to stop the pipeline processing if an error occurs.
2. **File Exceptions Trigger Circuit Breaker:** Check this to stop the pipeline processing if file and indexing exceptions occur.
3. **Error Threshold:** Enter the maximum times a single error type can occur before the pipeline is stopped.
4. **Time Period:** Enter the amount of time to track for duplicate errors, in seconds.

<figure><img src="../../../../../.gitbook/assets/image (787).png" alt="" width="563"><figcaption></figcaption></figure>
