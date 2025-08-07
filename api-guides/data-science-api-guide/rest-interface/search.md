# Search

`POST insightmaker/ds/search/datasets/<dataset>`\
Datasets can be a comma separate list of sources, or \* for all.

#### **Body**

Search query in Elasticsearch Query DSL (matching the installed version of Elasticsearch)

<table><thead><tr><th width="100.17244466145831">Parameter</th><th width="250.24072265625">Value</th><th>Example</th></tr></thead><tbody><tr><td>include</td><td>Comma separated list of field ids to include, or * for all.</td><td><p>name,data.myModel.myAttribute</p><p> </p></td></tr><tr><td>size</td><td>Integer, the number of documents to return.</td><td>10</td></tr></tbody></table>

#### **Response**

A list of documents matching the search query. By default, document id and source id are always returned, others must be specified with the include parameter.

{% code overflow="wrap" lineNumbers="true" %}
```python
{
    "scrollId": "DXF1ZXJ5QW5kRmV0Y2gBAAAAAAACHtUWOW42OG1ORzhSUE9wczNJY29YUWFNQQ==",    
    "total": 355,
    "items": [
        {
            "id": "FIoQuHUBC7u0ycD76whe",
            "isSensitive": false,
            "type": "File",
            "sourceId": "documents",
            "name": "hello+world.txt",
            "metadata": {},
            "entities": {},
            "actions": [],
            "collections": [],
            "suggestions": []
        },
        {
            "id": "74sluHUBC7u0ycD7SRt2",
            "isSensitive": false,
            "type": "File",
            "sourceId": "documents",
            "name": "hello+world.txt",
            "metadata": {},
            "entities": {},
            "actions": [],
            "collections": [],
            "suggestions": []
        },
        {
            "id": "_Ifrt3UBC7u0ycD7wnQh",
            "isSensitive": false,
            "type": "File",
            "sourceId": "documents",
            "name": "rcpp_hello_world.R",
            "metadata": {},
            "entities": {},
            "actions": [],
            "collections": [],
            "suggestions": []
        }
    ]
}
```
{% endcode %}
