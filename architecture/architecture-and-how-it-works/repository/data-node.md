# Data Node

A data node holds part of the indexed content. Data (or indexes) are split into shards which are then distributed across the data nodes.&#x20;

The whole replication and distribution process is managed by Elasticsearch. Data nodes tend to have good amounts of CPU, memory and underlying disk space. This would be fast access SSD disks ideally.

Large production systems commonly have servers with 8+ CPUS, 32GB-64GB of RAM and enough disks for the underlying indexes.

### Recommendation

We recommend you allocate half the memory to Elasticsearch and the remaining to the operating systems disk cache. This memory balance is key to Elasticsearch performance.

* For Aiimi Insight Engine it is common to see performance improve when more memory is given to the operating system.
