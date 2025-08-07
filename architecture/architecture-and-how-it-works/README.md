# Architecture and How It Works

Workplace AI is made up of services that do ‘backend processing’, a repository and a set of web apps for access.&#x20;

## Requirements

The Workplace AI agents and web apps run on Microsoft Windows or Linux operating systems.&#x20;

* This can be a server or desktop version providing it can run a web server such as Internet Information Server of Apache.&#x20;

A desktop version such as Windows 10 should only be used for demo or development environments.

The repository, Elasticsearch, can run on Windows or Linux.&#x20;

* Java is required to run Elasticsearch. The 7 generation of Elasticsearch is packaged with a suitable JVM for the software.
  * You can use an external version but, new licencing models apply to Oracle Java versions.

The Elasticsearch tool Kibana is useful for admins to inspect indexes and perform ad-hoc reporting. On production platforms access to this would be locked down.

***

## High Level Architecture

### **Agent Servers**

<table data-view="cards"><thead><tr><th></th><th></th></tr></thead><tbody><tr><td><strong>Security Agent</strong></td><td>Responsible for synchronising users and groups from the credential stores. It is also responsible for servicing authentication requests.</td></tr><tr><td><strong>Source Agent</strong></td><td>Connects to source systems to discover new, modified and deleted data and documents. It also fetches data and documents for enrichment and when users want to preview a document.</td></tr><tr><td><strong>Content Agent</strong></td><td>A support service for the Source Agent. It handles thumbnails, caching, proxying document &#x26; data fetch and preview requests.</td></tr><tr><td><strong>Enrichment Agent</strong></td><td>Runs enrichment on data and documents stored within Workplace AI. It runs the configured pipelines, each containing one or more enrichment steps. For example, document classification, NER or image recognition.</td></tr><tr><td><strong>Job Agent</strong></td><td>Runs maintenance and other jobs that the platform requires to be run. For example index backup, recommendations, and notifications. It may also run customer specific scripts.</td></tr><tr><td><strong>OCR Agent</strong></td><td>Responsible for running one or more OCR engines. Out of the box IronOCR is provided, but plugging in other engines such as ABBY Reader is supported.</td></tr><tr><td><strong>Migration Agent</strong></td><td>Runs migration jobs which move documents and data between systems.</td></tr><tr><td><strong>Tika Agent</strong></td><td>Converts documents from their native format to plain indexable text. This is used by the enrichment agent (Tika Text Conversion Step).</td></tr></tbody></table>

### **Repository Servers**

* One or more Elasticsearch nodes.
* One or more Elasticsearch proxy nodes.
* One Kibana node (usually shared with a proxy node).

### **Web Servers**

* One or more servers running the APIs and the end user apps.

#### Example Architecture

<figure><img src="../../.gitbook/assets/image (469).png" alt=""><figcaption><p>This schematic illustrates an example architecture for Workplace AI.</p></figcaption></figure>
