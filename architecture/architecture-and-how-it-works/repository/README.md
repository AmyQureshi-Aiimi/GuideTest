# Repository

Aiimi Insight Engine currently only supports Elasticsearch for the reposistory. This is a schema-less, scalable, JSON based search and analytics engine. Elasticsearch scales well and with excellent resilience with its clustering and replication capabilities.There are many online resources available that detail all aspects of Elasticsearch. [https://www.elastic.co/](https://www.elastic.co/)

### Key Points For Aiimi Insight Engine:

1. Elasticsearch requires a Java Virtual Machine (JVM) on the operating system.&#x20;
   * Elasticsearch now ships with a JVM so there is no need to install an external one, although you can do if you wish.
2. It requires the security within Elasticsearch to be operational.
   * All communications are over SSL, usernames and passwords are required to gain access.
3. XPack licensing is a prerequisite.&#x20;
   * It provides additional capabilities including, 3rd line support for your Elasticsearch cluster.
     * Depending on how you procured Aiimi Insight Engine, a licence may be included in your subscription. Your Account Executive or Services representative will be able to clarify this.
4. For a production environment you will have a multi-node cluster running data and proxy nodes.
   * This will be discussed further in Deployment Options.
5. Elasticsearch supports both a Microsoft Windows and Linux based operating systems. Aiimi does not have a preference.
6. We recommend installing the user interface Kibana. It allows administrators access to the underlying indexes and various reporting tools.&#x20;
   * This should be locked down to key users.

Kibana provides a series of capability including cluster monitoring. This is a very useful tool for administrators of large clusters.

<figure><img src="../../../.gitbook/assets/image (604).png" alt=""><figcaption></figcaption></figure>

