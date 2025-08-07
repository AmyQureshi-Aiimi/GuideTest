# Enabling Providers

There are several steps to enable providers.

{% hint style="info" %}
We are working to replace these steps with a user interface in Control Hub.
{% endhint %}

## **Export**

1. Navigate to the utils folder in your Workplace AI installation.
   * On a a multi-server enrichment, you can pick any where Index Utils are set up.
2. Navigate to `InsightMaker.IndexUtils`
3. Export your AI Registration Configuration using the following command: `InsightMaker.IndexUtilities.exe export --ai-registration-configuration C:\tmp\ai.json`
4. Open the export in an editor.
5. Find the AI Model Service for the relevant host name.
6. Enable the steps and optional models you want to use.

<figure><img src="../../../.gitbook/assets/image (176).png" alt="" width="563"><figcaption><p>AI Model Service Export</p></figcaption></figure>

7. Once enabled import the new config using: `InsightMaker.IndexUtilities.exe import --ai-registration-configuration C:\tmp\ai.json`
8. Re-start the AI Enrichment Service.
   * You should see a log like the example below.
   * Depending on the steps enables the models may take a while to download.

<figure><img src="../../../.gitbook/assets/image (177).png" alt=""><figcaption><p>Models Loading</p></figcaption></figure>
