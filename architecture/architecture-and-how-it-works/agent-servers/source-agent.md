# Source Agent

The source agent is built around the concept of a source plugin. This provides the implementation for a back-end data or document store such as SharePoint, Network File Shares or SAP.

The source agent has two main services:

1. To crawl and discover content in data and document systems (Source Systems).
2. To fetch data and documents from systems for enrichment and end-user functions.

> Aiimi has a number of source plugins and are constantly adding new ones. Aiimi, our customers and partners can write source plugins using the Microsoft.NET framework.

### Bulk Load

Source agents can bulk load information from back-end systems, perform deltas and store a current crawl state. Because of this, a Crawl can be suspended and restarted later to pick up from where it left off.

### Metadata

Source agents pull out metadata like name, location, created and modified date for discovered items. It also pulls the access control list for every item. This list is used to control who can access what data and documents in Workplace AI.

### Source System Settings

Source configurations consist of source system specific and common settings. These run on a schedule which is configured by an Admin within the Control Hub.

Source agents are not CPU or memory intensive, they only require disk space for logging. Bandwidth and network latency will impact how fast a crawl is. Ideally, on a network, source agents are located near the data sources with low latency.

### Source and Enrichment Agents

It is common for Source agents to share a server with enrichment and other supporting agents.&#x20;

Your source and enrichment agents work in pairs. For example, the source agent finds content and the enrichment agent performs its tasks.&#x20;

[See the specific configuration options in the deployment option guide.](../../deployment-options.md#production-environments)



<figure><img src="../../../.gitbook/assets/image (632).png" alt=""><figcaption></figcaption></figure>
