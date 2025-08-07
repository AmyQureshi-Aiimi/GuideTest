# Vectors for Semantic Search

You will need to create a vector for the sentence transformers that allow semantic searches. There are a few specific requirements but otherwise it's like setting up any other vector.

_For support creating a vector_ [see our guide on creating a new vector.](https://docs.aiimi.com/aiimi-insight-engine/control-hub/mappings/vectors)

## **New vector**

There are couple of specific requirements depending on the transformer you are using.

### All-mpnet-base-v2 - 768 Dimensions

1. **Type:** Dense Vector
2. **Element Type:** Select Float from the dropdown list.
3. **Dimensions:** 768
4. **Similarity Metric:** Select dot\_product from the dropdown list.
5. **Count:** 10
6. **Index:** This must be enabled.

<figure><img src="../../../../.gitbook/assets/image (860).png" alt="" width="563"><figcaption></figcaption></figure>

### Multi-qa-mpnet-base-dot-v1 - 768 Dimensions

1. **Type:** Dense Vector
2. **Element Type:** Select Float from the dropdown list.
3. **Dimensions:** 768
4. **Similarity Metric:** Select dot\_product from the dropdown list.
5. **Count:** 10
6. **Index:** This must be enabled.

<figure><img src="../../../../.gitbook/assets/image (861).png" alt="" width="563"><figcaption></figcaption></figure>

