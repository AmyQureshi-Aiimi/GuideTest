# Vectors

Vectors are used to enable semantic search within Workplace AI. \
Items within your system are vectorised during a Python Rest Enrichment Step and grouped together based on the vectors created in mappings.&#x20;

{% hint style="info" %}
A Vector must be created before the Python Rest enrichment step.
{% endhint %}

## Create a New Vector

{% hint style="warning" %}
Vectors cannot be deleted from the Control Hub. If a vector needs removing speak to your Elastic administrator.
{% endhint %}

1. Within the Control Hub go to Mappings > Vectors.
2. Select Create New Vector.
3. **ID** - Enter a unique ID for this vector.
   * This must be in camel case and only contain alphanumeric characters and underscores.
   * The Vector ID must match the enrichment steps Model ID.
4. **Vector Name** - Enter a user friendly name for this vector.
5. **Description** - Give the vector a description to explain what it is for within Description.
6. **Type** - At the moment we are only able to support Dense Vector types.
7. **Element Type** - Select the structure of your vectors from the dropdown.
   * Choose between Float or Byte.
8. **Dimensions** - Enter the number of Dimensions to compare for similarity.
   * Indexed vector dimensions must be less than 1024.
   * Non-Indexed vector dimensions must be less than 2048.
9. **Similarity Metric** - Select a metric to use to compare your vectors from the dropdown.
10. **Count** - Enter the number of vectors to create.
11. **Index?** - Check this to allow this field to be searched using the kNN search API.
12. Select Create Vector to finalise.&#x20;

<figure><img src="../../.gitbook/assets/image (759).png" alt="" width="563"><figcaption></figcaption></figure>
