# Open & Closed Book AI

Once your LLMs are set up you can make them available to users in Closed or Open Book AI.&#x20;

**Closed Book AI** - This allows users to access the AI from the main navigation. The AI will use a wide range of sources, documents and information to respond to a prompt.

**Open Book AI** - This allows users to access the AI from a document. The AI will use the information within the selected documents to respond to a prompt.

You will need to create search flows for this. These will have a few specific requirements but otherwise is set up like any other.

_For support creating a search flow_ [see our guide on creating a new search flow.](https://docs.aiimi.com/aiimi-insight-engine/control-hub/global-settings/search-flows/create-a-search-flow/general)

***

### General

**Type** - Must be "Result".

**Features** - Check Generative Open Book and/or Generative Closed Book.

### Query Classification Step

The query classification step should stay disabled.

### Model Steps

**Cache context** - We recommend enabling this to cache the results after the first prompt.

**Max New Tokens** - Enter the maximum size of the LLM response.

**Temperature** - 0.1 is recommended. Models usually range between 0 - 2.

