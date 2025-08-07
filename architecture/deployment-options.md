# Deployment Options

The section looks at the various deployment options that you have for Workplace AI. These are guides and are not representative of what your deployment will look like.&#x20;

<details>

<summary>Development Environments</summary>

For a development environment we recommend a single server set up. This should contain all the Workplace AI components.&#x20;

#### Single Server Requirement&#x20;

A laptop with the following requirements is ample for a single server installation of Workplace AI.

* 4 CPU Cores
* 16GB RAM
* 250GB Disk Space

You should be able to ingest a few hundred thousand documents and continue development and testing activities.

#### Two Server Set Up

Developers may set the whole platform up on a laptop or workstation computer using the below split.

* One server should host the repository.
* One server should host the agents and the gateway.&#x20;

</details>

<details>

<summary>Testing and QA Environments</summary>

The key decision about your QA environment is driven do you want to do performance testing. If you do, how much should it match the production environment in terms of scale.

### End-user performance testing of ‘search’ related transactions

* The elastic cluster and web server should be scaled as production.
* The QA system should contain the same volume of content.
* If you have not scaled the QA platform to match production, you can extrapolate some estimations for performance. Please note this is not an exact science, and the only true test is to have the QA platform sized the same as production.

### Strict pre-production testing environments:

* If production has a separate web server and agent servers so should QA.
* If production has multiple agent servers, QA should have at least 2 agent servers.
* If production has separate proxy nodes on the elastic cluster so should QA.
* If production uses a multi node elastic cluster than QA should.

### Performance Testing

For performance testing your Aiimi contact can provide separate guidelines.

* The most significant process for end user response times is search and aggregation requests.&#x20;
  * For performance, test the Elasticsearch cluster and the web servers being scaled.&#x20;
* If you want to test ingestion throughput ensure the Elasticsearch cluster and Agent servers are scaled.





</details>

<details>

<summary>Production Environments</summary>

Production environments need to be designed and scaled with your specific requirements.

Below are small, medium, and large sizing guides for each type of server. This can help as a starting point when designing your platform.&#x20;

{% code overflow="wrap" %}
```
For a medium or large platform you will have multiple servers for the agent and repository tiers.
```
{% endcode %}

#### Scaling Agent Servers

* Small – 4 CPU cores, 16GB RAM, 100GB local disk
* Medium – 8 CPU cores, 32GB RAM, 100GB local disk
* Large – 16 CPU cores, 64GB RAM, 100GB local disk

#### Scaling Repository Servers

* Small – 8 CPU cores, 16GB RAM, 200GB SSD local disk
* Medium – 16 CPU cores, 32GB RAM, 400GB SSD local disk
* Large – 32 CPU cores, 64GB RAM, 800GB SSD local disk
  * Proxy servers do not need the same amount of memory and local disk since they store no data. For this 16GB RAM will be sufficient and the CPU loading will increase with transactional concurrency.

#### Scaling Web Servers

* Small – 4 CPU cores, 16GB RAM, 100GB local disk
* Medium – 8 CPU cores, 32GB RAM, 100GB local disk
* Large – 16 CPU cores, 32GB RAM, 100GB local disk

### Production Platform Considerations

* Separate agent and web servers should be used.
* The number of agent servers required depends on:
  1. The number of source repositories
  2. Their respective size
  3. Pipeline complexity
  4. Content Ingestion rate
* In most scenarios only a single web server will be required.
  * If you use two you will need to load balance the user requests using a standard load balancer.
    * Load balancing should be ‘sticky’ – i.e. send the same users requests to the same web server
* If OCR is heavily used, then this should have it's own agent server.
* Separate proxy nodes in the repository tier.
* Multiple elastic servers and limit the maximum amount of memory per-node to 64GB.

</details>

<details>

<summary>Disaster Recovery Environments</summary>

Disaster recovery environments need to consider the service needed during a ‘disaster scenario’.

The business criticality of the system can be scaled accordingly. If you need the same level of users and ingestion rates, the recovery platform should replicate the production environment.

</details>
