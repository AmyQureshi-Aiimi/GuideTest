# Performance and Concurrency

Some enrichment steps are used for advanced machine learning and are CPU and memory intensive.

You can configure the concurrency on the AI enrichment step within your pipeline so it doesn't send too many requests at once. If you don't do this, you will get timeout errors and the items will be marked as ‘error’.

### Configuring Concurrency

1. Within the AI Enrichment Step select Show Advanced Options.&#x20;
2. Max Degree of Parallelism: Add a value.
   * We recommend you perform some empirical testing to establish the best value for this.
