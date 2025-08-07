# Update

`POST insightmaker/ds/document/<dataset>/<id>`\
id is the document ID to be updated.

#### **Body**

{% code overflow="wrap" lineNumbers="true" %}
```
{
	"metadata.a": "value a",
	"models.b": "value b"
}
```
{% endcode %}

{% hint style="info" %}
The keys must be fully qualified InsightMaker properties, starting with entities, metadata or models (or nothing if core) and the property must be correctly configured in control hub.
{% endhint %}

#### **Response**

Blank 200 response if successful. A value of none will erase a property.
