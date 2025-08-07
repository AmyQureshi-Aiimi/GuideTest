# Collection

## Get Collection Types

Pulls back all configured collection types as CollectionType objects&#x20;

{% code overflow="wrap" lineNumbers="true" %}
```python
SearchAPI.get_collection_types(raw=False) 
```
{% endcode %}

<table><thead><tr><th width="100.0531005859375">Name</th><th width="100.05291748046875">Type</th><th>Description</th></tr></thead><tbody><tr><td>raw </td><td>boolean </td><td>If true, this function returns the JSON response as a dictionary, not a CollectionType object. Default is false. </td></tr></tbody></table>

***

## Search Collections&#x20;

Searches all collections, returning a list of Collection objects. All matching collection objects up to the max\_results parameter (visible to the user) will be returned regardless of page size parameter value.&#x20;

{% code overflow="wrap" lineNumbers="true" %}
```python
SearchAPI.search_collections(query_string="*", start_page_num=1, page_size=20, max_results=0, raw=False) 
```
{% endcode %}

***

## Get Collection&#x20;

Used to retrieve a specific collection as a Collection object.&#x20;

{% code overflow="wrap" lineNumbers="true" %}
```python
SearchAPI.get_collection(collection_id, raw=False) 
```
{% endcode %}

<table><thead><tr><th width="124.79766845703125">Name</th><th width="99.74951171875">Type</th><th>Description</th></tr></thead><tbody><tr><td>collection_id </td><td>string </td><td>ID of collection to return </td></tr><tr><td>raw </td><td>boolean </td><td>If true, this function returns the JSON response as a dictionary, not a CollectionType object. Default is false. </td></tr></tbody></table>

***

## Delete Collection&#x20;

Used to delete a collection by ID.&#x20;

{% code overflow="wrap" lineNumbers="true" %}
```python
SearchAPI.delete_collection(collection_id) 
```
{% endcode %}

<table><thead><tr><th width="124.76861572265625">Name</th><th width="99.93988037109375">Type</th><th>Description</th></tr></thead><tbody><tr><td>collection_id </td><td>string </td><td>ID of collection to delete </td></tr></tbody></table>

***

## New Collection&#x20;

Used to create a new collection, returns the created collection as a Collection object.&#x20;

{% code overflow="wrap" lineNumbers="true" %}
```python
SearchAPI.new_collection(name, description="", collection_type="general-collection") 
```
{% endcode %}

<table><thead><tr><th width="140.4744873046875">Name</th><th width="100.3055419921875">Type</th><th>Description</th></tr></thead><tbody><tr><td>name </td><td>string </td><td>Name for new collection </td></tr><tr><td>description </td><td>string </td><td>Optional, description for collection </td></tr><tr><td>collection_type </td><td>string or CollectionType </td><td>Collection type to use, defaults to "general-collection", which will always be available. </td></tr></tbody></table>

***

## Add to Collection&#x20;

Adds a document to a collection.&#x20;

{% code overflow="wrap" lineNumbers="true" %}
```python
SearchAPI.add_to_collection(collection, dataset, document_id) 
```
{% endcode %}

<table><thead><tr><th width="125.06365966796875">Name</th><th width="99.9066162109375">Type</th><th>Description</th></tr></thead><tbody><tr><td>collection </td><td>string or collection </td><td>Collection to add to </td></tr><tr><td>dataset </td><td>string or dataset </td><td>Dataset containing document (either string dataset ID or a Dataset object) </td></tr><tr><td>document_id </td><td>string </td><td>ID of document to add </td></tr></tbody></table>

***

## Add Collection Permissions&#x20;

Used to add additional user permissions to collections.

{% code overflow="wrap" lineNumbers="true" %}
```python
SearchAPI.add_collection_permissions(collection, permissions, users)
```
{% endcode %}

<table><thead><tr><th width="124.82586669921875">Name</th><th width="99.8426513671875">Type</th><th>Description</th></tr></thead><tbody><tr><td>collection </td><td>string or Collection </td><td>Collection to add to </td></tr><tr><td>permissions </td><td>string or integer </td><td>“remove”, “read”, “write”, “delete” or appropriate corresponding integer value </td></tr><tr><td>users </td><td>list of string </td><td>List of qualified usernames to add these permissions for </td></tr></tbody></table>

***

## Get User&#x20;

Used to get details about an AIE user as a SearchUser object.

{% code overflow="wrap" lineNumbers="true" %}
```
SearchAPI.get_user(user_id="me", raw=False) 
```
{% endcode %}

<table><thead><tr><th width="125.0902099609375">Name</th><th width="100.1605224609375">Type</th><th>Description</th></tr></thead><tbody><tr><td>user_id </td><td>string </td><td>ID of user to pull (defaults to “me”, which returns the authenticated user) </td></tr><tr><td>raw </td><td>boolean </td><td>If true, this function returns the JSON response as a dictionary, not a SearchUser object. Default is false. </td></tr></tbody></table>

