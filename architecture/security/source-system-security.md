# Source System Security

Most source systems require credentials for access. An exception to this would be ingesting public web content.&#x20;

Credentials govern the access type Workplace AI has to a source system. Credentials also govern what Workplace AI is able to see. On a filesystem this controls what folders and files Workplace AI has access to.

{% hint style="info" %}
Workplace AI requires at least read-only access to any area of a source system that you want to ingest.
{% endhint %}

## Defence in Depth

This is a strategy that uses multiple security measures to protect your organisation and its assets.&#x20;

* Example: The credentials for Workplace AI have read-only permission for Specific Items in a source. Any upstream compromise would not be able to remove content from the source system.

{% hint style="warning" %}
While Workplace AI is secure, the principal of least privileges should always be applied. This defence approach makes it impossible for malicious attack vectors to remove or corrupt anything.
{% endhint %}

## Encryption and audit

* Workplace AI stores encrypted credentials all managed in the Control Hub. This simplifies administration and improves security.
* Source system auditing can inspect what Workplace AI is doing during the discovery and enrichment process.
