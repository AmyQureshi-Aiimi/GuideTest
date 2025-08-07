# System Prompt

The system prompt allows you to control the behaviour of the model. You can input variables using placeholders, and conditional text using JINJA Python syntax.

A system prompt is created each time you post a prompt back to a model, even mid-conversation.

### Available System Prompt Variables

* currentDatetime - The current date and time in format YYYY-MM-DD HH:mm:ss.
* username - The user's login username.
* givenName - The user's firse name.
* familyName - The user's last name.
* email - The user's email address.
* departmentName - The user's department.
* jobTitle - The user's job title.
* text - The combined text of all the documents in the search results.
* percentageTokensUsed - The percentage of tokens that have been used for the context window (results).
* percentageTokensLeft - The percentage of tokens that are left for the context window (results).
* hasTermsFilters - True if the search has any terms filters, false otherwise.
* chatCount - The number of chat messages in the chat history.
* filtersChanged - True if the filters have changed since the last chat message.

<figure><img src="../../../.gitbook/assets/image (21).png" alt="" width="563"><figcaption><p>Example System Prompt</p></figcaption></figure>

The below image shoes a more complex agentic system prompt that will perform a deep research task. It calls tools several times to compile a response for a user.

<figure><img src="../../../.gitbook/assets/image (22).png" alt="" width="563"><figcaption></figcaption></figure>
