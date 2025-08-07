# Fields

`GET insightmaker/ds/datasets/fields`

<table><thead><tr><th width="99.52742513020831">Parameter</th><th width="350.008544921875">Value</th><th>Example</th></tr></thead><tbody><tr><td>include</td><td>Comma separated combination of core, entities, metadata &#x26; models. For specifying which type of fields to return</td><td>core,entities</td></tr></tbody></table>

#### Response

Details of all available fields, their types and descriptions (including data model attributes).

{% code overflow="wrap" lineNumbers="true" %}
```python
{
    "core": [
        {
            "id": "name",
            "name": "name",
            "description": "File Name",
            "type": "Core",
            "dataType": "Keyword"
        },
        {
            "id": "extension",
            "name": "extension",
            "description": "File Extension",
            "type": "Core",
            "dataType": "Keyword"
        },
        {
            "id": "md5",
            "name": "md5",
            "description": "Checksum",
            "type": "Core",
            "dataType": "Keyword"
        },
        {
            "id": "owner",
            "name": "owner",
            "description": "File Owner",
            "type": "Core",
            "dataType": "Keyword"
        },
        {
            "id": "crawlDate",
            "name": "crawlDate",
            "description": "Crawl Date",
            "type": "Core",
            "dataType": "Datetime"
        },
        {
            "id": "enrichmentDate",
            "name": "enrichmentDate",
            "description": "Enrichment Date",
            "type": "Core",
            "dataType": "Datetime"
        }
    ],
    "metadata": [
        {
            "id": "metadata.createdDate",
            "name": "createdDate",
            "description": "Created Date",
            "type": "Metadata",
            "dataType": "Datetime"
        },
        {
            "id": "metadata.lastAuthor",
            "name": "lastAuthor",
            "description": "Last Author",
            "type": "Metadata",
            "dataType": "Keyword"
        }
    ],
    "entities": []
}
```
{% endcode %}