***

## Get Settings&#x20;

Used to return the Workplace AI settings dictionary, which can be used to determine various things about the configured system, including details on search flows, configured DSAR and disclosure settings, theming etc.&#x20;

{% code overflow="wrap" lineNumbers="true" %}
```
SearchAPI.get_settings()
```
{% endcode %}

***

## Download&#x20;

Used to directly download a document from AIE, this is returned in python as a BytesIO object.&#x20;

{% code overflow="wrap" lineNumbers="true" %}
```
SearchAPI.download(dataset, document_id) 
```
{% endcode %}

<table><thead><tr><th width="124.734375">Name</th><th width="99.8587646484375">Type</th><th>Description</th></tr></thead><tbody><tr><td>dataset </td><td>string or Dataset </td><td>Dataset containing document (either string dataset ID or a Dataset object) </td></tr><tr><td>document_id </td><td>string </td><td>ID of document to download </td></tr></tbody></table>

***

## Collection Objects&#x20;

The Collection class is a Python representation of a collection object, typically obtained through the SearchAPI wrapper. This class provides a structured way to interact with collections, allowing users to manage files, permissions, and other attributes associated with a collection. Below is a detailed overview of each class and its functionality.&#x20;

### Attributes&#x20;

`collectionType`\
An instance of CollectionType, representing the type of the collection.&#x20;

`search_api`\
An optional SearchAPI instance for performing operations.&#x20;

### Methods&#x20;

`type()`\
Returns the type of the collection.&#x20;

`name()` \
Returns the name of the collection.&#x20;

`str()` \
Returns a string representation of the collection in the format collection:\<name>.&#x20;

`to_dict()` \
Returns a dictionary representation of the collection, including files, file entries, and permissions.&#x20;

`files()` \
Returns a copy of the list of files associated with the collection.&#x20;

`file_entries()` \
Returns a copy of the file entries associated with the collection.&#x20;

`permissions()` \
Returns a copy of the permissions associated with the collection.&#x20;

`update(search_api=None)` \
Updates the collection's data using the provided search\_api instance or the instance stored in the object.&#x20;

* **Parameters:**&#x20;
  * `search_api` (optional): An instance of SearchAPI to fetch the latest collection data.&#x20;
* **Raises:**&#x20;
  * Exception: If no SearchAPI instance is provided.&#x20;

`delete(search_api=None)` \
Deletes the collection using the provided search\_api instance or the instance stored in the object.&#x20;

* **Parameters:**&#x20;
  * `search_api` (optional): An instance of SearchAPI to perform the deletion.&#x20;
* **Raises:**&#x20;
  * Exception: If no SearchAPI instance is provided.&#x20;

`add_document(dataset, document_id, search_api=None)`\
Adds a document to the collection.&#x20;

* **Parameters:**&#x20;
  * `dataset`: The dataset to which the document belongs. This can be an instance of Dataset or a dataset ID.&#x20;
  * `document_id`: The ID of the document to be added.&#x20;
  * `search_api` (optional): An instance of SearchAPI to perform the operation.&#x20;
* **Raises:**&#x20;
  * Exception: If no SearchAPI instance is provided.&#x20;
* **Notes:**&#x20;
  * If the document is already in the collection, a warning is printed and the operation is not performed again.&#x20;

`add_permissions(permissions, users, search_api=None)` \
Adds permissions for specified users to the collection.&#x20;

* **Parameters:**&#x20;
  * `permissions`: The permissions to be added, which can be a string ("read", "write", "delete", or "remove") or an integer.&#x20;
  * `users`: A list of users to whom the permissions will be granted.&#x20;
  * `search_api` (optional): An instance of SearchAPI to perform the operation.&#x20;
* **Raises:**&#x20;
  * Exception: If no SearchAPI instance is provided.&#x20;
  * ValueError: If the permissions are not valid.&#x20;
* **Notes:**&#x20;
  * The method first removes the specified users from all permission types and then adds them according to the specified permissions.&#x20;

`parse_permissions(permissions)` \
A static method to parse permissions from a string or integer.&#x20;

* **Parameters:**&#x20;
  * `permissions`: The permissions to be parsed, which can be a string or an integer.&#x20;
* **Returns:**&#x20;
  * An integer representing the parsed permissions.&#x20;
* **Raises:**&#x20;
  * ValueError: If the permissions are not valid.&#x20;

`create_new(search_api, name, description="", collection_type="general-collection")` \
A static method to create a new collection.&#x20;

* **Parameters:**&#x20;
  * `search_api`: An instance of SearchAPI to perform the operation.&#x20;
  * `name`: The name of the new collection.&#x20;
  * `description` (optional): A description for the new collection.&#x20;
  * `collection_type` (optional): The type of the collection, defaulting to "general-collection".&#x20;
