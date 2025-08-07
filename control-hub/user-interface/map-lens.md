# Map Lens

The Map Lens provides users with a view of their data and document results on a map. Items must have geopoints enabled within your models and entities to show in the maps lens.

{% hint style="danger" %}
If you are upgrading to the Primo release or later you will need to update your models and entities to match your previous attribute list.
{% endhint %}

## General Configuration

1. **Maximum Search Results** - Define the maximum number of results that can be returned on a map.
   * The default for this is 1000.
   * A large number of results can cause performance issues.&#x20;
2. **Maximum Geo-Points per Result** - Define the maximum points that will be plotted on the map for each result.
   * If a result has multiple locations attributed to it this field determines how many of these points could be used.&#x20;
   * The default for this is 50.

<figure><img src="../../.gitbook/assets/image (757).png" alt="" width="563"><figcaption></figcaption></figure>

***

## Map Lens Attributes

{% hint style="danger" %}
If you are upgrading to the Primo release you will need to update your models and entities to match your previous attribute list.
{% endhint %}

The attributes used for the map lens come from the published models, entities and metadata geo-point attributes.

These are determined in your models and entities. To set these up see [our guide for setting up a model](../mappings/models/create-a-new-model.md#attributes) or [our guide to setting up an entity](../mappings/entities/create-an-entity.md#details).

***

## Tile Server

1. **Tile Server API** - Enter the address of the API.&#x20;
   * For a production set up you may need to host your own tile server to avoid throttling. Your own provider must be compatible with Leaflet.js.
   * You can reach out to Aiimi for support with this.
2. **Tile Providers Attribution Text** - Enter any attribution text that may be required.
   * This will appear at the bottom of the map.&#x20;
   * By default this will be `&copy <a href="https://www.openstreetmap.org/copyright">OpenStreetMap</a>`

<figure><img src="../../.gitbook/assets/image (303).png" alt="" width="563"><figcaption></figcaption></figure>
