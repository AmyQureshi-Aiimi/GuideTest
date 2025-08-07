# Built In Functions and Tools

There are a few built in tools that ship with Workplace AI. There are two types, server side tools and pure client side tools. Server side tools involve a call back to Workplace AI to fetch data and render results. Pure client side tools render a response using a client side component. They do not send any data back to the LLM model.

## Available Server Side Tools

### Search

This performs a search for data within Workplace AI and posts the data back to the LLM.

#### Required Parameters

**searchStepId** (string)

* This defines the search step configuration to use. [For more information see our search flow guide.](broken-reference)

<pre class="language-json" data-overflow="wrap" data-line-numbers><code class="lang-json">"searchStepId": {
  "type": "string",
<strong>  "enum": ["water"],
</strong>  "description": "The search step to use. Choose the search step that will contain the results relevant to the users question."
}
</code></pre>

**size** (number)

* The number of results to return.

{% code overflow="wrap" lineNumbers="true" %}
```json
"size": {
    "type": "number",
    "description": "The number of results to return. If you do not pass this then the default number will be returned. This parameter should only be set if the user asks for a specific number of results to be returned."
}
```
{% endcode %}

**sort** (object)

* The field to sort on, specified with the field parameter.
* Use the Boolean descending parameter to determine if we sort descending.

