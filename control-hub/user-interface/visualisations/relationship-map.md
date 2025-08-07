# Relationship Map

Visualise the entity relationships and connections between documents and data. See how things like names are connected to phrases, locations and concepts within data sets. &#x20;

Users can perform a search and use this lens to see the nodes and connections. The entities are shown as nodes and the documents or data are the connections between them.&#x20;

* Connect the dots between completely different sets of data and content in one place. Improve decision making and turn your insights into actions.&#x20;
* A new way to visualise the search results in a more insightful, contextual way. Remove the need to dive through pages of individual results to find commonalities.  &#x20;

1. Check Enable/Disable visualisation to determine if users can use this visualisation.&#x20;

### Entities, Metadata and Data

The Entities Shown in Diagram allows a user to select which entities, data and metadata items are available to add to a relationship map.

1. Check all the entities that should be shown in the Relationship Map from the Entities Shown in Diagram dropdown.&#x20;
2. Enter the Minimum Number of Shared Results. This determines the amount of linking documents required to show a node on a connection.
3. &#x20;Enter a Sample Size to use for the explore API.&#x20;
   * A low value can make results less relevant.
   * Higher values can dilute results and increase load times.
4. Enter the maximum number of values for each field that can be selected within Max Initial Nodes Per Field.&#x20;
   * This will stop the graph having too many connections to one common type of data.
5. Enter a limit for how many connection can be made for each field within Max Connection per Field.&#x20;
   1. For example, if a postcode is linked to 100 addresses, this will cap the number of addresses that can be shown.&#x20;

### Relationship Types

You can also define pre-configured relationships types, which help users quickly reuse existing or commonly used relationship maps.

1. Enter the Relationship Type Name for the new type.
2. Select the Entities and properties that will form a map for this relationship type from the Entities Shown dropdown.
3. Enter the number of documents needed to make a connection within Min No. of Shared Results.
4. Select Add Relationship type.
5. You can then arrange the order of these types using the up and down arrows.

<figure><img src="../../../.gitbook/assets/image (298).png" alt=""><figcaption></figcaption></figure>
