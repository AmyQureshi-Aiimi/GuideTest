# Tools

## Tool Calling with Language Models

Tool calling allows language models to use external systems, APIs, and services. Models can perform functions, get real-time data, do calculations, and integrate with your infrastructure.

Based on a users question, the model can identify if it needs anything from an external function. It can select the right function, call it, and use the results in its response. This means responses are no longer limited to text responses.

{% hint style="info" %}
The word Tool and Function are used interchangeably.
{% endhint %}

### How Tool Calling Works

The tool calling process follows a structured workflow:

1. User Query Processing
   * When a user submits a request, the model analyses if it needs external tools for an accurate and complete response.
2. Tool Selection
   * The model compares the available tools and selects the most appropriate based on the users request and tool description.
3. Parameter Extraction
   * The model takes the relevant parameters of the user's request and formats them according to the tool's specified schema.
4. Function Execution
   * The tools are called using the relevant parameters and results are returned to the model.

{% hint style="info" %}
The LLMs do not call the functions. Workplace AI performs the function call and provides the results to the LLM.
{% endhint %}

#### Response Integration

The model then uses the results in a coherent, natural language response for the user.

### Benefits for Organisations

Tool calling transforms a static chatbot into a capable assistant. They can access live data and perform real actions. You can get stock levels, check system statuses, search documents, and interact with databases without leaving the chat. It reduces context switching and ensures responses use accurate and up-to-date information.

### Tool Configuration Architecture

Administrators are able to define tools through structured schemas. You can specify function names, descriptions, required parameters, and expected return formats.

### Getting Started

Workplace AI ships with a series of out of the box tool definitions. You can also create your own tools.
