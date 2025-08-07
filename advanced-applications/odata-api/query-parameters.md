# Query Parameters

## Optional query parameters:

**$top -** The number of results to return. If not given it will return the maximum set by your administrator.\
Return the top 200 results:

```
?$top=200
```

**$skip -** The number of results that are not returned in a result set.\
Don't return the first 10 results:

```
?$skip=10
```

Note - If you apply both Skip and Top, skip will be applied first so you always get the correct number of results. For Example, skip=10 and top=30 would return results 11-40.

**$search -** The search term to be used.\
Return results for water bills:

```
?$search=water bills
```

**$orderby -** Choose which fields to order by and if ascending or descending. If no order is given asc (ascending) is applied by default.

```
?$orderby=Owner desc
```

**$filter -** Add filters to your search.

```
?$filter= Year gt 2008
```

**Combining Filters -** You can combine multiple filters using "and" "or", "not" and "()".

```
$filter= Year le 2004 and status eq false
```

***

## Available Operators

eq - equal

ne - not equal

lt - less than

gt- greater than

le - less than or equal to

ge - greater than or equal to

### Structure example

The curly brackets {} show where data is needed they are not needed in the query.

```
{apiUrl}/odata/{entitySetName}?username={username}&api-key={apikey}&{OtherParameters}
```

***

## OData ID

All results will be returned with a unique ODataID. This can be used as the unique identifier or used to request a single file.

You can request a single result from the API if you have its ODataID. the ID must be within single quotation marks.&#x20;

```
apiURL/odata/entitysetname('odataID')
```

***

## Saved Search

You can use any saved searches from Workplace AI. You can reference them by Name or ID.

1. If you do not provide a type in the query it will default to name.
2. it is not possible to query ?savedsearch and $search together.

### **Name**

The name must be unique and the user must have access to that saved search.

```
?savedSearch={SavedSearchName}&type=name
```

### **ID**

If the saved search does not have a unique name you can use the ID.

```
?savedSearch={savedSearchID}&type=id
```

You can find your saved search ID within Workplace AI.

1. Go to your saved searches.
2. Select the options menu of the relevant saved search.
3. Select the Saved Search ID to copy it to your clipboard.
