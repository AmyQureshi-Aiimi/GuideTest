# Getting SAR data from Google Vault

When gathering data for a SAR that can also include data from a Google Vault not connected to Workplace AI as a Source.

### Creating a Job for Google

A Job must be configured to run periodically for Workplace AI to gather information from Google. This must be configured with Control Hub.

Complete 5 simple steps to set up a Google Vault Job Configuration.

1. Complete the General tab. [See our guide to Job Configuration - General Tab.](../../agents/configurations/job-configurations/general.md)
2. Complete the Job tab for a Google Vault Jobs. [See our guide to Job Configuration - Google Vault SAR.](../../agents/configurations/job-configurations/job/googlevaultsar.md)
3. Complete the Output tab. [See our guide to Job Configuration - Output Tab](../../agents/configurations/job-configurations/output.md).
4. Complete the Agents tab. [See our guide to Job Configuration - Agents Tab.](../../agents/configurations/job-configurations/agents.md)
5. Complete the Schedule tab. [See our guide to Job Configuration - Schedule Tab.](../../agents/configurations/job-configurations/scheduling.md)

### How does the Google Vault SAR work?

1. A job will run periodically checking for in progress SARs within Workplace AI.
2. All search terms from in progress SARs are prepared for the Google Vault SAR Job.
3. The Google Vault SAR job will run and Workplace AI will turn the search terms into "Matter" within Google Vault.
4. The "Matter" is then used to search in Google Vault for related results.
5. Any found results will be exported to your designated SAR Import destinations source.
6. These file are also added to the relevant SAR document lists.

Any files added to a SAR from Google Vault in this way can be exported and disclosed like all other documents.
