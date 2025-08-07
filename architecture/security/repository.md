# Repository

### Elasticsearch security

* XPack is mandatory, all traffic will be encrypted and password protected.
* Each Elasticsearch server needs to communicate with each other and the firewall ports need to be open.   Default transport port: **9300**
* Kibana needs to communicate with the Elasticsearch nodes that are processing Kibana requests.
* The agents and web server (gateway) need access to the Elasticsearch servers as described in the firewall section. Default port: **9200**

[Review the full Elasticsearch comprehensive security guide](https://www.elastic.co/what-is/elastic-stack-security).
