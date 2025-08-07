# AI Model Server API Wrapper

The AI Model Server Wrapper provides a convenient approach in python to use generative AI, extractive AI, sentence transformers and document splitting, hosted by the Workplace AI AI Model Service.&#x20;

## Initialisation&#x20;

On initialisation of a ModelServer object, details required for connection to the Workplace AI Model Server are provided.

<table><thead><tr><th width="164.550537109375">Name</th><th width="120.3558349609375">Type</th><th>Description</th></tr></thead><tbody><tr><td>host </td><td>string </td><td>Host URI, if hosting the Model Server locally, you can typically use “http://localhost:15008/” </td></tr><tr><td>https </td><td>boolean </td><td>Optional, flag for if using HTTPS (default false) </td></tr><tr><td>verify </td><td>boolean </td><td>Flag to verify HTTPS requests, defaults to True </td></tr><tr><td>system_secret </td><td>string </td><td>Workplace AI system secret for verification. Default value, “insightmaker” </td></tr><tr><td>ssl_context </td><td>SSLContext </td><td>Optionally, provide a python SSLContext object for SSL enabled model servers </td></tr><tr><td>encoding </td><td>string </td><td>String to use for decoding the generative stream, default “utf-8”, unlikely to require changing </td></tr></tbody></table>

#### Example&#x20;

{% code overflow="wrap" lineNumbers="true" %}
```python
from aiimi_insight_engine.model_server import ModelServer 
model_server = ModelServer("http://localhost:15008/") 
```
{% endcode %}

#### SSL Example&#x20;

{% code overflow="wrap" lineNumbers="true" %}
```python
from aiimi_insight_engine.model_server import ModelServer 
from aiimi_insight_engine.core.certs import load_ca_from_p12, create_ssl_context 
 
ssl_context = create_ssl_context(load_ca_from_p12("elastic-stack-ca.p12", "password123")) 
 
model_server = ModelServer("https://myserver:15008/", ssl_context=ssl_context) 
```
{% endcode %}

***

## Generative AI&#x20;

To use a generative AI model with the Model Server Wrapper, you need to produce a GenerativeModel object. The easiest way is via the get\_generative\_model method.&#x20;

{% code overflow="wrap" lineNumbers="true" %}
```python
ModelServer.get_generative_model(model_type_id, model_id, settings=None, model_parameters=None) 
```
{% endcode %}

<table><thead><tr><th width="165.93212890625">Name</th><th width="119.60467529296875">Type</th><th>Description</th></tr></thead><tbody><tr><td>model_type_id </td><td>string </td><td>Model service provider, e.g. “AzureOpenAIGenerative” </td></tr><tr><td>model_id </td><td>boolean </td><td>Model ID parameter for provider, e.g. “GPT 3.5 Turbo” </td></tr><tr><td>settings </td><td>dict </td><td>Optional, settings dictionary to pass to model server </td></tr><tr><td>model_parameters </td><td>dict </td><td>Optional, model parameters dictionary to pass to model server. It is not required to specify “modelId” here as it will be added in based on earlier parameter. </td></tr></tbody></table>

#### Example&#x20;

<pre class="language-python" data-overflow="wrap" data-line-numbers><code class="lang-python">from aiimi_insight_engine.model_server import ModelServer 
model_server = ModelServer("http://localhost:15008/")
<strong>
</strong><strong>generative = model_server.get_generative_model("AzureOpenAIGenerative", "GPT 4.1 Nano") 
</strong> 
prompt = "What bird does Jack (from the document) think is the best?" 
context = "Jack thinks chickens are the best bird." 
 
print(generative.ask(prompt, context)) 
</code></pre>

***

## Generative Chat&#x20;

For convenience, there is a chat object which can be created with generative AI for longer conversations.

{% code overflow="wrap" lineNumbers="true" %}
```python
# For generative models, you can also create chat objects which remember a conversation 
chat = generative.new_chat() 
print(chat.ask("Hello!")) 
print(chat.ask("What was the last thing you said to me?")) 
 
# Chats can have context too 
chat2 = generative.new_chat(context) 
print(chat2.ask("What other types of bird might Jack like?")) 
```
{% endcode %}

***

## Extractive AI&#x20;

Extractive AI models work in a similar way to generative AI models. They use an ExtractiveModel object which is generated using the get\_extractive\_model method.&#x20;

{% code overflow="wrap" lineNumbers="true" %}
```python
ModelServer.get_extractive_model(model_type_id, model_id) 
```
{% endcode %}

<table><thead><tr><th width="165.09710693359375">Name</th><th width="120.14886474609375">Type</th><th>Description</th></tr></thead><tbody><tr><td>model_type_id </td><td>string </td><td>Model service provider, e.g. “HuggingfaceExtractive” </td></tr><tr><td>model_id </td><td>boolean </td><td>Model ID parameter for provider, e.g. “Tiny Roberta Squad2” </td></tr></tbody></table>

#### Example&#x20;

{% code overflow="wrap" lineNumbers="true" %}
```python
from aiimi_insight_engine.model_server import ModelServer 
model_server = ModelServer("http://localhost:15008/") 
 
extractive = model_server.get_extractive_model("HuggingfaceExtractive", "Tiny Roberta Squad2") 
 
prompt = "What bird does Jack (from the document) think is the best?" 
context = "Jack thinks chickens are the best bird." 
 
print(extractive.ask(prompt, context)) 
 
Outputs from extractive AI are dictionaries with all details of extracted answers contained. Example: 
{ 
   "extractiveAnswers":[ 
      { 
         "answer":"chickens", 
         "chunkNumber":1, 
         "end":20, 
         "executionTime":0.169106, 
         "score":99.52, 
         "start":12, 
         "surroundingContext":"Jack thinks chickens are the best bird.", 
         "surroundingContextWithHighlights":"Jack thinks <b class=""highlight"">chickens</b> are the best bird." 
      } 
   ], 
   "warnings":[] 
}
```
{% endcode %}

***

## Sentence Transformers&#x20;

The model server wrapper allows for the execution of sentence transformer models to vectorise strings. This can be useful for data science purposes as the transformers available will be the same ones used by Workplace AI for document vectorisation and semantic search etc.&#x20;

#### Example&#x20;

{% code overflow="wrap" lineNumbers="true" %}
```python
st_model = model_server.get_sentence_transformer("HuggingfaceSentenceTransformers", "All-mpnet-base-v2 - 768 Dimensions") 
print(st_model.transform("Hello World!")) 
```
{% endcode %}

#### Example Output&#x20;

{% code overflow="wrap" lineNumbers="true" %}
```python
{"executionTime": 0.423893, "vector": [ ... ]} 
```
{% endcode %}

***

## Document Splitting&#x20;

The Workplace AI model server document splitting capability is also exposed by the wrapper, the main use case for this endpoint is the testing of custom document splitting endpoints.&#x20;

#### Example

{% code overflow="wrap" lineNumbers="true" %}
```python
splitter = model_server.get_document_splitter("MaxCharactersSplitter", {"maxChars": 40}) 
print(splitter.split("This is a very long bit of text.\n There are separate sentences.\n So it will split smart.\n I hope.")) 
```
{% endcode %}
