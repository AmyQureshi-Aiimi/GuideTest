# Jobs

Jobs are used to train models and cluster documents to help improve your classification experience. Clustering jobs help to improve the accuracy of any training jobs.&#x20;

**Clustering Jobs** - Clustering jobs group files based on similarities. These groups can then be reviewed and labelled. These can then help improve the accuracy of training jobs.&#x20;

**Training Jobs -** Training jobs are used to improve the models classify documents.

***

## New Clustering Job

Clustering jobs look at the documents you picked and groups them based on what it think should go together. Once items have been clustered they can then be reviewed for accuracy within labels. This is then fed to training jobs to help them improve their accuracy.

1. Within AI Studio, select Jobs from the menu.
2. Select Clustering from the tabs.
3. Select New Job.
   * This will open the Create a New Job modal.
4. **Job Type** - Select Clustering from the dropdown list.
5. **Job Name** - Enter a name for the job.
6. **Classification** - Select the classification it is for from the dropdown.
7. **Sources** - Select the Sources that it should use from the dropdown.
8. **Query String** - Enter a Lucene string to help the job.
9. **Cluster Classified Documents** - Check this to include documents that already have classifications.&#x20;
10. Select Create Job
    * Once you have set up a job it will join a queue to complete as only one job can be run at a time.&#x20;
11. Once a clustering job is complete it will be added to the labelling areas to be checked.

***

## New Training Job

Training jobs are used to improve the models that apply classifications to your items. It takes a group of correctly classified or clustered items to learn from. It uses these items to identify common features that it can use in future to determine a classification.&#x20;

1. Within AI Studio, select Jobs from the menu.
2. Select Training from the tabs.
3. Select New Job.
   * This will open the Create a New Job modal.
4. **Job Type** - Select Training from the dropdown list.
5. **Job Name** - Enter a name for the job.
6. **Classification** - Select the classification it is for from the dropdown.
7. **Sources** - Select the Sources that it should use from the dropdown.
8. **Query String** - Enter a Lucene string to help the job.
9. **Classes to Include** - Select all the classes that should be trained using this from the dropdown.
10. **Classes to Exclude** -  Select all the classes that should **not** be trained using this from the dropdown.
11. **Status Include** - Select the statuses that should be used for training no matter the classification method.
12. **Status Exclude** - Select the statuses that should not be used for training.
13. Select Create Job.
    * Once you have set up a job it will join a queue to complete as only one job can be run at a time.&#x20;
