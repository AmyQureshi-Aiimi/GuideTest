# Firewalling

If a firewall is in place the necessary ports need to be open for Workplace AI. Specific port numbers are detailed in the relevant Agent Server sections.

**Gateway server** - Needs to communicate with every agent server.

* Respective agent services that are running on the server.

**Gateway and the agent servers** - Needs to communicate with the Elasticsearch repository.

* You can provide an array of server addresses to configure a set of Elasticsearch servers.
* Ports for each Elasticsearch server used will need to be open.

**Agent servers** - Needs to communicate with each source system.&#x20;

* The exact port requirements depend on the source system. This information is usually found in your source systems API documentation.

**Kibana** - Needs access to Elasticsearch.

* Open the array of ports you plan to use for Kibana access.

**Users** - Needs access to the Aiimi Insight Maker Apps.

* Open the port that the web server is using to host the gateway and apps.