[For information around filtering see General Search Parameters.](built-in-functions-and-tools.md#general-search-parameters)

{% code overflow="wrap" lineNumbers="true" %}
```json
"sort": {
    "type": "object",
    "description": "Defines the sort configuration for a query",
    "properties": {
        "field": {
            "type": "string",
            "enum": [ "field.name" ],
            "description": "The field to sort on"
        },
        "descending": {
            "type": "boolean",
            "description": "Set this to true for descending order, false for ascending order",
            "default": true
        }
    },
    "required": ["field"]
}
```
{% endcode %}

### GetSimpleAggregation

This performs an aggregation (sum, average, min, max) on data that is stored in the Workplace AI repository.

It uses a dynamic chart component and not natural language to respond to the user.

#### Required Parameters

**fieldToAggregate** (string)

* The numeric field to perform calculations on.

{% code overflow="wrap" lineNumbers="true" %}
```json
{
  "fieldToAggregate": {
    "type": "string",
    "enum": [ 
      "data.aiimiInvoices.sumAmountPaid", 
      "data.aiimiInvoices.sumTotal" 
    ],
    "description": "The field to aggregate. If you are asked for a count, then you can select any of these values."
  }
}
```
{% endcode %}

**aggregationType** (string)

* The mathematical operation to perform on the field.
* Options:
  * `average` - Calculate mean value
  * `sum` - Add all values together
  * `count` - Count number of records
  * `min` - Find minimum value
  * `max` - Find maximum value

{% code overflow="wrap" lineNumbers="true" %}
```json
{
  "aggregationType": {
    "type": "string",
    "enum": ["average", "sum", "count", "min", "max"],
    "description": "The type of aggregation to perform."
  }
}
```
{% endcode %}

**chartType** (string)

* The visual format for displaying results.
* Options:
  * `bar` - Bar chart
  * `pie` - Pie chart
  * `radar` - Radar/spider chart
  * `table` - Tabular data display
  * `metric` - Single metric display

{% code overflow="wrap" lineNumbers="true" %}
```json
{
  "chartType": {
    "type": "string",
    "enum": ["bar", "pie", "radar", "table", "metric"],
    "description": "The type of chart or table to generate. Always include this."
  }
}
```
{% endcode %}

**title** (string)

* A descriptive title for the aggregation.
* Used to identify and label the aggregation in the user interface.

{% code overflow="wrap" lineNumbers="true" %}
```json
{
  "title": {
    "type": "string",
    "description": "Whether to ignore zero values.",
    "default": false
  }
}
```
{% endcode %}

**ignoreZero** (Boolean)

* Whether to ignore zero values on the **fieldToAggregate.**

{% code overflow="wrap" lineNumbers="true" %}
```json
{
  "ignoreZero": {
    "type": "boolean",
    "description": "Whether to ignore zero values.",
    "default": false
  }
}
```
{% endcode %}

#### Optional Parameters

**groupBy** (string)

* Primary field to group results by.

{% code overflow="wrap" lineNumbers="true" %}
```json
{
  "groupBy": {
    "type": "string",
    "enum": [ 
      "data.aiimiInvoices.invoiceNumber", 
      "data.aiimiInvoices.status", 
      "data.aiimiInvoices.contactName" 
    ],
    "description": "The field to group on."
  }
}
```
{% endcode %}

**groupBySecondary** (string)

* Secondary field for additional grouping level.
* Creates nested groupings when used with groupBy.

{% code overflow="wrap" lineNumbers="true" %}
```json
{
  "groupBySecondary": {
    "type": "string",
    "enum": [ 
      "data.aiimiInvoices.invoiceNumber", 
      "data.aiimiInvoices.status", 
      "data.aiimiInvoices.contactName" 
    ],
    "description": "The field to group on."
  }
}
```
{% endcode %}

[For information around filtering see General Search Parameters.](built-in-functions-and-tools.md#general-search-parameters)

### GetSimpleAggregationNoUI

This is the same as GetSimpleAggregation but it expects the 'add tool data' and 'call generative' options to be selected. This means the model will render a natural language response.

The chartType parameter will be ignored by the tool.

[For information around filtering see General Search Parameters.](built-in-functions-and-tools.md#general-search-parameters)

### **General Search Parameters**

**sourceIds** (array)

* Specifies which data sources to search within Workplace AI.
* Select one or more source relevant to your search query.

{% code overflow="wrap" lineNumbers="true" %}
```json
"sourceIds": {
    "type": "array",
    "description": "The source ids to search.",
    "items": {
        "type": "string",
        "enum": [ "my_source_one", "my_source_two" ]
    }
}
```
{% endcode %}

**sourceId** (string, required)

* The source identifier for the data set.
* This specifies which dataset to query.

{% code overflow="wrap" lineNumbers="true" %}
```json
"sourceId": {
    "type": "string",
    "enum": [ "my_source_one", "my_source_two" ],
    "description": "The source id for the data set."
}
```
{% endcode %}

**queryString** (string)

* Free-text search terms to find relevant information.
* Use simple keywords without field names or Boolean operators.
  * "steel fabrication costs" or "delivery schedule".

{% code overflow="wrap" lineNumbers="true" %}
```json
"queryString": {
    "type": "string",
    "description": "The search query string. Just provide keywords that you want to search for. Do not provide the field name or anything else."
}
```
{% endcode %}

**filters** (object)

* Apply specific term filters to narrow search results.
* The key of the object will be the field to filter on.
* You can then specify optional enum to constrain values.

{% code overflow="wrap" lineNumbers="true" %}
```json
"filters": {
    "type": "object",
    "description": "An optional filter to apply to the data set.",
    "properties": {
        "data.aiimiInvoices.status": {
            "type": "array",
            "items": {
                "type": "string",
                "enum": [ "PAID", "DELETED", "AUTHORISED" ]
            }
        }
    }
}
```
{% endcode %}

**numericRangeFilter** (array)

* Filter results based on numeric value ranges.
* Each filter contains:
  * `field` - The numeric field to filter on.
  * `greaterThanOrEqualTo` - Minimum value (inclusive).
  * `lessThanOrEqualTo` - Maximum value (inclusive).

{% code overflow="wrap" lineNumbers="true" %}
```json
"numericRangeFilter": {
    "type": "array",
    "description": "Optional numeric range filters.",
    "items": {
        "type": "object",
        "properties": {
            "field": {
                "type": "string",
                "enum": [ "field.name" ],
                "description": "The numeric field to filter on"
            },
            "greaterThanOrEqualTo": {
                "type": "number",
                "description": "Greater than or equal to value"
            },
            "lessThanOrEqualTo": {
                "type": "number",
                "description": "Less than or equal to value."
            }
        },
        "required": ["field", "greaterThanOrEqualTo", "lessThanOrEqualTo"]
    }
}
```
{% endcode %}

**dateRangeFilter** (array)

* Filter results based on date ranges.
* Each filter contains:
  * `field` - The date field to filter on.
  * `from` - Start date in ISO format (inclusive).
  * `to` - End date in ISO format (inclusive).

{% code overflow="wrap" lineNumbers="true" %}
```json
"dateRangeFilter": {
    "type": "array",
    "description": "Optional date range filters. Valid date fields are: data.aiimiSales.dateInitiated",
    "items": {
        "type": "object",
        "properties": {
            "field": {
                "type": "string",
                "enum": [ "field.name" ],
                "description": "The date field to filter on"
            },
            "from": {
                "type": "string",
                "format": "date-time",
                "description": "Start date (inclusive) in ISO format"
            },
            "to": {
                "type": "string",
                "format": "date-time",
                "description": "End date (inclusive) in ISO format"
            }
        },
        "required": ["field", "from", "to"]
    }
}
```
{% endcode %}

### UpdateFile

This can update file metadata and entities.

#### Required Parameters

**sourceId** (string)

* Identifies the data source of the file to be classified.

**id** (string)

* Unique identifier of the specific document or object to classify.

**fields** (object)

* Contains the metadata or entity fields to update for the document.
* This is a dictionary where the keys are the fields, and the type is an array of strings.

### RemoteTool

This is a proxy tool that will attempt to execute the tool via the AIModelService. You never use 'RemoteTool' as the function name, use the name of the function as advertised by the AIModelService.

## Pure Client Side Tool

These tools do not make a call back to Workplace AI and use client side components to render the result to a user.

### ClearResults

This clears the results from the result context which means they do not get sent to the LLM model.

It helps you save on context space as an interaction with an LLM grows (i.e. the context grows).

### Graph

This renders a client side relationship map (knowledge network). The parameters are defined in the example tool call and are not configurable.

### ResultDetails

This renders a client side table that contains the details for a result. It takes a single parameter, the result index (id).

