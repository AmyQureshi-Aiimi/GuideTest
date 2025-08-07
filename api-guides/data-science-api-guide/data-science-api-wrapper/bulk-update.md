# Bulk Update

`DataSample.update_to_insight_maker(im , columns, mask=None, value=None)`\
A function of a DataSample object (returned from searches) to update all documents returned from that search.

<table><thead><tr><th width="99.99977620442706">Name</th><th width="124.7867431640625">Type</th><th>Description</th></tr></thead><tbody><tr><td>im</td><td>InsightMaker</td><td>InsightMaker object associated with instance to perform update on</td></tr><tr><td>columns</td><td>List or String</td><td>single column to update or list of column names</td></tr><tr><td>mask</td><td>Iterable</td><td>Optional – A filter for a Pandas DataFrame to select rows to update</td></tr><tr><td>value</td><td>Any</td><td>Optional – Update supplied column(s) to this value, rather than the ones in DataSample.df</td></tr></tbody></table>

### Response

True

#### Example

{% code overflow="wrap" lineNumbers="true" %}
```python
# Search a result set
results = im.search("Hello World", dataset = "documents")

# Update results set with a value
results.update_to_insight_maker(im, "metadata.title", value="Test Python")
```
{% endcode %}

