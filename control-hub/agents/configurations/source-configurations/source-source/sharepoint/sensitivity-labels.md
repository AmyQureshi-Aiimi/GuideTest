# Sensitivity Labels

You can apply your classifications within Workplace AI back to Sharepoint and OneDrive using Sensitivity Labels configured in Microsoft Purview.

<details>

<summary>Prerequisites</summary>

### Microsoft Purview

This needs Microsoft Purview to have been configured by your organisation and be available for SharePoint. Purview functionality is limited to modern Microsoft Office files and PDF files. Attempts to apply these to other types of files will result in an error.

 If no other metadata updates are being applied, you may want to filter what files the   enrichment step applies to. This will help avoid unnecessary checkouts of files in SharePoint.

### Additional Permissions

The associated app registration used in your Sharepoint source configuration requires the following additional permissions:

1. Microsoft Graph: Files.ReadWrite.All
   1. This enables the update of files.
2. Microsoft Graph: InformationProtectionPolicy.Read.All
   1. This enables the application to read configured sensitivity labels.

</details>

This can be set up on existing SharePoint Configurations or new ones. However, sources must not be using the deprecated ACS approach, and must have the "Secondary" section which contains the Microsoft Graph information populated.

## Setting Up Sensitivity labels

To make the necessary changes, select or create an appropriate SharePoint source.

1. Within the SharePoint source configuration, go to the Mappings Tab.
2. Map the Workplace AI classification and SharePoint sensitivity labels together.
   1. Left Column - Enter the Workplace AI classification value.
      * This is the value that is populated in the chosen entity.
   2. Right Column - Enter the GUID of the sensitivity label in Purview.
      * It can be difficult to find the GUID for a sensitivity label so we have added a utility to the SharePoint utilities to help.

### Running the SharePoint Utility

{% hint style="info" %}
You need a SharePoint source with the "Secondary" section populated for this to work.
{% endhint %}

1. On the server, run the InsightMaker.Source.SharePointUtilities.exe (.sh on Linux) with the following argument.&#x20;
   * This will return your organisations configured labels, their unique GUID and a description for further clarification.
   * The GUID is the value to populate as the target in the mappings section described above.

{% code overflow="wrap" %}
```
InsightMaker.Source.SharepointUtilities.exe sensitivity --source-id <id of sharepoint source>
```
{% endcode %}

***

## Enrichment

You will need to add an enrichment step to write the information back to SharePoint. This process runs as a background task after making the API call. It can take a few minutes for the changes to show.

1. Add an UpdateMetadata Step to your enrichment process.
2. **Source Field Name:** Select the entity/metadata field containing the classification from the dropdown.
3. **Target System Field Name:** Enter "purview.sensitivityLabel" as the target field.
   * If run successfully, the appropriate sensitivity label should be applied within SharePoint.

For support setting up enrichments use [our guide on enrichment configurations](../../../enrichment-configurations/).
