# Scroll Search

`InsightMaker.scrolled_search(query, dataset=None, fields=None, scroll_size=100,max_size=10000)`\
Combines the search and scroll methods to perform a scrolled search up to a limit (good for large downloads).

<table><thead><tr><th width="99.87111409505206">Name</th><th width="199.736572265625">Type</th><th>Description</th></tr></thead><tbody><tr><td>query</td><td>String, dict or insight_maker.api.<br>query_builders.<br>SubQuery</td><td>InsightMaker Query, can either be a Lucene Syntax query string, Elasticsearch Query DSL as a python dictionary (starting at bool), or a SubQuery (or decedent) object from insight_maker.api.query_builders (wrappers for Query DSL)</td></tr><tr><td>dataset</td><td>string, Dataset or list</td><td>Optional - Dataset object, dataset name string, or list of either</td></tr><tr><td>fields</td><td>list</td><td>Optional – List of field ids of Field objects</td></tr><tr><td>scroll_size</td><td>integer</td><td>Number of results to return per page (default 100)</td></tr><tr><td>max_size</td><td>integer</td><td>Maximum number of documents to acquire (default 10,000)</td></tr></tbody></table>

### Response

A DataSample object, properties:

`DataSample.df`\
A pandas DataFrame object containing all results

`DataSample.scroll_id`\
The scroll ID required for a scroll search

#### Example

{% code overflow="wrap" lineNumbers="true" %}
```python
results = im.scrolled_search("*", dataset = "sharepoint", scroll_size=10, max_size=100)

print(results.df)
```
{% endcode %}
