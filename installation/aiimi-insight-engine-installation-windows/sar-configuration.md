# SAR Configuration

To have SARs on your Workplace AI system there are a few things that need to be set up.&#x20;

## Extract Disclosure Portal Zips

1. Extract the ‘disclosure-portal.zip’ folder to C:\ &#x20;
   * The paths should be:
     * C:\DisclosurePortal\admin-api&#x20;
     * C:\DisclosurePortal\client-api&#x20;
     * C:\DisclosurePortal\client-app&#x20;

## Initialise SAR Collection

1. Within the Control Hub go to Mappings, Models.
2. Under the Collection Business Area check if the dsarCollection exists.
3. Initialise it by running the following commands on the Workplace AI server:&#x20;

{% code overflow="wrap" lineNumbers="true" %}
```powershell
cd C:\InsightMaker\Utils\InsightMaker.IndexUtilities\ 

.\InsightMaker.IndexUtilities.exe initialise --dsar --publish 
```
{% endcode %}

This will create the model, publish it, and populate default values for objects such as Subject Types, Universal Policies etc.&#x20;

## Privacy Portal Certificate

### Configuring IIS

1. Open the Internet Information Services (IIS).
2. Right click Sites then Add Website.
   1. **Site name:** PrivacyPortal (or similar, useful name)&#x20;
   2. **Physical path:** C:\DisclosurePortal\client-app&#x20;
   3. **Binding:**&#x20;
      * **Type:** https (not http)&#x20;
      * **IP address:** All Unassigned&#x20;
      * **Port:** 444 (Usually on Port 443 unless on the same server)&#x20;
      * **SSL certificate:** InsightEngine20&#x20;
3. Click OK
4. Right Click on PrivacyPortal then Add Application.
   1. **Alias:** api&#x20;
   2. **Physical path:** C:\DisclosurePortal\client-api
5. Click OK
6. Click Admin
7. Under Management select Configuration Editor
8. **Section:** Select system.webServer  > serverRuntime
9. **uploadReadAheadSize:** Change to **2147483647**
10. Select apply
11. Select admin again
12. Under the IIS Section select SSL Settings
13. Enable Require SSL and select Require under client certificates.

### Generate root and child certificates

If deploying on a separate web server to Workplace AI, copy the folder ‘C:\InsightMaker\scripts’ to the server.

If deploying on the same server as AIE, simply use the existing ‘C:\InsightMaker\scripts’ folder.

1. Create folder ‘certs’ under C:\DisclosurePortal&#x20;
2. Open PowerShell as an Administrator.
3. Run the following command

{% code overflow="wrap" lineNumbers="true" %}
```powershell
C:\InsightMaker\scripts\create-root-child-certs.ps1 
```
{% endcode %}

4. Confirm the certificate files exist under C:\DisclosurePortal\certs\\
5. Right click root.crt and select Install Certificate
6. Select Local Machine then Next.
7. Select 'Place all certificates in the following store'.
8. Click Browse and select ‘Trusted Root Certification Authorities’.&#x20;
9. Click OK, then Next and Finish.

#### Deploying on a separate web server to Workplace AI

1. Copy the Elastic cert ‘elastic-certificiates.p12’ file to the server under C:\DisclosurePortal\certs\\
   * e.g. C:\Apps\elasticsearch-8.11.1\config\certs\elastic-certificates.p12&#x20;
2. Copy the cert file ‘child.pfx’ to the Workplace AI server (or AIE web app AND agents servers, if multi-server deployment).

#### Deploying on the same server as Workplace AI

1. Use the existing ‘elastic-certificates.p12’ path and password.

## Delete Configuration Files

### Log4net.config

1. Rename the **log4net.default.config** files within \client-api and \admin-api to **log4net.config**.
2. Open \client-api\log4net.config in Notepad++ (or similar application).
3. Update the **file** value on line 4 to a valid location.
   * e.g.  C:/tmp/logs/DisclosurePortal/ (_the log name in the file_).&#x20;
4. Save and close&#x20;
5. Repeat steps 1 to 4 for the ‘\admin-api\log4net.config’ file.

