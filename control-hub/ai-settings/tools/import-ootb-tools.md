# Import OOTB Tools

Import out of the box tools with the Index Utils application. Run the following script to load a series of 'example' tools.

{% code overflow="wrap" lineNumbers="true" %}
```powershell
InsightMaker.IndexUtilities.exe import --tools tools-definitions.json
```
{% endcode %}

Examples:

* **ApplyClassification -** This uses the UpdateFile tool to apply a classification to a file.
* **GetResultDetails -** This tool shows the details page for a search result.
* **ClearResults -** This tool clears the current results context down.
* **GetSimpleAggregation\_aiimi\_invoices -** This tool computes aggregations on data stored within Aimii Insight Engine. It then renders a natural language rendition of the data.
* **Graph -** This tool creates a knowledge graph from a set of results.
* **Search -** This tool performs a search and returns the results to the model.
* **WeatherTool -** This is a sample Python tool, it demonstrates how to extend tool calling with your own functions.

