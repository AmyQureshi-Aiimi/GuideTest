# Search

Search allows a standard search of Workplace AI, as if it were entered in enterprise search. It returns a DataSample object which has a .df property, a pandas data frame.&#x20;

{% code overflow="wrap" lineNumbers="true" %}
```python
SearchAPI.search(query_string="*", search_flow_id=None, datasets=None, page_size=100, access_level=None, include=None, raw=False) 
```
{% endcode %}

<table><thead><tr><th width="140.21331787109375">Name</th><th width="114.91064453125">Type</th><th>Description</th></tr></thead><tbody><tr><td>query_string </td><td>string </td><td>Free text, search term, can use Lucene syntax </td></tr><tr><td>search_flow_id </td><td>string </td><td>Optionally, the ID for the search flow to use (otherwise will use default) </td></tr><tr><td>datasets </td><td>list of string </td><td>List of dataset IDs to search over, if not provided, all are searched </td></tr><tr><td>page_size </td><td>integer </td><td>Page size (number of documents returned), defaults to 100 </td></tr><tr><td>access_level </td><td>integer </td><td>AIE access level to use, optional, if provided overrides default privileged access state </td></tr><tr><td>include </td><td>string </td><td>Optional, “include” property of AIE JSON filter </td></tr><tr><td>raw </td><td>boolean </td><td>If true, this function returns the JSON response as a dictionary, not a DataSample object. Default is false. </td></tr></tbody></table>

#### Example&#x20;

{% code overflow="wrap" lineNumbers="true" %}
```python
results = search_api.search("Hello World", search_flow_id = "engineering") 
print(results.df) 
```
{% endcode %}
