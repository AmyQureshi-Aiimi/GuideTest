# Aggregating Results

You can request data aggregations through your OData API query. This groups data and performs functions to summarise specific fields. The aggregated data can then be used for statical analysis. or as a summary.

Aggregations are performed using the query parameter $apply. This parameter can be added as part of the query parameter.

{% code overflow="wrap" %}
```
apiUrl/odata/entitySetName?username=username&api-key=key&$apply= ...
```
{% endcode %}

## **Aggregate a Single Property**&#x20;

**$count** - Returns the total number of results for a query.&#x20;

{% code overflow="wrap" %}
```
$apply=aggregate($count as TotalResults)
```
{% endcode %}

### Non Array Type Aggregation Functions

**Max** - Returns the highest value from your results. _Numeric fields only._

{% code overflow="wrap" %}
```
$apply=aggregate(Rating with max as MaxRating)
```
{% endcode %}

**Min** - Returns the lowest value from your results _Numeric fields only._

{% code overflow="wrap" %}
```
$apply=aggregate(Rating with min as MinRating)
```
{% endcode %}

**Sum** - Adds together all the values of a field. _Numeric fields only._

{% code overflow="wrap" %}
```
$apply=aggregate(OrdersValue with sum as TotalOrdersValue)
```
{% endcode %}

**Average** - Returns the mean of all the values. _Numeric fields only._

{% code overflow="wrap" %}
```
$apply=aggregate(OrderValue with average as AverageOrderValue)
```
{% endcode %}

**countdistinct** - Returns the total number of unique results for a field.\
$apply=aggregate(OrderNumber with countdistinct as TotalUniqueOrders)

**Combine aggregations** - Combine aggregations in 1 query using commas to separate them.\
$apply=aggregate(Rating with max as MaxAge, PersonAge with average as AverageAge)

***

## **Group By Aggregations**

**GroupBy -** Group the results of a field and return the unique values as buckets. When grouping you must use double brackets.

{% code overflow="wrap" %}
```
$apply=groupby((OrderNumber))
```
{% endcode %}

It is possible to group by multiple properties and this will return buckets for each distinct combination of values. These are separated by commas:

**Combined GroupBy** Group the results of 2 fields and return the unique values as buckets. Each field must be separated by commas. When grouping you must use double brackets.

{% code overflow="wrap" fullWidth="false" %}
```
 $apply=groupby((OrderNumber,Customer))
```
{% endcode %}

***

## **Value aggregations on Grouped Buckets.**

You can combine groupby and aggregate functions  to perform aggregations on each bucket.&#x20;

{% code overflow="wrap" %}
```
$apply=groupby((CustomerNumber), aggregate(OrderValue with average as AverageOrderValue))
```
{% endcode %}

This will return a bucket per unique value in CustomerNumber and the average order value for each as AverageOrderValue.
