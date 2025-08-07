# HTML Cleaner Service

The HTML Text Cleaner service is an optional service used by the Web Sites source connector. It provides an alternative way to parse HTML into text that uses some intelligence to try and capture the main content from the web page, whilst ignoring the menus and other links around the main content.

You will need to perform some testing to ensure it captures the right content from the web sites you are crawling before using it. If it does not, then you can revert to the standard text extraction option.

## Installation <a href="#installation" id="installation"></a>

### AIModel Service <a href="#aimodel-service" id="aimodel-service"></a>

1. Open the AIModel Service.
2. Enable the 'BeautifulSoupHTMLCleaner'.

<figure><img src="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FQ9m34y7e3pDOaTliRmAh%2Fuploads%2FNn2gFjaSmM7TI2zNMwyW%2Fimage.png?alt=media&#x26;token=3b900b47-98f8-4cf6-99ff-e84882999564" alt="" width="563"><figcaption></figcaption></figure>

3. Once enabled import the new config using: `InsightMaker.IndexUtilities.exe import --ai-registration-configuration C:\tmp\ai.json`

### Source Agent <a href="#source-agent" id="source-agent"></a>

1. Open the appsettings.json file in your source agent folder.
   * Example location - 'C:\insightMaker\SourceAgent'
2. Within the advanced object add: `"webSites_HTMLCleanerService": "http://127.0.0.1:15008/"`
   * If your source agent and AIModel Service run on different hosts, use "127.0.0.1" for the AIModel Service hostname.
3. Save this file.
4. Restart your Source Agent.

### Source Config <a href="#source-config" id="source-config"></a>

1. Within the control Hub go to Configurations.
2. Select Edit on the configured websites source and go to the Source tab.
3. **Text Extraction Mode:** Select BeautifulSoup HTML Cleaner from the dropdown.
4. Save the source.
