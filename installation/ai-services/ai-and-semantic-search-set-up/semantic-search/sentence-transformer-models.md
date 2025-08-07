# Sentence Transformer Models

You need to enable the Huggingface sentence transformers for the AIEnrichmentService and the AIModelService.

* The AI enrichment service uses the transformer at enrichment. It converts a documents textContent into vectors.
* The AI model service uses the transformer at search time. It converts a search query into vectors.

_For support making these changes_ [see our guide on enabling providers.](https://docs.aiimi.com/aiimi-insight-engine/installation/ai-services/ai-model-service/enabling-providers)

## **Using a GPU**

If you are able to use a GPU we recommend using it for the AIEnrichment service.

There are two pre requisites for using a GPU with your sentence transformers.

1. The GPU is installed and set up.
   * _For support setting this up_ [see step 2 of our AI Model Service install requirements.](https://docs.aiimi.com/aiimi-insight-engine/installation/ai-services/ai-model-service/installation-and-setup#install-requirements)
2. Within the ai.json, under the AIEnrichment Service model change the device to cuda:0.
   * _For support making these changes_ [see our guide on enabling providers](https://docs.aiimi.com/aiimi-insight-engine/installation/ai-services/ai-model-service/enabling-providers).

<figure><img src="../../../../.gitbook/assets/image (110).png" alt="" width="563"><figcaption></figcaption></figure>
