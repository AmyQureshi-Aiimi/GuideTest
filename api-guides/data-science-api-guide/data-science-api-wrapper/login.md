# Login

The DS API wrapper automatically authenticates on instantiation of the AiimiInsightEngine object.&#x20;

{% code overflow="wrap" lineNumbers="true" %}
```python
AiimiInsightEngine. __init__(user=None, key=None, host=None, https=False, verify=True) 
```
{% endcode %}

<table><thead><tr><th width="100.28253173828125">Name</th><th width="100.00262451171875">Type</th><th>Description</th></tr></thead><tbody><tr><td>user </td><td>string </td><td>The username associated with the DS API key – if not provided, the system username will be used.</td></tr><tr><td>key </td><td>string </td><td>Either the API key directly, or a path to a file containing it, if not provided API key will be searched for in .\ds.key</td></tr><tr><td>host </td><td>string </td><td>The URL to the Aiimi Insight Engine host (webserver), defaults to localhost:80 </td></tr><tr><td>https </td><td>boolean </td><td>Flag if to connect using HTTPS or not, if not provided, will attempt to determine from the host string.</td></tr><tr><td>verify </td><td>boolean </td><td>Flag to verify HTTPS requests, defaults to True</td></tr></tbody></table>

#### Example&#x20;

{% code overflow="wrap" lineNumbers="true" %}
```python
aie = AiimiInsightEngine(host="AIEserver01", user="jlawton", key="config/key.ds") 
```
{% endcode %}
