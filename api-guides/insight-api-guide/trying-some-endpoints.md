# Trying Some Endpoints

You can now test that your bearer token works by using the /users/me endpoint, which should return information about the current user.

<figure><img src="../../.gitbook/assets/image (685).png" alt=""><figcaption></figcaption></figure>

You can now try and perform a simple search. Here we search a single source for the term “oil” and ask for some facets to also be returned. The facets we ask for are some named entities that appear in the documents. These are returned in groups with their respective values and counts (you get the top 20 values).

Here is the search payload:

{% code overflow="wrap" lineNumbers="true" %}
```python
{
    "sources": [
        "invoices"
    ],
    "include": [
        "data",
        "metadata",
        "actions",
        "entities"
    ],
    "lenses": [
        "search"
    ],
    "scope": 2,
    "queryString": "equipment",
    "pageSize": 12,
    "withHits": true,
    "withTotals": true,
    "withSizes": false,
    "withFacets": true,
    "withChartData": false,
    "page": 1,
    "facets": {
        "terms": [
            [
                "entities.invoice.company"
            ],
            [
                "entities.invoice.contact"
            ]
        ]
    }
}

```
{% endcode %}

<figure><img src="../../.gitbook/assets/image (556).png" alt=""><figcaption></figcaption></figure>

If you have some matching results you should see something like this:

<figure><img src="../../.gitbook/assets/image (672).png" alt=""><figcaption></figcaption></figure>

The hits are within the ‘items’ array and you will find the facets within the ‘facets’ object. In this example, the named entities are within the ‘terms’ sub-object.

<figure><img src="../../.gitbook/assets/image (504).png" alt=""><figcaption></figcaption></figure>
