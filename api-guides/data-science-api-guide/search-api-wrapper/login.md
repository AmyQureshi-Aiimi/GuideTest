# Login

The search API authenticates on initialisation of the SearchAPI object and provides a variety of options for authentication:&#x20;

* Username and password&#x20;
* SMAL&#x20;
* API Key (with future release post-Jalapeno)&#x20;

{% code overflow="wrap" lineNumbers="true" %}
```python
SearchAPI.__init__(host: str, https: bool = True, verify: bool = True, persistent_user: str = None, username: str = None, api_key: str = None, track_response_time: bool = True, csrf: bool = True, reset_persistent_password: bool = False, privileged_access=False, saml = False, encoding: str = "utf-8")  
```
{% endcode %}

<table><thead><tr><th width="222.82958984375">Name</th><th width="89.9522705078125">Type</th><th>Description</th></tr></thead><tbody><tr><td>host </td><td>string </td><td>Host URL </td></tr><tr><td>https </td><td>boolean </td><td>If to use the HTTPS protocol, default True </td></tr><tr><td>verify </td><td>boolean </td><td>If to verify HTTPS requests, default True </td></tr><tr><td>persistent_user </td><td>string </td><td>Optionally, a user to store a persistent login for (meaning passwords will only be asked for on the first run) </td></tr><tr><td>username </td><td>string </td><td>A username to be used with API key authentication (with future release post-Jalapeno) </td></tr><tr><td>api_key </td><td>string </td><td>API Key (with future release post-Jalapeno) </td></tr><tr><td>track_response_time </td><td>boolean </td><td>Flag to allow the wrapper to time AIE responses in the background </td></tr><tr><td>csrf </td><td>boolean </td><td>Flag to enable usage of CSRF cookies in authentication, defaults True </td></tr><tr><td>reset_persistent_password </td><td>boolean </td><td>Flag to reset the password of a persistent user, defaults False </td></tr><tr><td>privileged_access </td><td>boolean </td><td>Flag to initialise the wrapper using privileged access mode, defaults to False </td></tr><tr><td>saml </td><td>boolean </td><td>Flag to use SAML authentication, which opens a browser window for the user to sign in, defaults to False (SAML authentication requires the optional packages, selenium and webdriver-manager) </td></tr><tr><td>encoding </td><td>string </td><td>Encoding type to use for decoding generative streams, defaults to “utf-8” – there should be no need to change this value. </td></tr></tbody></table>

#### Example

{% code overflow="wrap" lineNumbers="true" %}
```python
search = SearchAPI("localhost", verify=False, https=True, csrf=False) 
```
{% endcode %}
