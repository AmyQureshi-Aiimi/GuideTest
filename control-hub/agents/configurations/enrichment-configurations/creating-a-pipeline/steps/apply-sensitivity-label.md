# Apply Sensitivity Label

You can add classifications from Aiimi Insight Engine to a file at source with Microsoft Purview. This requires Microsoft Purview to be configured by an administrator.&#x20;

### **Limitations**

* This is only possible when running Aiimi Insight Engine on Microsoft Window software.
* The labels will only apply to Microsoft Office files and PDF files. Attempts to apply these to other types of files will result in errors.

## **Prerequisites**

<details>

<summary>Permissions</summary>

It needs an app registration in the Azure tenant associated with your Purview or Office 365 environment. It must have the following permissions:

### Azure Rights Management Service

* **Content.SuperUser** - This enables content to be read when the label or policy involves encryption.
* **Content.Writer** - This enables content to be written when the label or policy involves encryption.

### Microsoft Information Protection

* **UnifiedPolicy.Tenant.Read** - This enables the tenant policy information to be read.

- The application ID and secret must have a credential within Aiimi Insight Engine.

</details>

<details>

<summary>Other Steps</summary>

This enrichment step should sit within a pipeline containing other steps.&#x20;

### Content Retrieval

As a minimum it requires a "ContentRetrieval" step to provide the files to apply labels to.

For support setting up this step [see our guide on Content Retrieval](content-retrieval.md).&#x20;

### AI Classification

The "AIClassification" step can apply classifications within Aiimi Insight Engine. These classification can then form what this step writes back to the file.

For support setting up this step [see our guide on AI Classification](ai-classification.md).

### Copy

The "Copy" step can output the newly labelled file back to a source system. If configured correctly, this can replace the source file with the labelled version.

For support setting up this step [see our guide on the Copy step.](copy.md)

</details>

## Configuration

1. **AIE Classification to Sensitivity Label ID** - Enter the mappings for the Aiimi Insight Engine classification and the Purview Sensitivity Label.
   1. Select Add New Item
   2. **Left Column** - Enter the Aiimi Insight Engine classification ID, entity or metadata field of the record.
   3. **Right Column** - Enter the GUID of the purview sensitivity label, not the name or display name.
   4. Select the tick button to add this mapping.
   5. You can select Add New Item to add another mapping. There is no limit to the number of mappings you can add.
2. **Select Credential** - Select the application ID and secret credential mentioned in the prerequisites.
3. **Application Name** - We recommend this matches the application registration configured within Azure.
4. **Tenant ID** - Enter the ID of your organisation's tenancy where the sensitivity labels are configured.
5. **Classification Source** - Select where the classification is pulled from.
   1. **Classification** - This pulls the classification from the dedicated section within each document. The classification scheme is defined in the classification scheme to read field.
      * Within the mappings at the top, the ID of the classification must be provided.
   2. **Metadata** - This pulls the classification from a metadata field. This value is defined in the Metadata field to read field.
      * To avoid confusion, these will fail if the field does not contain exactly one value.
   3. **Entity** - This pulls the classification from an entity. The entity is defined in the Entity to read field.
      * To avoid confusion, these will fail if the field does not contain exactly one value.
6. **To read** - Depending on your chosen classification source enter the relevant information.
   1. **Classification Scheme to read** - Enter the classification scheme to use.
   2. **Metadata field to read** - Enter the Metadata to use in the form "metadata.name".
   3. **Entity to read** - Select the entity to use from the list of available entities.

{% hint style="info" %}
The mappings at the top must match the values in the to read field. This will be the display value of the classification. Metadata and Entity are not as robust as classifications should a classification name change in the future.
{% endhint %}
