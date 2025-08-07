# Entities, Metadata and Data

You can manipulate entities, metadata and data within an enrichment step. You will need to make sure you assign the right data types to the respective field, and you can inspect the type of a field in Control Hub.

<figure><img src="../../../.gitbook/assets/image (639).png" alt=""><figcaption></figcaption></figure>

Ensure that you create your respective entity, metadata, or data model property before you try and manipulate them in an enrichment pipeline.

### Entities

To add entities:

```
workItem.File.Entities["entities.test.code"] = new HashSet<string> { "fulmsp", "nelgsp" };
```

### Metadata

To add metadata:

```
work.File.Metadata["metadata.people"] = new HashSet<string> { "Paul", "Keith" }; 
```

### Data Models

To add values to data models:

```
work.File.Data["data.model_id.person"] = "Paul Maker";
```

