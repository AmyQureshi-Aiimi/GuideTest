# Create and Edit Tools

The Create and Edit Tool interface allows you to create, modify, and manage custom tools used by Aiimigo.

You can create multiple configurations of the same name for different scenarios. This allows you to control parameter values and improve tool calling accuracy.

## Interface Components

### Basic Configuration

#### **ID Field**

* **Purpose**: Unique identifier for the tool.
* **Format**: Use descriptive names with underscores (e.g., `search_ai_demo`).
* **Requirements**: Must be unique across all tools.
* **Best Practice**: Use clear, descriptive names that indicate the tool's function.

**Function Name**

* **Purpose**: The underlying function that will be called (see list of valid tool types).
* **Format**: Human-readable name (e.g., "Search").
* **Usage**: This name appears in tool lists and user interfaces.

**Description**

* **Purpose**: Brief explanation of what the tool does.
* **Best Practice**: Keep concise but informative.
* **Example**: "The AI Demo search call".

**Enabled Toggle**

* **Purpose**: Controls whether the tool is available to use.
* **States**:
  * ✅ Enabled (green) - Tool is active
  * ❌ Disabled (red) - Tool is inactive

### Function Definition

The Function Definition contains the JSON schema that defines how the tool operates.

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

**Key Elements:**

**Function Object Structure:**

* `type`: Always set to "function".
* `function`: Contains the main function definition.

**Function Properties:**

* `name`: Internal function name this should match the Function Name field.
* `description`: Detailed explanation of the function's purpose and usage.
* `parameters`: Defines the input parameters the function accepts.

**Parameters Structure:**

* `type`: Usually "object" for complex parameters.
* `properties`: Defines each parameter the function accepts.
  * Each property should have:
    * `type`: Data type (string, number, boolean, etc.).
    * `description`: Clear explanation of what the parameter does.

#### Access Control Groups

* **Purpose**: Restricts which user groups can access this tool.
* **Configuration**: Start typing to search and select groups.
* **Best Practice**: Only grant access to groups that need the functionality.

### Tool Configuration Options

#### **Add Tool Data**

* **Purpose**: Checkbox to pass the tool response to the LLM.
* **When to use**: If the LLM model needs to know results from a tool call. In most cases you will want this enabled. There are some 'client side' tools that do not need to pass anything back.

#### **Call Generative**

* **Purpose**: Checkbox to tell Aiimigo to post the results of tool calls back to the model.
* **When to use**: If the model needs the tool call results to proceed. For example, you have performed a search or called called the aggregations tool.

#### **Available Out of the Box Tools**

* **Purpose**: Dropdown to select a 'function name'. Listed here are the out of the box functions.
* **Usage**: Use as starting points for common tools.

***

## Configuration Best Practices

#### Naming Conventions

1. **IDs**: Use lowercase with underscores (`search_customer_data`).
2. **Function Names**: These need to match the underlying function name.
3. **Descriptions**: Start with action verbs ("Performs", "Retrieves", "Creates").

#### Parameter Design

1. **Required vs Optional**: Clearly define which parameters are required.
2. **Data Types**: Use appropriate types (string, number, boolean, array, object).
3. **Descriptions**: Provide clear guidance on parameter usage and format.
4. **Validation**: Include format requirements and constraints.

#### Security Considerations

1. **Access Control**: Always configure appropriate access control groups for tools that perform updates (i.e. UpdateFile).
2. **Parameter Validation**: Ensure parameters are properly validated.
3. **Sensitive Data**: Avoid exposing sensitive information in descriptions.
4. **Testing**: Thoroughly test tools before enabling in production.

***

## Validation and Testing

#### JSON Validation

1. Use the "Validate JSON" button to check syntax.
2. Use "Pretty Print JSON" to format the JSON properly.
3. Ensure all brackets and quotes are properly closed.

***

## Troubleshooting

**Tool Not Appearing**

1. Check if the tool is enabled.
2. Verify access control groups are properly configured.
3. Ensure the user has appropriate permissions.

**JSON Validation Errors**

1. Check for missing commas, brackets, or quotes.
2. Verify parameter types match expected formats.
3. Use the built-in validation tools.

**Parameter Issues**

1. Ensure required parameters are clearly marked.
2. Check parameter descriptions are clear and actionable.
3. Verify data types are appropriate for the use case.

**Performance Issues**

1. Review tool complexity and optimise if needed.
2. Consider parameter validation to reduce processing.
3. Monitor tool usage and response times.

***

## Maintenance

### Regular Tasks

1. **Review Access**: Periodically audit the access control groups.
2. **Update Descriptions**: Keep tool descriptions current and accurate.
3. **Monitor Usage**: Track which tools are being used and how often.
4. **Performance Review**: Check tool performance and optimise as needed.

### Version Control

1. Document changes when updating tools.
2. Test updates in staging environments first.
3. Maintain backups of working configurations.
4. Consider versioning for major tool updates.

***

## Support and Documentation

#### Internal Documentation

* Maintain detailed documentation for any custom tools.
  * Include use cases and examples.
  * Document any limitations or known issues.

#### User Training

* Provide training materials for end users.
  * Include examples of proper tool usage.
* Create troubleshooting guides for common issues.

#### Change Management

* Establish approval processes for tool changes.
* Communicate updates to affected users.
* Maintain change logs for audit purposes.
