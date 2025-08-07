# Concepts

## LLM Tool Calling Function Definitions

Tool calling allows language models to use external systems, APIs, and services. The foundation of this lies in **JSON Schema** definitions. They describe each available tool's interface, parameters, and expected behaviour.

### What is a Function Definition?

A function definition is a structured specification that tells the LLM:

* A description of what the function does
* The parameters it accepts
* What parameters are required and what are optional
* The expected data types for each parameter
* Valid value constraints and formats

***

## JSON Schema Structure

Function definitions use JSON Schema formats with these key components:

### Basic Structure

{% code overflow="wrap" lineNumbers="true" fullWidth="false" %}
```json
{
  "name": "function_name",
  "description": "What this function does",
  "parameters": {
    "type": "object",
    "properties": {
      "parameter_name": {
        "type": "string|number|boolean|array|object",
        "description": "What this parameter is for",
        "enum": ["option1", "option2"],
        "default": "default_value"
      }
    },
    "required": ["required_parameter_names"],
    "additionalProperties": false
  }
}
```
{% endcode %}

### Core Fields

* **`name`** (string, required)
  * The function identifier that the LLM will use to call this tool.
  * Should be descriptive and follow snake\_case or camelCase naming conventions.
* **`description`** (string, required)
  * This helps the LLM understand when to use this tool.
  * Should be a clear explanation of what the function does.
  * It's important it is concise but informative.
* **`parameters`** (object, required)
  * Defines the function's input schema using JSON Schema.
  * Always has `"type": "object"` at the root level.

***

## Parameter Types and Constraints

#### String Parameters

{% code overflow="wrap" lineNumbers="true" %}
```json
"username": {
  "type": "string",
  "description": "User's login name",
  "minLength": 3,
  "maxLength": 50,
  "pattern": "^[a-zA-Z0-9_]+$"
}
```
{% endcode %}

#### Number Parameters

{% code overflow="wrap" lineNumbers="true" %}
```json
"temperature": {
  "type": "number",
  "description": "Temperature in Celsius",
  "minimum": -273.15,
  "maximum": 1000
}
```
{% endcode %}

#### Boolean Parameters

{% code overflow="wrap" lineNumbers="true" %}
```json
"include_metadata": {
  "type": "boolean",
  "description": "Whether to include additional metadata",
  "default": false
}
```
{% endcode %}

#### Array Parameters

{% code overflow="wrap" lineNumbers="true" %}
```json
"tags": {
  "type": "array",
  "description": "List of category tags",
  "items": {
    "type": "string"
  },
  "minItems": 1,
  "maxItems": 10
}
```
{% endcode %}

#### Object Parameters

{% code overflow="wrap" lineNumbers="true" %}
```json
"user_profile": {
  "type": "object",
  "description": "User profile information",
  "properties": {
    "name": {"type": "string"},
    "age": {"type": "number"}
  },
  "required": ["name"]
}
```
{% endcode %}

#### Enum Parameters

{% code overflow="wrap" lineNumbers="true" %}
```json
"priority": {
  "type": "string",
  "description": "Task priority level",
  "enum": ["low", "medium", "high", "urgent"]
}
```
{% endcode %}

***

## Complete Example

{% code overflow="wrap" lineNumbers="true" %}
```json
{
  "type": "function",
  "function": {
    "name": "Search_ai_demo",
    "description": "Performs a search to find relevant information to answer a users question. Use the makers_clear_water_inc sourceId for water related queries.",
    "parameters": {
      "type": "object",
      "properties": {
        "queryString": {
          "type": "string",
          "description": "The search query string. Just provide keywords that you want to search for. Do not provide the field name or anything else."
        },
        "sourceIds": {
          "description": "The source ids to search.",
          "items": {
            "enum": [
              "ai_demo",
              "makers_clear_water_inc"
            ],
            "type": "string"
          },
          "type": "array"
        },
        "size": {
          "type": "number",
          "description": "The number of results to return. If you do not pass this then the default number will be returned. This parameter should only be set if the user asks for a specific number of results to be returned."
        }
      },
      "required": [
        "queryString",
        "sourceIds"
      ]
    }
  }
}
```
{% endcode %}

***

## Best Practices

#### Clear Descriptions

* Write the descriptions from the LLM's perspective.
* Explain when and why to use the function.
* Include information about the expected outcomes.

#### Parameter Naming

* Use descriptive, self-explanatory names.
* Follow a consistent naming convention.
* Avoid abbreviations unless universally understood.

#### Validation and Constraints

* Set appropriate minimum and maximum values.
* Use enums for fixed sets of options.
* Include format specifications for dates, emails, URLs.
* Set realistic string length limits.

#### Required vs Optional

* Mark any essential parameters as required.
* Provide sensible defaults for optional parameters.
* Consider the minimum viable function call.

#### Error Prevention

* Use `additionalProperties: false` to prevent unexpected parameters.
* Include format validations where applicable.
* Set realistic bounds on numeric values.

***

## Advanced Features

#### Conditional Parameters

Use `oneOf`, `anyOf`, or `allOf` for complex parameter relationships:

{% code overflow="wrap" lineNumbers="true" %}
```json
"search_criteria": {
  "oneOf": [
    {
      "properties": {
        "by_name": {"type": "string"}
      },
      "required": ["by_name"]
    },
    {
      "properties": {
        "by_id": {"type": "integer"}
      },
      "required": ["by_id"]
    }
  ]
}
```
{% endcode %}

#### Dynamic Validation

{% code overflow="wrap" lineNumbers="true" %}
```json
"coordinates": {
  "type": "object",
  "properties": {
    "latitude": {
      "type": "number",
      "minimum": -90,
      "maximum": 90
    },
    "longitude": {
      "type": "number", 
      "minimum": -180,
      "maximum": 180
    }
  },
  "required": ["latitude", "longitude"]
}
```
{% endcode %}

***

## Testing Your Definitions

When creating function definitions:

1. **Validate JSON Schema** - Ensure your schema is syntactically correct.
2. **Test Edge Cases** - Consider boundary values and invalid inputs.
3. **Verify Descriptions** - Make sure they clearly communicate intent.
4. **Check Required Fields** - Ensure minimum viable calls work.
5. **Test with LLM** - Verify the model understands when to use your function.

***

## Troubleshooting

Well-crafted function definitions are the key to successful LLM tool integration. This enables models to understand not just what tools are available, but exactly how and when to use them effectively.

### **LLM doesn't call your function**

1. Check the description clearly indicates when to use it.
2. Ensure required parameters aren't too restrictive.
3. Verify the function name is intuitive.

### **Parameter errors**

1. Review your type definitions and constraints.
2. Check for typos in parameter names.
3. Ensure required parameters are actually needed.

### **Function called incorrectly**

1. Add more specific descriptions.
2. Use enums to limit parameter values.
3. Include examples in descriptions where helpful.
