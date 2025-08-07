# Fields

`InsightMaker.fields(include=None, core=True, entities=True, metadata=True, models=True, raw=False)`

<table><thead><tr><th width="99.81374104817706">Name</th><th width="100.36138916015625">Type</th><th>Description</th></tr></thead><tbody><tr><td>include</td><td>list</td><td>List of any combination of "core", "entities" and "metadata" for inclusion in returned object</td></tr><tr><td>core</td><td>boolean</td><td>Alternative to include, boolean, include core fields in return</td></tr><tr><td>entities</td><td>boolean</td><td>Alternative to include, boolean, include entities fields in return</td></tr><tr><td>metadata</td><td>boolean</td><td>Alternative to include, boolean, include metadata fields in return</td></tr><tr><td>models</td><td>boolean</td><td>Alternative to include, boolean, include data model fields in return</td></tr><tr><td>raw</td><td>boolean</td><td>meDefault False, if true, returns the raw REST JSON response as a python dictionary.</td></tr></tbody></table>

### Response

A list of available Field objects, methods:

`Field.id()`\
String, Field ID

`Field.name()`\
String, Field name

`Field.data_type()`\
Python type object, the Python type for this field (str, datetime, int or float)

#### Example

{% code overflow="wrap" lineNumbers="true" %}
```python
model_fields = im.fields(core=False, entities=False, metadata=False, models=True)
print("Model Fields:")
for field in model_fields:
    print("{} : {}".format(field.name(), field.data_type()))
```
{% endcode %}
