# Overview and Key Concepts

Aiimi Insight Engine is an information management platform that brings unstructured and structured information together. It offers users a fundamentally different way to consume information. Leveraging links between, recommendations, machine learning, user personas and other next generation capabilities.&#x20;

## Aiimi Insight Engine's Key Concepts:

### Source Connectors&#x20;

Connect to source systems that have documents or data that need indexing into Aiimi Insight Engine. They provide the initial load and the deltas (new, updated and deleted items). There are many out of the box connectors, but we are always updating these and adding new ones.&#x20;

> All source connectors follow the same pattern and are underpinned by a framework. This enables Aiimi, our customers and our partners to quickly create new connections.&#x20;

### Enrichment

Add context to the items Aiimi Insight Engine discovers using the enrichment pipeline. Most are labels that are applied to items used to present more meaningful information to your users. Enrichment can add classifications, geotags, named entities and other such things to items.&#x20;

> Like source connectors, they are extensible and underpinned by a framework. This makes it easy for both Aiimi, our customers and partners to create enrichment steps. Enrichment steps are generally written in .NET or Python, but can be any language and interfaced using the REST enrichment step.

### AI Enrichment

Use artificial intelligence and machine learning to enrich your data and documents. Steps include things like vectorisation for semantic search, large language model classification, extractive NLP models, and generative AI.

### Repository

The repository is where Aiimi Insight Engine stores the items it discovers and enriches. Along with the items it stores the configurations, permissions and other information. The repository is based on Elasticsearch which provides excellent scaling and performance for massive enterprise data sets.

### Gateway & API

The gateway hosts a series of REST APIs used to access data and documents stored within the repository. It's also responsible for authenticating users and authorising what they can see.&#x20;

> The APIs are used by our own apps, but can also be used by our customers and partners to create their own apps and integrations.

### AI Model Service

The AI Model Service provides a series of services that support search time vectorisation for semantic search, query ad prompt classification so the right models can be selected, and the engagement of extractive and generative AI.

### User Interface&#x20;

The user interface is a collection of apps used to access the information within Aiimi Insight Engine. The apps are HTML5/CSS/JavaScript but, can be anything that can communicates with the Gateway using HTTPS and REST.
