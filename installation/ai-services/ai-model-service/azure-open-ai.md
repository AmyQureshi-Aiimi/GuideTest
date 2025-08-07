# Azure Open AI

## Using Azure Open AI

1. Provision an endpoint in Azure, and the models you want to use.
2. Export and edit the provider, changing the URL as required.
3. Create a new secret only credential within Control Hub.
   * _For support setting up a secret only credential_ see [our guide on creating secret only credentials.](https://docs.aiimi.com/aiimi-insight-engine/control-hub/credentials/create-a-credential)
4. Update the provider with that correct path.

***

## Troubleshooting

Sometimes the Tiktoken's tonkenizer is unable to resolve which causes an error on every call. "_<mark style="color:orange;">Failed to resolve 'openaipublic.blob.core.wi</mark>_[_<mark style="color:orange;">ndows.net' (\[Errno 11001\] getaddrinfo failed)"))</mark>_](#user-content-fn-1)[^1]_"._ This is caused by networking rules in certain environments.

The following steps resolve the issue by removing the need for the above call to occur in the first place.

1. Create a new folder named tiktoken\_cache in any location.
   * E.g. C:\tiktoken\_cache. We recommend having this outside of any InsightMaker folders.
2. Set an environment variable called TIKTOKEN\_CACHE\_DIR that points to the folder you created.
   1. Search "Edit the system environment variables on windows.
   2. Select Environment Variables...
   3. Within System Variables select New.
   4. Variable Name: Enter TIKTOKEN\_CACHE\_DIR
   5. Variable Value: Enter the path to the folder you created.
   6. Select Ok and Exit.
3. Download the tiktoken tokenizer. The tokenizer you need depends on the model you are running:
   * GPT 3.5 or 4: [https://openaipublic.blob.core.windows.net/encodings/cl100k\_base.tiktoken](https://openaipublic.blob.core.windows.net/encodings/cl100k_base.tiktoken)
   * GPT 4o or 4o-mini: [https://openaipublic.blob.core.windows.net/encodings/o200k\_base.tiktoken](https://openaipublic.blob.core.windows.net/encodings/o200k_base.tiktoken)

{% hint style="info" %}
If you are can't download it from these links please try on an unrestricted network or hotspot.
{% endhint %}

4. Once downloaded, rename the tokenizer file:
   * _From_ **cl100k\_base.tiktoken** _to_ **9b5ad71b2ce5302211f9c61530b329a4922fc6a4**
   * _From_ **o200k\_base.tiktoken** _to_ **fb374d419588a4632f3f557e76b4b70aebbca790**
     * These do not need an extension.
5. Move the downloaded and renamed item to the folder created in step 1.

[^1]: 
