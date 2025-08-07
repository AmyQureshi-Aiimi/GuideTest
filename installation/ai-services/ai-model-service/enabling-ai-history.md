# Enabling AI History

There are a couple of things that need to be initialised in the index utilities for AI History.

1. Run the following script.

```
cd C:\InsightMaker\Utils\InsightMaker.IndexUtilities 

.\InsightMaker.IndexUtilities.exe initialise --ai-history 
```

You can check this was successful by logging into the Control Hub.

1. Go to Mappings then Models.
   * You should see an Aiimi Insight Engine group with two models within it.

***

## Configure an AI History Source

1. Go to the configurations area of the control hub.
2. Click new configuration and select source from the dropdown.

### General Tab

1. **Configuration ID:** Enter ai\_history.
2. **Configuration Description:** Enter AI History.
3. **Manage:** Under visibility uncheck manage.
4. **Mapped Data Models:** Select Aiimi Insight Engine AI from the dropdown.

<figure><img src="../../../.gitbook/assets/image (100).png" alt="" width="563"><figcaption></figcaption></figure>

### Source Tab

1. **Source System:** Select AI History from the dropdown.

### Agents Tab

1. Select the available agent from this tab.
2. Select Save

### Creating a New Empty Index

1. Once the Source Configuration is set up go to the configuration page.
2. Find the source you just configured.
3. Select the actions menu for the source.
4. Select Start.
5. This will create a new empty index that you can see in Kibana.

***

## Enabling AI History in Search Flows

1. Within the Control Hub go to Search Flows.
2. Select Edit of the Search Flow you want to add history to.
3. On the General tab
4. History Source: Select AI History from the dropdown.
5. Save the Search Flow.

<figure><img src="../../../.gitbook/assets/image (99).png" alt="" width="563"><figcaption></figcaption></figure>

***

## Troubleshooting

### Chat Hanging

If your AI chats are hanging on the second message it is likely due to a malformed AI History index.&#x20;

#### In Kibana

1. Delete the corrupt source index&#x20;
   1. For example, DELETE prod\_idx\_ai\_history\_main

#### In the Control Hub

1. Go to the Configuration page.
2. Select the AI History source config.&#x20;
3. Select the actions menu for the source.
4. Select Start.
   * This will create an empty index. You can confirm this has worked by checking in Kibana.
5. You can now start using AI History in search flows again.

### No History Written to Chatbot

After creating a new chatbot search flow and defining its AI history source you should restart the middleware with iisreset.
