# AI Model Service

This details the AI Model Service and the providers that are included with Aiimi Insight Engine. These providers support users performing semantic search, and engaging with large language models (Generative AI).

The following providers are included:

* **Azure Open AI Generative** - This provides access to Azure Open AI models, including GPT 3.5 and GPT 4. You can easily add new models as they are released by Open AI.
* **Huggingface Classifier** - This is used by the user interface to classify a user prompt (query) and the user record. A 'label' is returned which is then used by the UI to select the right type of search to perform, and which optional model to run over the results.
* **Huggingface Extractive** - This provider hosts a series of extractive models. These are used to take an object in AIE and then extract a fact for a given prompt.
* **Huggingface Generative** - This provides access to Huggingface generative models such as Llama2  and Llama3. These can be run on your own private virtual machines.
* **Huggingface Generative LlamaCpp** - This provider allows you to run GGUF format models. These can often be found on Huggingface. GGUF format models are often quantised and therefore can run using less memory. You can also balance the model across GPU VRAM and conventional memory.
* **Huggingface Sentence Transformers** - Sentence Tranformers underpin dense vector sematic search. This provider is used by the search API to vectorise user queries.
* **Huggingface Sparse Vector** - Sparse vectors underpin sparse vector sematic search. This provider is used by the search API to vectorise user queries.
* **Risk Scanner** - This provider is used to svan generative output for sentiment and toxicity.
