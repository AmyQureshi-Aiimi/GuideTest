# Query and Prompt Classification

Search Flows allow you to classify queries and prompts from users. You can then use this to select the right search algorithm or AI model to use.

Aiimi Insight Engine provides a few classification models out of the box, such as 'Is A Question'. However, you can add custom models.

Classification models return a value or a label that contains the 'classification'. For example, 'Is A Question' will return 'true' or 'false' and uses this to select the right algorithm or model.

Classification is optional and search step selection defaults to the first defined search step if not used.

<figure><img src="../../../.gitbook/assets/image (47).png" alt="" width="563"><figcaption><p>Query Classification</p></figcaption></figure>

## Configuration

* Enabled - Whether the query classifcation step is enabled.
* AI Model Service - The model service that is running the classification provider.
* AI Model Provider - The provider to use. You will only shown classification providers.
* Model - The model to use. Note that you will need to marry up the labels that the model returns and use these as the IDs of your search steps.
