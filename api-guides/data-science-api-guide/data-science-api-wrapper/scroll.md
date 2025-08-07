# Scroll

`InsightMaker.scroll(sample, append=True, raw=False)`\
A scrolled search to provide additional results to those from a previous search using a scroll id.

<table><thead><tr><th width="99.91426595052081">Name</th><th width="125.209716796875">Type</th><th>Description</th></tr></thead><tbody><tr><td>sample</td><td>DataSample or string</td><td>DataSample object to perform scrolled search for, or scroll id as a string.</td></tr><tr><td>append</td><td>boolean</td><td>Default, True – if true append the scrolled results to the provided DataSample object (making it larger), if false, return a new DataSample object containing only new results.</td></tr><tr><td>raw</td><td>boolean</td><td>Default False, if true, returns the raw REST JSON response as a python dictionary.</td></tr></tbody></table>

### Response

DataSample object properties

`DataSample.df`\
A pandas DataFrame object containing all results

`DataSample.scroll_id`\
The scroll ID required for a scroll search

#### Example

{% code overflow="wrap" lineNumbers="true" %}
```python
results = im.search("*", dataset = "sharepoint")

extra_results = im.scoll(results, append=False)
```
{% endcode %}
