# Privileged Access

Once authenticated, privileged access mode may be toggled on and off using enable\_privileged\_access and disable\_privileged\_access. The enable setting can accept an access level, it defaults to 1, which corresponds to privileged access. In future releases of Workplace AI if different access levels are made available, this may prove useful.&#x20;

### Enable&#x20;

{% code overflow="wrap" lineNumbers="true" %}
```python
SearchAPI.enable_privileged_access(access_level=1) 
```
{% endcode %}

### Disable&#x20;

{% code overflow="wrap" lineNumbers="true" %}
```python
SearchAPI.disable_privileged_access() 
```
{% endcode %}
