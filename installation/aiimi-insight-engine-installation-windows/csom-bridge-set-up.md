# CSOM Bridge Set Up

{% hint style="warning" %}
This is for Windows Only.
{% endhint %}

The CSOM Bridge is for Windows applications only. It hosts a REST API that connects Workplace AI systems written in .NET to on-premises SharePoint instances. The SharePointLegacy source requires the CSOM Bridge service to be a proxy that make calls to SharePoint.

{% hint style="info" %}
If you require the CSOM Bridge to be deployed on a dedicated host please speak to your Aiimi contact.
{% endhint %}

<details>

<summary>Prerequisites</summary>

1. The latest version of .NET Framework 4.8 must be installed.
2. Workplace AI must be installed.

</details>

## Installation

### SharePoint

In order to query site collections, CSOM extensions must be installed on the SharePoint server. For help installing these [see Microsoft's guide on New CSOM API for Sharepoint Servers](https://learn.microsoft.com/en-gb/archive/blogs/sharepointdevelopersupport/new-csom-api-for-sharepoint-server-2016-tenant-getsiteproperties).

### Workplace AI

1. Open the appsettings.json file for CSOMBridge
   * \<IM\_ROOT>\Utils\InsightMaker.CSOMBridge\appsettings.json
   * The CSOM Bridge does not connect to Elastic or use plugins. It only needs a RemoteAPI section and system secret.
2. Set the CSOM Bridge port to use.
   * By default this is set to port 2227. It is secured using the internal elastic-certificates.p12 HTTPS certificate.
3. Set the systemSecret to match the rest of your system.
4. Save and close the appsettings.json file.
5. Open the log4net.config file for CSOMBridge
   * \<IM\_ROOT>\Utils\InsightMaker.CSOMBridge\log4net.config
   * You should check the file location and set the logging settings for your requirements.&#x20;
6. Save and close the log4net.config file.

### CSOM

NSSM must be used to host the bridge, do not use the EXE service install commands.

{% hint style="info" %}
Before using any scripts in this guide, please update the root folder to match your file structure.
{% endhint %}

1. Open an Administrator Command Prompt or PowerShell.
2. Run the following script to install the CSOMBridge.

{% code overflow="wrap" lineNumbers="true" %}
```
run %PATH_TO_NSSM%\nssm.exe install InsightMakerCSOMBridge
```
{% endcode %}

3. Set the Application path to `<IM_ROOT>\Utils\InsightMaker.CSOMBridge\InsightMaker.CSOMBridge.exe`
4. Set the Startup Directory to `<IM_ROOT>\Utils\InsightMaker.CSOMBridge\`
5. The name must include "CSOMBridge".
   1. This allows upgrade scripts to start/stop it correctly.&#x20;
6. The remaining parameters can be set as required.
7. Select Install Service.
8. Within the Windows Service Area start this service.

### Sharepoint Legacy Source

Configure a SharePointLegacy source to connect to the on-premises SharePoint. For support setting this up use [our guide on setting up new sources.](../../control-hub/agents/configurations/source-configurations/source-general.md)

1. The "REST Endpoint" should point to the CSOM Bridge's remote API address.
2. Within the Source Config the "Process without Delta Tokens?" must be enabled.
