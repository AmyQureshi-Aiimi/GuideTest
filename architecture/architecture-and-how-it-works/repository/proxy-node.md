# Proxy Node

A proxy node gets all the API requests to access data from Workplace AI agents and the gateway API. It then coordinates the execution of the request across the data nodes.

### Requirements

Proxy nodes don't have the same disk and memory requirements as data nodes. They do not store any data locally, other than some cache requirements. In an environment with parallel processes they need enough CPU to keep up with requests.

If you have more than one proxy node, you could have one load balance, one for the gateway and another for the agents.

### Proxy Alternatives

You can configure your platform without proxy nodes by distributing requests to available data nodes. You must consider how this might balance with ingestion, the consequence for user requests and ingestion requests.&#x20;

> Your Aiimi contact can provide more advice if you do not want to use a proxy node.
