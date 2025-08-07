# ChatBot Class

The ChatBot class is an extension of the Chat class, designed to provide a chatbot interface that interacts with the SearchAPI wrapper. It is used to facilitate conversational interactions by leveraging search flows and generative responses. Below is a detailed overview of the class and its functionalities.&#x20;

## Initialisation&#x20;

{% code overflow="wrap" lineNumbers="true" %}
```python
ChatBot(search_api: SearchAPI, search_flow: str, initial_prompt: str, access_level: int = 0, max_results: int = None)  
```
{% endcode %}

`search_api`\
An instance of the SearchAPI object used to connect to the AI Enrichment (Aiimi Insight Engine) platform.&#x20;

`search_flow`\
A string representing the ID of the search flow to be used for chat interactions.&#x20;

`initial_prompt`\
A string containing the initial prompt for the chat.&#x20;

`access_level`\
An integer representing the Aiimi Insight Engine access level, defaulting to 0.&#x20;

`max_results`\
An optional integer to override the maximum number of results for Retrieval-Augmented Generation (RAG). Defaults to the configured value for the search flow or 10 if not specified.&#x20;

### Attributes&#x20;

`initial_search_seconds`\
The time taken for the initial search query to complete.&#x20;

`chat_history`\
A list maintaining the history of chat interactions, including user prompts and assistant responses.&#x20;

### Methods&#x20;

The ChatBot class inherits several methods from the Chat class, which are used to manage chat interactions:&#x20;

`generative_stream() -> GenerativeResponse`\
Initiates a generative stream request using the current chat history and settings.&#x20;

`ask(prompt: str, return_header: bool = False) -> GenerativeResponse`\
Sends a user prompt to the chat and returns the generative response.&#x20;

`latest_response()`\
Returns the latest response content from the chat history.&#x20;

`split_on_double_newline_and_keep_newlines(input_str: str) -> list[str]`\
Splits a string on double newlines while preserving the newlines in the resulting list of strings.&#x20;

### Usage&#x20;

The ChatBot class is designed to facilitate conversational interactions by integrating search capabilities with generative responses. Upon initialisation, it performs an initial search using the provided prompt and search flow, setting up the context for subsequent interactions.&#x20;

#### Example

{% code overflow="wrap" lineNumbers="true" %}
```python
# Initialize the SearchAPI 
search_api = SearchAPI("localhost", verify=False, https=True, csrf=False) 
 
# Define the search flow and initial prompt 
search_flow = "example_search_flow" 
initial_prompt = "What is the impact of climate change on polar bears?" 
 
# Create an instance of ChatBot 
chatbot = ChatBot( 
    search_api=search_api, 
    search_flow=search_flow, 
    initial_prompt=initial_prompt, 
    access_level=1 
) 
 
# Ask a question using the ChatBot 
response = chatbot.ask("How can we mitigate these impacts?") 
print(response.text_response) 
 
# Retrieve the latest response from the chat history 
latest_response = chatbot.latest_response() 
print("Latest response:", latest_response) 
```
{% endcode %}
