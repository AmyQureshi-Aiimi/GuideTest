# Result Templates

Result templates allow you to format individual results that are sent to a model. You can create different templates for different sources.

1. Select New Result Template.
2. **Name** - Enter a unique name for the template.
3. **Source IDs** - Select the Source IDs this template will apply to.&#x20;
   * If no source is selected, this will become a generic template. It will be used when no other templates match the source.
4. **Extra Data to Send** - Select any extra data, entities or metadata to send to the model.
5. **Collapse Whitespace** - Check this to remove white space from things like tables or new lines.
   * This should only be checked if newlines do not convey meaning to the model.&#x20;
6. **Template** - Enter a template to use when passing the results to a model.&#x20;
   * The template uses Python style string formatting, for example {index} {name}: {textContent}.

<figure><img src="../../../.gitbook/assets/image (20).png" alt="" width="563"><figcaption></figcaption></figure>

#### Template standard data items

* {index} - The 1 based index of the result in the list of results sent.
* {id} - The ID of the result.
* {sourceId} - The source ID for the result.
* {sourceDescription} - The description of the source.
* {name} - The name of the result.
* {textContent} - The text content of the result.
* {createDate} - The create date for the result.
* {modifiedDate} - The modified date for the result.
* {uri} - The URI for the result.

#### Extra Data - This always takes the form:

* Entities - {metadata\[entities.entityGroup.entityId]}
* Metadata - {metadata\[metadata.entityId]}
* Data - {metadata\[data.modelId.attributeId]}

The use of metadata\[....] is historic and does not imply just metadata, but includes data and entities.

