# Model Steps

Model steps allow you to abstract one or more Generative AI model. You can match different size and cost models to your different use cases.

## **Step Details**

1. Select New Model Setp.
2. **Step Name** - Enter a name for this step.
3. **AI Model Service** - Select the model service this is running the generative provider.
4. **AI Model Provider** - Select the provider you want to use.&#x20;
   * This will only show generative providers.
5. **AI Model Credential ID** - (Optional) Select the credential to use to authenticate against the model provider.
6. **Max Characters to Send** -  Enter the maximum number of characters that can be sent to the model at once.
   * As a guide, 4 characters is a approximately 1 token for most models.
   * For public facing installations this should be the maximum size of the context you want to send to a model.&#x20;
   * If this is set to 0, it will not be enforced.
7. **Tools** - Select the tools that will be sent to the model as part of this step.
   * [See our guides about tools for more information on tools are and what you can use them for.](../tools/)

<figure><img src="../../../.gitbook/assets/image (17).png" alt="" width="563"><figcaption></figcaption></figure>

## Model Parameters

1. **Model** - Select the model to use.
2. **Max New Tokens** - Enter the maximum number of tokens to generate.

{% hint style="warning" %}
For some cloud models the number of tokens you request will count towards your throttled limit not the number generated.
{% endhint %}

3. **Temperature** - Enter a decimal value between 0 and 1 to determine how the model will respond.
   * Temperature is a parameter that influences the language model's output. It determines whether the output is more creative or predictable.
   * A value closer to 0 will produce more predictable and less creative outputs.
4. **Streaming** - Choose if the response is returned to the user as it is generated (true) or once it is finished (false).
   * For user interactive chatbots this should be true.&#x20;
   * If you are using the API for background agent tasks then you can set this to false.
5. **Last Prompt Template** - Enter a template that can be used for the last prompt sent to the model.&#x20;
   * This can help re-anchor model responses. For example:
     * "{prompt} always respond using the provided results, and use the correct tool calling parameters." The users prompt is placed in the {prompt} placeholder.

<figure><img src="../../../.gitbook/assets/image (18).png" alt="" width="563"><figcaption></figcaption></figure>
