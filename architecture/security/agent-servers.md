# Agent Servers

Each Workplace AI agent runs as a Windows or Linux service. They listen and communicate with gateways using ports. They also locally write logs and can generate local temporary data.

### Specific communications:

* Source Agent - Content Agent
* Enrichment Agent - Content Agent
* Migration Agent - Content Agent
* Migration - Source Agent
* Enrichment Agent - OCR Agent
* Enrichment Agent - Tika Agent
* Job Agent - All agents or Job dependent

<details>

<summary>Security Agent</summary>

### Elasticsearch Connection

The security agent requires network access to the Elasticsearch cluster as outlined in the firewalling guide. Default port: **9200**

[Read more about Workplace AI Firewalling.](firewalling.md)

### Azure Directory Connection

The security agent requires network access to the Active Directory you are synching users and groups from. Default port: **2222**

{% hint style="info" %}
If you use other security repositories such as Azure AD or OpenText Content Server, these ports need to be accessible to the security agent.
{% endhint %}

### Security Specifics

By default, the windows service will run as the local system account. You should not need to change this. The account needs:

* Read access to the installation folder for Workplace AI.
* Write access to the logs folder.
* Read access to the security certificates used to secure communications with Elasticsearch.

</details>

<details>

<summary>Source Agent</summary>

### Elasticsearch Connection

The source agent requires network access to the Elasticsearch cluster as outlined in the firewalling guide. Default port: **9200**

[Read more about Workplace AI Firewalling.](firewalling.md)

### Source System Connection

The source agent requires network access to all source systems. Default port: **2221**

### Security specifics

By default, the windows service will run as the local system account. You should not need to change this. The account needs:

* Read access to the installation folder for Workplace AI.
* Write access to the logs folder.
* Read access to the security certificates used to secure communications with Elasticsearch.

</details>

<details>

<summary>Content Agent</summary>

### Elasticsearch Connection

The content agent requires network access to the Elasticsearch cluster as outlined in the firewalling guide. Default port: **9200**

[Read more about Workplace AI Firewalling.](firewalling.md)

### Content Agent Connection

Default port: **2225**

### Security specifics

By default, the windows service will run as the local system account. You should not need to change this. The account needs:

* Read access to the installation folder for Workplace AI.
* Write access to the logs folder.
* Read access to the security certificates used to secure communications with Elasticsearch.
* Write access to the folder used to cache the thumbnails (configured in the control hub).

</details>

<details>

<summary>Enrichment Agent</summary>

### Elasticsearch Connection

The enrichment agent requires network access to the Elasticsearch cluster as outlined in the firewalling guide. Default port: **9200**

[Read more about Workplace AI Firewalling.](firewalling.md)

### Tika Agent Connection

The enrichment agent needs network access to the Tika Agent. Default port: **9998**\
**T**his service usually runs on the same server as the enrichment agent.

### Enrichment Agent Port

Default port: **2223**

### Security specifics

By default, the windows service will run as the local system account. You should not need to change this. The account needs:

* Read access to the installation folder for Workplace AI.
* Write access to the logs folder.
* Read access to the security certificates used to secure communications with Elasticsearch.

</details>

<details>

<summary>Job Agent</summary>

### Elasticsearch Connection

The job agent requires network access to the Elasticsearch cluster as outlined in the firewalling guide. Default port: **9200**

[Read more about Workplace AI Firewalling.](firewalling.md)

### Job Agent Port

Default port: **2220**

### Security specifics

By default, the windows service will run as the local system account. You should not need to change this. The account needs:

* Read access to the installation folder for Workplace AI.
* Write access to the logs folder.
* Read access to the security certificates used to secure communications with Elasticsearch.

</details>

<details>

<summary>OCR Agent</summary>

### Elasticsearch Connection

The OCR agent requires network access to the Elasticsearch cluster as outlined in the firewalling guide. Default port: **9200**

[Read more about Workplace AI Firewalling.](firewalling.md)

### OCR Agent Port

Default port: **2224**

### Security specifics

By default, the windows service will run as the local system account. You should not need to change this. The account needs:

* Read access to the installation folder for Workplace AI.
* Write access to the logs folder.
* Read access to the security certificates used to secure communications with Elasticsearch.

</details>

<details>

<summary>Migration Agent</summary>

### Elasticsearch Connection

The migration agent requires network access to the Elasticsearch cluster as outlined in the firewalling guide. Default port: **9200**

[Read more about Workplace AI Firewalling.](firewalling.md)

### Migration Agent Port

Default port: **2226**

### Security specifics

By default, the windows service will run as the local system account. You should not need to change this. The account needs:

* Read access to the installation folder for Workplace AI.
* Write access to the logs folder.
* Read access to the security certificates used to secure communications with Elasticsearch.

</details>

<details>

<summary>Tika Agent</summary>

The Tika agent requires no outbound network access to other services, it services inbound requests only.

### Tika Agent Port

Default port: **9998**

### Security specifics

By default, the windows service will run as the local system account. You should not need to change this. The account needs:

* Read access to the installation folder for Workplace AI.

</details>
