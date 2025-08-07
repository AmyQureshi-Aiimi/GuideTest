# Archiving a SAR

The SAR lifecycle is an automated process for removing SAR data. You can determine the type of data that is removed and when. This process only runs for completed or cancelled requests.

{% hint style="warning" %}
This feature must be enabled by an administrator to use it.
{% endhint %}

## Lifecycle Settings

Manage what data is removed and when. The settings can be adjusted by anyone who can access the SAR application and apply to all SARs.

1. Within the SAR application, go to Settings.
2. Then select Lifecycle settings.
   * This will show you the settings currently applied to SARs.
3. To change any of these select Edit Settings.
4. For each Response Data type select the dropdown to change the 'Remove After' length.
   * When a closed or Cancelled SAR reaches the selected time the specific data will be removed.

{% hint style="info" %}
The data must be removed in the order it is shown in the list.\
For example: Collected items can't be 6 months and Latest Disclosure 5 months. You can set them both to 6 months, or set Collected Items to 6 months and Latest Disclosure to 7 months.
{% endhint %}

5. Select Save

### Response Data Types

There are 4 types of response data that can be removed at different points of time.

* **Collected Items** - This includes the original, marked up and finalised items within a SAR no matter the status.
  * Items added via search are only removed from the SAR. Imported items are removed from the SAR and the System.
* **Latest Disclosure** - This includes the disclosed items and cover letter.
* **Data Subject Details** - This includes any names, contact information, addresses for the subject and third parties, response labels, response descriptions and disclosure manifests.
* **Response Metadata** - This includes all subject agnostic metadata; response start dates, due dates and extension dates.

***

## Disclosure Manifests

Requests that have not gone through the final stage of the lifecycle have the disclosure manifest available. You can download the manifest from the SARs activities tab.
