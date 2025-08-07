# OData API

## Connect the OData API

1. Within Global Settings of the control hub select OData API.
2. Enter the URL for the API in API URL.
   * This is configured when the API is built.

<figure><img src="../../.gitbook/assets/image (719).png" alt="" width="563"><figcaption></figcaption></figure>

***

## OData Entity Sets

The entity sets for the OData API determine what a query will search. You much configure the name used during the search and the field within Workplace AI that relates to.

### Create an Entity Set

1. Within Global Settings of the control hub select OData API.
2. Select New Entity Set.
   * This will open up the create entity set modal.

### General Settings

1. Enter a Unique Name for the entity set.
2. Select Source and check each source it will use from the dropdown.
3. Enter the maximum number of results that should be returned in Max Results.
   * When no $top is in a query this is the maximum number of results a query using this entity set can return.
   * By default this will be set to 100.
   * This number must be less than 10,000 or elastic will limit the results returned.
4. Select Continue.
   * This will take you to the fields section.

<figure><img src="../../.gitbook/assets/image (720).png" alt="" width="563"><figcaption></figcaption></figure>

#### Field Settings

1. Enter a Name for this field within the data set.
   * This name must be unique across all entity sets.
2. Select a Field to add to the data set from the dropdown.
   * You can choose a generic field or a metadata or entity field from the sources selected.
3. If you select a Metadata or entity field a single value field checkbox will appear.
   * Check this to only return one value for this field even if there are multiple available. If left unchecked the query will return all the results in an array.
4. Once a field is selected the type will populate with Keyword, Boolean, Double etc.
5. Select Add to Set.
6. Each field will appear in a table below. You can add as many fields as you want to an entity set.
   * You can delete or edit fields in an entity set from this table using the Edit and Delete buttons.
7. Once you've added all your fields select Create Entity Set.
   * This will return you to the main OData API page.

<figure><img src="../../.gitbook/assets/image (721).png" alt="" width="563"><figcaption></figcaption></figure>

6. Select Restart API to create these endpoints.
   * This will open a confirmation modal.
   * A restart may take a few minutes. While the API restarts users will have no access to the API.

<figure><img src="../../.gitbook/assets/image (719).png" alt="" width="563"><figcaption></figcaption></figure>

### User Access

Users must be authenticated in the control hub before they can use this API. Users must have a configured API key. Follow our Editing User Access guide to set this up.

Users need their API key to use and create queries for this API. Admins can get API keys from the control hub.

1. Within User Settings of the control hub.
2. Find the user you want to edit.
   * Search for a user within the search bar or, Select Show Filters and use the filters to narrow down users.
   * To edit multiple users at once, check the checkbox to the left of their name.
3. To get the API Key select the Key (key icon) and select Generate API Key.
   * This key is valid until revoked.
   * API keys are only available when first created. If it is lost or deleted, a new one will need to be generated.

<figure><img src="../../.gitbook/assets/image (722).png" alt=""><figcaption></figcaption></figure>

