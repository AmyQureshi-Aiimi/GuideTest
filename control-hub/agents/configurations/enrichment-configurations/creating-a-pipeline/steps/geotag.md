# Geotag

This step adds Geotags to data and documents using a lookup feature. If you add Geotags you can then view information in our Map view along with using Geotag queries.

{% hint style="info" %}
Geotagging requires you to set up a lookup index.
{% endhint %}

## Create a Geotag

1. **Index that contains geopoint lookups:** Enter the index name or select an index from the dropdown that contains your lookups.&#x20;
   * This is created by the InsightMaker.GeotagIndexLoader.

### Entity or Data Model Lookup

#### **Using an Entity for lookup**

1. **Entity to use for lookup:** From the dropdown select the entity that contains the lookup value.

#### **Using a Data Model for lookup**

1. **Data Model ID to use for lookup:** From the dropdown select the data model ID that contains the lookup value.
2. **Model Attribute to use for lookup:** From the dropdown select the model attribute for this lookup.

### **Geopoint Storage Settings**

#### **Entity Store**

1. **Entity to store geopoint:** From the dropdown select what entities these geopoints will be stored against.

#### Data Model Store

1. **Data Model ID to use to store geopoint:** From the dropdown select the data model these geopoints will be stored against.
2. **Metadata field to use to store geopoint:** From the dropdown select the specific metadata field these geopoints will be stored against.

### Advanced Options

1. Select Show Advanced Options
2. Define the maximum number of items to process concurrently in Bounded Capacity.
3. Define the maximum number of items that can be queued.&#x20;

{% hint style="info" %}
Limiting either of these will reduce the memory use but increase the time taken.
{% endhint %}
