# Email Threading Upgrade

You can allow emails to be grouped and collapsed and remove duplicates using email threading. These are the steps to setup and configure email threading as part of an upgrade to Habanero or newer.

These steps need to be applied to all sources regardless of whether they are structured or unstructured data sources.&#x20;

{% hint style="danger" %}
If installing Aiimi Insight Engine Habanero or later, for the first time ignore these steps.&#x20;
{% endhint %}

The Habanero release introduced two new elastic fields that are required for email threading.

#### CollapseID

The default CollapseID is `{prefix}_{source}_{id}_{version}`. This is automatically populated by Aiimi Insight Engine at crawl time. The fields combined ensure every item has a unique collapseID even if it appears in multiple sources.

#### DeduplicationID

deduplicationID is only applied for Exchange and Mimecast sources. For Mimecast, Exchange and the File Extractor, deduplicationID is populated with the internet message ID of the email at crawl time. It reduces the number of times the same email, in different mailboxes, is displayed in Aiimi Insight Engine.

For emails in all other sources, the value will default to the unique\_value and will need to be populated by Tika.

***

## Upgrading Aiimi Insight Engine

After upgrading to Habanero  or later there are a few upgrade steps required to apply the default collapseID to existing sources.

{% hint style="info" %}
Check the path of all commands to ensure they match your installation before you run them.
{% endhint %}

1. Open PowerShell as an admin.
2. Run the following command

```
cd C:\InsightMaker\Utils\InsightMaker.IndexUtilities
```

3. Run the following command to create an Alias for future commands.

<pre data-overflow="wrap"><code><strong>New-Alias -Name im-utils -Value C:\InsightMaker\Utils\InsightMaker.IndexUtilities\InsightMaker.IndexUtilities.exe -ErrorAction SilentlyContinue
</strong></code></pre>

4. Run the following command to create the mapping.

```
im-utils map -s
```

5. Run the following command to test the source.
   * Replace \<id> with the source name.

```
im-utils collapse --set-default --source-id <id>
```

6. Open Kibana Dev Tools.
7. Run the following command to check the collapse id has applied correctly.
   * Update the index name to match the source you used above.

{% code overflow="wrap" lineNumbers="true" %}
```
GET dev_idx_changeme_main/_search
{
  "track_total_hits": true,
  "collapse": {
    "field": "collapseId",
    "inner_hits": {
      "name": "collapsed_results",
      "size": 10
    }
  },
  "sort": [ { "createdDate": "desc" } ],
  "size": 10
}
```
{% endcode %}

8. If this has worked the collapseID should appear in the elastic index.

If the results are correct, apply the collapseID to the remaining sources. The following command loops through all the sourceID's and applies the collapseID command.

9. Within PowerShell run the following command to apply the collapseID to other sources.
   * This command uses the alias created earlier to find all the sources.

{% code overflow="wrap" lineNumbers="true" %}
```
foreach ($index in im-utils list)
{
  im-utils collapse --set-default --source-id $index
}
```
{% endcode %}

***

## Exchange and Mimecast Only

After the upgrade, all emails will have a unique collapseID applied and the old method of viewing emails should still work. For Exchange and Mimecast sources an enrichment needs to be run to populate the deduplicationID and threadIDs.&#x20;

### Enrichment Configuration for Email Threading

See our Enrichment Configuration [guide for help creating a new enrichment.](../control-hub/agents/configurations/enrichment-configurations/)

#### Required Steps

1. ContentRetrieval
2. TikaText extractor
3. Text Cleaner

#### Content Retrieval

1. Retrieve Content - Set to Always
   * This will ignore any content that already exists.

<figure><img src="../.gitbook/assets/image (53).png" alt="" width="412"><figcaption></figcaption></figure>

#### Tika Text Extractor

This can be left as default.

#### Text Cleaner

1. Cleaning Process - Select Remove Blank Lines.
   * This removes any empty lines.

<figure><img src="../.gitbook/assets/image (54).png" alt="" width="412"><figcaption></figcaption></figure>

***

## Control Hub Email Threading Configuration

1. Once the enrichment is complete go to Control Hub> Search Settings > Search Performance.
2. Group Emails - Check this to Group Emails from a conversation together in a thread.
   * Enabling this will impact your search performance.
   * If not ticked, emails will behave as they did previously, no grouping or collapsing and all results including duplicate will be displayed.

<figure><img src="../.gitbook/assets/image (55).png" alt="" width="412"><figcaption></figcaption></figure>

***

## Testing

1. Login to the Aiimi Insight Engine search application.
2.  In the search enter one of the following:

    `_exists_:metadata.isParent`&#x20;

    * This will show all results where an attachment exists.

    `_exists_:collapseId`&#x20;

    * This will show all results where a collapseId exists

    `_exists_:metadata.conversationId`

    * This will show all emails results where a conversationId exists
3. Selecting a result will either open the inline or full screen preview.
4. Instead of displaying one email it will show the email chain. Any attachments in the email chain will be added to the bottom of the preview results.
5. Navigate through the chain by expanding the related results on the right hand side.

