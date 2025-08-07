# Datasets

`InsightMaker.datasets(raw=False)`

<table><thead><tr><th width="99.76369222005206">Name</th><th width="100.0982666015625">Type</th><th>Description</th></tr></thead><tbody><tr><td>raw</td><td>boolean</td><td>meDefault False, if true, returns the raw REST JSON response as a python dictionary.</td></tr></tbody></table>

### Response

A list of Dataset objects (includes both data and content indices), methods:

`Dataset.id()`\
String, Dataset ID

`Dataset.description()`\
String, Dataset description

`Dataset.count()`\
Integer, Dataset size

#### Example

{% code overflow="wrap" lineNumbers="true" %}
```python
datasets = im.datasets()

print("Datasets:")
for dataset in datasets:
    print("{} : {}".format(dataset.description(), len(dataset)))
```
{% endcode %}
