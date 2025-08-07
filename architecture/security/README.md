# Security

Aiimi Insight Engine supports a host of security options that allow you to secure your deployment. It can be secured at the application and the infrastructure level.

## Concepts:

### XPack

An Elasticsearch module that secures Elasticsearch transport and HTTP protocol using SSL. This ensures all traffic to and from the cluster is encrypted. It also enforces the need for a username and password on all requests, which are also encrypted.

### Source System Credentials

The credentials used to discover and ingest content from the source systems. They act as a layer of security that controls what Aiimi Insight Engine can do. For example, a read-only account means Aiimi Insight Engine cannot make any changes to an item or write back.

### HTTPS

A secure form of HTTP used to communicate between the agents, web server, Elasticsearch and between users and the gateway.

### Authentication

All users and admins accessing the system must login in with valid credentials before accessing the apps.

### Authorisation

All user requests go through a series of authorisation steps. These govern what apps and items a user has access to.

### Permissions Trimming

This controls what users can and cannot see when using Aiimi Insight Engine to search or anything else. These controls are mainly taken from the source system but further restrictions can be applied within Aiimi Insight Engine.
