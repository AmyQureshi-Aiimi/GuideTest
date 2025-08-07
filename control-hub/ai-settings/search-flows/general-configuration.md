# General Configuration

The configuration needed to set up a Search flow will depend on the type.&#x20;

### **General Settings**

* **Search Flow ID** - Enter a Unique ID for the search flow.
* **Enabled** - If enabled the search flow will be visible to users.
* **Default** - If on, this search flow is selected by default for users. This works in conjunction with the access control list where you can give users different default search flows.&#x20;
* **Name** - Enter a display name for this search flow.
* **Description** - Enter a description to help others know what this search flow is for.
* **Type** - Select what type of search flow this is.
* **Sources** - Select the sources that are valid for the search flow.&#x20;
  * You can override this on a per-search step level.
* **History** **Source** - Select the source that will store the previous chats.&#x20;
  * This requires a source set up to store AI history specifically.
* **Access Control Groups** - The access control lists for the search flow. Only users with these groups will be able to see the search flow.

<figure><img src="../../../.gitbook/assets/image (14).png" alt="" width="563"><figcaption></figcaption></figure>

### **Search Flow Features**

* **Do Initial Search (ChatBot only)** - If checked, the users initial searched to fetch relevant results for the model to use.
* **Ad-Hoc Search (ChatBot only)** - If checked, the user can perform their own searches to add results to the chat.
* **Allow No Results (ChatBot only)** - If checked, the model will answer with no results.&#x20;
  * You can use this to either, allow the model to answer using model memory or, if using tool calling to perform searches.
* **Allow Filter Changes (ChatBot only)** - If checked, the user can change filters once a chat has started.
* **Allow URLs (ChatBot only)** - If checked, users can add URLs to chats.
* **Web Page History Source (ChatBot only)** - Select the source to use to store URL history.&#x20;
  * This requires a source set up to store AI history specifically.
* **Markdown** - If checked, markdown will be rendered in chat responses. Models often produce markdown to help format responses.
* **Cache Context** - If checked, the result context will be cached rather than re-fetching results every time you chat.
* **Include in Search Focus (Search only)** - If checked, this search flow will be included in recommended search flows when results are not found.
* **Filters (ChatBot only)** - Select the filters that are available for users to select to help narrow down results.
* **Max Number of Results** - Enter the maximum number of results that can be provided to a model.
  * This can be overridden at the search step level.
* **Example Prompts** - Enter example prompts that are provided to the user to help.

<figure><img src="../../../.gitbook/assets/image (896).png" alt="" width="563"><figcaption></figcaption></figure>