### Web.config

1. Rename the **web.default.config** files within \client-api and \admin-api to **web.config**.

### Appsettings.json

{% hint style="info" %}
If you are deploying on a separate web server to Workplace AI, copy the folder ‘C:\InsightMaker\Plugins’ to the server.
{% endhint %}

1. Rename the **appsettings.default.json** files within \client-api and \admin-api to **appsettings.json**.
2. Open \client-api\appsettings.json in Notepad++ (or similar application).
   1. Set the plugins.locations to C:\\\InsightMaker\\\Plugins (line 10).
   2. Set the disclosureSettingsPath to C:\\\DisclosurePortal\\\disclosuresettings.json.
   3. Set the disclosureRoot to C:\\\tmp\\\disclosures.
3. Create an empty file called disclosuresettings.json and save this within C:\DisclosurePortal\\.
4. Create a folder path of C:\tmp\disclosures\\.
5. Save and close.
6. Create a folder path of C:\tmp\RequestStore\\.
7. Create a file called verificationStore.json and save this within C:\tmp\\.&#x20;
   1. Set the contents of this file to:

{% code overflow="wrap" lineNumbers="true" %}
```json
{ 

  "Requests": {} 

} 
```
{% endcode %}

12. Save and close.
13. Open ‘\admin-api\appsettings.json’ in Notepad&#x20;
    1. Set the disclosureSettingsPath to ‘C:\\\DisclosurePortal\\\disclosuresettings.json’.
    2. Set the disclosureRoot to ‘C:\\\tmp\\\disclosures’.
    3. Set the plugins.locations to ‘C:\\\InsightMaker\\\Plugins’ (line 6).
    4. Set the remoteApi.certificate.path to ‘C:\\\DisclosurePortal\\\certs\\\elastic-certificates.p12’&#x20;
       * (or the existing path of ‘elastic-certificates.p12’ if deploying on the same server as Workplace AI)
    5. Set the remoteApi.certificate.password value to the password of ‘elastic-certificates.p12’&#x20;
14. Save and close&#x20;

## Installing .NET Hosting Bundle

#### Deploying on a separate web server to Workplace AI

1. Download .NET Hosting Bundle 8.x from [https://dotnet.microsoft.com/en-us/download/dotnet/8.0](https://dotnet.microsoft.com/en-us/download/dotnet/8.0) (actual version number may vary from screenshot)

<figure><img src="../../.gitbook/assets/image (868).png" alt="" width="375"><figcaption></figcaption></figure>

2. Run ‘dotnet-hosting-8.0.xx-win.exe’&#x20;
   * It's important that the Hosting Bundle is installed after IIS has been installed and enabled.&#x20;
3. Perform an iisreset.
4. Browse to [https://localhost:444/#/login](https://localhost:444/#/login)&#x20;
   1. jsonThe login screen should be displayed.

## Configure Insight Engine Agents and APIs

1. For the Admin and Search API’s and Content and Job Agents, open ‘appsettings.json’ in Notepad.
   * Admin API (e.g. C:\InsightMaker\Apps\Admin\api\appsettings.json)&#x20;
   * Search API (e.g. C:\InsightMaker\Apps\Search\api\appsettings.json)&#x20;
   * ContentAgent (e.g. C:\InsightMaker\ContentAgent\appsettings.json)&#x20;
   * JobAgent (e.g. C:\InsightMaker\JobAgent\appsettings.json)&#x20;
2. Add/update the advanced.disclosureClientCertificate section with the correct path to ‘child.pfx’ and its password:

<pre class="language-json" data-overflow="wrap" data-line-numbers><code class="lang-json">"advanced": { 
    "redactionLicencedKey": "See Agreement", 
    "disclosureClientCertificate": { 
<strong>      "path": "C:\\DisclosurePortal\\certs\\child.pfx", 
</strong><strong>      "password": "changeme" 
</strong><strong>    } 
</strong>  } 
</code></pre>

3. Restart IIS where Search and Admin are deployed, and restart the Job and Content agents.&#x20;
