# Search Flows

Search focuses allow administrators to simplify using search and large language models for users. They help users arrive at a smaller, high quality, set of relevant results. It can also automatically pick the right LLM (GenAI) model used to answer a prompt.

{% hint style="info" %}
Search Flows are configured within the Control Hub under Global Settings. See our guide on configuring search flows for more information.
{% endhint %}

### How search flows help:

* Users can become overwhelmed with the number of search results. Filtering is a good way to reduce this number of results, but relies on users selecting the right ones, if any. Search flows can select the right filters based on the query. They reduce friction and direct users to fewer, more relevant results. We call this smart filtering
* Every enterprise has information stored across many sources. Often what different user types need will be in a specific source. Search flows can pre-select any number of sources for the user based on their need. This helps shrink the data world down further and improve result relevancy.
* Different algorithms work better for different search queries. For example, a fine-tuned QA semantic model will work best if a user asks a question. However, users are unlikely to know the best algorithm for them. The query classification capability allows us to do this for the user automatically. This ensures the best algorithm for what the user needs.
* LLMs come in different shapes, sizes and complexity, with costs to reflect that. Common business prompts, like fact extraction or summarisation, don't need a large model for good results. The prompt classification allows us to do this for the user automatically. This means the best model is used for the users prompt.
* It's essential to be able to audit the use of GenAI. You can store all the generative AI history within the repository. This allows compliance users to monitor use (subject to permissions). But, also means users can find and continue working from previous chats.

All of our Search Flow features are available in the main user interface and via the Insight API. This allows you to leverage these features when building your own app.

<figure><img src="../../../.gitbook/assets/image (44).png" alt=""><figcaption><p>Seatch Flows</p></figcaption></figure>
