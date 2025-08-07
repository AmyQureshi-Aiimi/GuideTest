# Kibana Node

The Kibana node hosts the Kibana user interface, it manifests itself as a servers-side NodeJS application.&#x20;

Kibana is locked down in production and is only used by administrators of the platform.

### Recommendations

We usually host Kibana on a proxy node but in a highly concurrent environment it may need its own dedicated node.

