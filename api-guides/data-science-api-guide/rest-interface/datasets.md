# Datasets

`GET insightmaker/ds/datasets`

#### Response

Details for all available datasets. This includes both content and data sources – distinguishable by their “type” property.

#### Example

<pre class="language-python" data-overflow="wrap" data-line-numbers><code class="lang-python"><strong>    {
</strong>        "id": "shareddrive",
        "description": "Shared Drive",
        "type": "FileSystem",
        "count": 365256
    },
    {
        "id": "sharepoint",
        "description": "Sharepoint",
        "type": "FileSystem",
        "count": 436545
    }

</code></pre>



