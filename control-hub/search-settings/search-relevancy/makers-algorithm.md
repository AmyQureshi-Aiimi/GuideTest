# Makers Algorithm

## What Is Makers Algorithm?

Makers algorithm is how Workplace AI determines the relevancy of a result. \
Administrators need to set rules for query types that determine the relevancy of a search result. You can adjust the relevancy score applied to a result based on different Query Types.

### Configuring Makers Algorithm

You must enable Makers algorithm to get Boosted Relevancy Scores.

1. Sign in to the Control Hub.&#x20;
2. Go to Global Settings then Search.&#x20;
3. Select "Enabled" under Makers Algorithm to change the status.&#x20;
   * If the checkbox is marked it is enabled, If it's empty it is disabled.&#x20;
4. Click "Update" to save and apply your changes.

<figure><img src="../../../.gitbook/assets/image (486).png" alt=""><figcaption></figcaption></figure>

### Boost a Relevancy Score

Apply a Boost to the relevancy score of a result from a Phrase, "AND" and "OR" query type. The Boost is the value that is added to a result to determine its "score". \
The higher the boost score the higher up the results list it will appear.&#x20;

Makers algorithm must be enabled for boost layers to take effect. If no Boost Layers are defined, relevancy will revert to default settings.&#x20;

1. Go to Search within the Global Settings of Control Hub.&#x20;
2. Select Add Boost Layer (This will open a modal).&#x20;
3. Choose the query type you want to create.&#x20;
   * Please note, you can only boost one AND query type.&#x20;
4. Select Done.&#x20;
5. To remove a layer Select the Delete (Bin icon).

### Boosting a Phrase&#x20;

When you have added a Phrase query you can add a Boost and a Slop percentage.&#x20;

1. Within the Boost input, enter a score you want to give a result that matches a phrase. The Higher the score the higher in a results list it will appear.&#x20;
2. Within the Slop (%) input, enter the percentage of additional words within a phrase before it’s not a match. For exact matches leave this as 0.&#x20;

The Slop is calculated by the Slop Percentage and the number of words in a query excluding words like "and", "the", and "it".

<figure><img src="../../../.gitbook/assets/image (574).png" alt="" width="563"><figcaption></figcaption></figure>

You can create multiple Phrase boosts with varying Slop percentages and boost so you can have a higher boost for a query with less "Slop" and vice versa.

### Boosting an AND&#x20;

When you have added an AND query you can add a Boost score for this.&#x20;

1. Within the Boost input, enter a score you want to give a result that matches a phrase. The Higher the score the higher in a results list it will appear. You can only boost one AND query type.

<figure><img src="../../../.gitbook/assets/Screenshot 2023-02-13 at 13.51.29.png" alt="" width="563"><figcaption></figcaption></figure>

### Boosting an OR&#x20;

When you have added an OR query you can add a Boost score and Minimum Matching Terms (%) for this.&#x20;

1. Within the Boost input, enter a score you want to give a result that matches a phrase. The Higher the score the higher in a results list it will appear.&#x20;
2. Within the Minimum Matching Terms (%) input, enter the percentage of a search queries terms that must be in the content, file name or metadata to get the boost.

<figure><img src="../../../.gitbook/assets/Screenshot 2023-02-13 at 13.53.20.png" alt="" width="563"><figcaption></figcaption></figure>

#### Slop Percentage

The Slop is calculated by the Slop Percentage and the number of words in a query excluding words like "and", "the", and "it".&#x20;

Create Phrase boosts with varying Slop percentages and boosts. You can have a higher boost for a query with less "Slop" and vice versa.

#### Minimum Matching Terms Percentage&#x20;

The Minimum Matching Terms Percentage can be assigned for an OR query type. It is the percentage of a search queries terms that must be in the content, file name or metadata before it is shown in the results.

If a result matches a boost layer a "score" is attributed to that result. The higher the "score" the higher up the results list it will appear.
