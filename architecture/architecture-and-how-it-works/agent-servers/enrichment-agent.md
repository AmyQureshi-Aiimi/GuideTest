# Enrichment Agent

The enrichment agent sits at the heart of Aiimi Insight Engine, it enriches data and documents with additional context. This information is stored against the item as a series of labels and data structures. These help structure information, drive recommendations, push insights, and support data science activities.

### Enrichment Steps

The enrichment agent is like a pipeline, it is a container for a series of enrichment steps. Each step is responsible for enriching the item being passed through. Example Steps include classification, named entity recognition, adding geotags and many more.

You can choose the steps to implement and configure them within the the Control Hub. [View our guide to configuring an Enrichment step.](../../../control-hub/agents/configurations/enrichment-configurations/)

> Aiimi, our customers and partners can create a framework to meet their needs.
>
> * A Microsoft.NET framework can be used to implement a pipeline step.
> * You can use the REST step to call out to any REST/JSON based service.

### REST Enrichment Approach

Aiimi uses the REST approach for a series of Python based machine learning steps. For example, Document classification, phrase and topic extraction, statistical named entity recognition, document summarisation and sentiment analysis.  \
These are in the Python REST Service shipped with Aiimi Insight Engine.

Enrichment can be demanding on CPU and Memory depending on the steps in your pipeline. Enterprise production platforms commonly have more than one server for crawling and enrichment. The exact number will depend on your volumetric.&#x20;

> If you are unsure what is best for your organisation your contact at Aiimi will be able to help.

<figure><img src="../../../.gitbook/assets/image (573).png" alt=""><figcaption></figcaption></figure>

