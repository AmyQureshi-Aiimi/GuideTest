# Job Agent

The job agent runs index backups and scripts required for Workplace AI to run smoothly. It also runs the notification agent, recommendation engines and some machine learning services.

[View our guide to configuring a Job](../../../control-hub/agents/configurations/job-configurations/).

Jobs are run on a schedule using a CRON style syntax. Most jobs will sit on the same server as other agents unless the job agent is doing something resource dependent.&#x20;

### Executable or Script Logic

It can run customer specific logic as an executable or a script. The script must be written in a language like Python or a Windows Power Shell script.

The following job types are able to run any executable or script:

1. CommandJob
2. ElasticJob
3. PurgeJob
4. TextContentMergeJob

<figure><img src="../../../.gitbook/assets/image (431).png" alt=""><figcaption></figcaption></figure>

