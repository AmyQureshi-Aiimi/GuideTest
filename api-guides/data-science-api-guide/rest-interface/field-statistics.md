# Field Statistics

`GET insightmaker/ds/datasets/<dataset>/fields/<field_id>`

#### **Response**

Statistics for a given field (format depends on field type).

{% code overflow="wrap" lineNumbers="true" %}
```python
{
    "total": 365256,
    "buckets": [
        {
            "key": "index.js",
            "docCount": 6092
        },
        {
            "key": "package.json",
            "docCount": 5934
        },
        {
            "key": "README.md",
            "docCount": 5334
        },
        {
            "key": "LICENSE",
            "docCount": 3787
        }
    ]
}
```
{% endcode %}
