# Search

`InsightMaker.search(query, dataset=None, fields=None, size=100, raw=False)`

<table><thead><tr><th width="99.85365804036456">Name</th><th width="199.53143310546875">Type</th><th>Description</th></tr></thead><tbody><tr><td>query</td><td>String, dict or insight_maker.api.<br>query_builders.<br>SubQuery</td><td>InsightMaker Query, can either be a <a href="https://lucene.apache.org/core/2_9_4/queryparsersyntax.html">Lucene Syntax</a> query string, <a href="https://www.elastic.co/guide/en/elasticsearch/reference/6.8/query-dsl.html">Elasticsearch Query DSL</a> as a python dictionary (starting at bool), or a SubQuery (or decedent) object from insight_maker.api.query_builders (wrappers for Query DSL)</td></tr><tr><td>dataset</td><td>string, Dataset or list</td><td>Optional - Dataset object, dataset name string, or list of either</td></tr><tr><td>fields</td><td>list</td><td>Optional – List of field ids of Field objects</td></tr><tr><td>size</td><td>integer</td><td>Number of results to return (default 100)</td></tr><tr><td>raw</td><td>boolean</td><td>Default False, if true, returns the raw REST JSON response as a python dictionary.</td></tr></tbody></table>

### Response

A DataSample object, properties:

`DataSample.df`\
A pandas DataFrame object containing all results

`DataSample.scroll_id`\
The scroll ID required for a scroll search

#### Example

Below is an example of a simple string query. These use Lucene Syntax or more simply, they behave in same way as the search box in the enterprise search app. An asterisk will return all documents.

{% code overflow="wrap" lineNumbers="true" %}
```python
results = im.search("*", dataset = "sharepoint")
print(results.df)
```
{% endcode %}

Alternatively, a python dictionary can be used to store an [Elastic Query DSL](https://www.elastic.co/guide/en/elasticsearch/reference/6.8/query-dsl.html) JSON query. This is the most complex, but also most flexible way to query InsightMaker. For example:

{% code overflow="wrap" lineNumbers="true" %}
```python
query = {
    "bool": {
        "must":
            [
                {
                    "range": {"size": {"gte": 1000, "lt": 2000}}
                },
                {
                    "bool":
                        {
                            "must_not": [{"regexp": {"name": {"value": ".*\\.txt"}}}]
                        }
                }
            ]
    }
}

results = im.search(query, dataset = "documents", size = 10)
print(results.df)
```
{% endcode %}
