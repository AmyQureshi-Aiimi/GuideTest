# Set Access

Within your 3rd party analytics tool you need to create an OData query. You need to select OData Feed as your source type.

The API URL and user credentials must be entered at the beginning to authenticate access.&#x20;

1. Enter the OData API Endpoint URL from your administrator.
   * Contact your Workplace AI administrator to get this from the control hub.

```
apiUrl/odata/entitySetName
```

2. Using query parameters enter your Workplace AI username and API key to start the query.

* Contact your Workplace AI administrator to get this information.

```
?username=usernamehere
?api-key=apikeyhere
```

#### Example Structure:

```
apiUrl/odata/entitySetName?username=username&api-key=apikey&
```

