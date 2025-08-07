# SAR Archiving

This job looks for Completed or cancelled SARs within Workplace AI. It then compares them to the lifecycle settings configured. As a SAR reaches a specific time the job will remove the relevant response data from the SAR.

{% hint style="info" %}
You must enable SAR lifecycle archiving within SAR settings. [For help turning SAR Archiving on see our SAR Import Guide.](../../../../global-settings/sar/importing-data-for-a-sar.md)

Users with SAR Configuration Access are able to edit the lifecycle settings. [For help managing users access to this see our guide on SAR Access.](../../../../global-settings/sar/sar-configuration-access.md)
{% endhint %}

#### Lifecycle Data Options

The lifecycle timings are configured within the SAR application. See our SAR archiving Guide for help defining the lifecycles.

**Collected Items** - This includes the original, marked up and finalised items within a SAR no matter the status.

* Items added via search are only removed from the SAR. Imported items are removed from the SAR and the System.

**Latest Disclosure** - This includes the disclosed items and cover letter.

**Data Subject Details** - This includes any names, contact information, addresses for the subject and third parties, response labels, response descriptions and disclosure manifests.

**Response Metadata** - This includes all subject agnostic metadata; response start dates, due dates and extension dates.

## Configuring the Job

1. **Job Type** - Select SAR Archiving from the dropdown list.
   * There are no specific fields required for this job.

