# Field Statistics

`InsightMaker.stats(fields=None, datasets=None)`

<table><thead><tr><th width="100.48470052083331">Name</th><th width="100.16259765625">Type</th><th>Description</th></tr></thead><tbody><tr><td>fields</td><td>list</td><td>Optional - List of Fields objects or strings for field ids. If not provided, all fields are used.</td></tr><tr><td>datasets</td><td>list</td><td>Optional - List of Dataset objects or strings for dataset ids. If not provided, all fields are used.</td></tr></tbody></table>

### Response

A Stats object, either

* `Cast as DataFrame`
* `Stats.to_data_frame()`

Returns the field stats displayed in Pandas DataFrame format

Iterate over multiple FieldStats objects:

`FieldStats.id()`\
String, Field ID

`FieldStats.name()`\
String, Field name

`FieldStats.data_type()`\
Python type object, the Python type for this field (str, datetime, int or float)

`FieldStats.total()`\
The total number of occurrences of this field

`FieldStats.percentage()`\
The total occurrences of this field as a percentage of the overall dataset(s)

`FieldStats.top_values()`\
Return a list of (top value, value count) for this field (or NaN if inappropriate)

`FieldStats.max()`\
Maximum value of this field.

`FieldStats.min()`\
Minimum value of this field.

`FieldStats.average()`\
Average value of this field (mean).

`FieldStats.to_dict()`\
The raw json from the REST response as a python dictionary.

#### Example:

{% code overflow="wrap" lineNumbers="true" %}
```python
stats = im.stats(datasets = "sharepoint")
# stats can be parsed as a DataFrame for ease of exploration
stats_df = stats.to_data_frame()
print(stats_df)
```
{% endcode %}
