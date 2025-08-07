# Managing a Bulk Search

All current bulk searches will be displayed in a table within the control hub. The table contains the search Owner, Name, Number of searches, Search terms, number of users it is shared with and its status. There is no limit to the number of searches you can add to a bulk search. The only limitation is the number of results that can be returned. This is limited to 10,000 results.

All bulk searches can be turned on and off or deleted by and admin from this table. By default all searches will be enabled.&#x20;

<details>

<summary>Prerequisites</summary>

**Job Configuration**\
Bulk search requires an Automated Search Job to be configured. If there are any bulk searches configured and enabled it will automatically pick them up. You can configure how frequently this job is run and the agent it uses from the Job configuration.&#x20;

As bulk searches can be resource heavy we recommend this job suns when no other jobs are.&#x20;

_For support setting up a Job_ [see our guide on creating a job configuration.](../../agents/configurations/job-configurations/)

</details>

## Disable or Enable a Bulk Search

If enabled the bulk search will run on the same schedule as other saved searches.&#x20;

If disabled the user will still see the search in their table but it will not run on a schedule.

You may want to disable searches for a number of reasons:\
\- Large searches as they could slow down your system. \
\- Inappropriate or sensitive terms.\
\- Users who have left the business.

1. Within Workplace AI Control Hub select Global Settings.
2. Select Bulk Search.
3. Within the table find the bulk search you are looking for. You can find for a bulk search using the search bar.&#x20;
4. Select the status toggle to switch the status.
5. Select Update at the top of the page to save any changes.

<figure><img src="../../../.gitbook/assets/image (742).png" alt=""><figcaption></figcaption></figure>

## Deleting a Bulk Search

If a search is deleted from here it will also be deleted from the users bulk search list. This will delete the Search and any related Notifications for all Users.

1. Within Workplace AI Control Hub select Global Settings.
2. Select Bulk Search.
3. Within the table find the bulk search you are looking for. You can find for a bulk search using the search bar.&#x20;
4. Select Delete Bulk Search from in the row of the item you want to delete.
   * This will open a confirmation modal.
5. Select Yes to confirm the deletion of this search.&#x20;

## Job Management

### Job Logs

You can find detailed logs for failed and passed bulk search jobs. They are stored on the server the job is run on under **C:\tmp\logs**. There will be a text file named **insightmaker.jobagent.log** within this.

If you notice a job has failed, you can restart it from the Configurations area of the Control Hub. Find the job from the Job table, Select the options button and select start from the menu.

### Changing a bulk search&#x20;

The bulk search job gets all the CSVs it needs to process before the job begins. If a user edits their settings or CSV while the job is running the changes will not be applied. The changes will be applied and used in the next search.

### CSV Storage

The CSVs uploaded by users are converted to elastic queries so do not require dedicated storage. When a user downloads their CSV, it is actually being built by elastic on demand. So, no CSV is ever stored only a representation of it in Elastic which is used when the job agent excutes.
