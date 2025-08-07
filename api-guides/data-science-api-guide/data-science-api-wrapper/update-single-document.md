# Update Single Document

`InsightMaker.update(dataset, document_id, body)`\
Allows you to update a single document, given its id.

<table><thead><tr><th width="124.67152913411456">Name</th><th width="124.82806396484375">Type</th><th>Description</th></tr></thead><tbody><tr><td>dataset</td><td>String or Dataset</td><td>Dataset object or dataset name string</td></tr><tr><td>document_id</td><td>String</td><td>Document ID</td></tr><tr><td>body</td><td>Dictionary</td><td>Key value pairs of properties &#x26; their updated values (these can be any InsightMaker properties, including data attributes)</td></tr></tbody></table>

### Response

True

#### Example

{% code overflow="wrap" lineNumbers="true" %}
```python
im.update("documents", "SoXQt3UBC7u0ycD7FRg2", {"metadata.title": "Hello Python"})
```
{% endcode %}
