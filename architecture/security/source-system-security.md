# Source System Security

Most source systems require credentials for access. An exception to this would be ingesting public web content.&#x20;

Credentials govern the access type Aiimi Insight Engine has to a source system. Credentials also govern what Aiimi Insight Engine is able to see. On a filesystem this controls what folders and files Aiimi Insight Engine has access to.

{% hint style="info" %}
Aiimi Insight Engine requires at least read-only access to any area of a source system that you want to ingest.
{% endhint %}

## Defence in Depth

This is a strategy that uses multiple security measures to protect your organisation and its assets.&#x20;

* Example: The credentials for Aiimi Insight Engine have read-only permission for Specific Items in a source. Any upstream compromise would not be able to remove content from the source system.

{% hint style="warning" %}
While Aiimi Insight Engine is secure, the principal of least privileges should always be applied. This defence approach makes it impossible for malicious attack vectors to remove or corrupt anything.
{% endhint %}

## Encryption and audit

* Aiimi Insight Engine stores encrypted credentials all managed in the Control Hub. This simplifies administration and improves security.
* Source system auditing can inspect what Aiimi Insight Engine is doing during the discovery and enrichment process.
