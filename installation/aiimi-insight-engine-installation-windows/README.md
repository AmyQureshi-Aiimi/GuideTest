# Workplace AI Installation (Windows)

This is a guide for setting up a simple single node Workplace AI instance on Windows 2016 or later.&#x20;

{% hint style="info" %}
If you are designing and installing a production environment you will be installing individual agents and components on specific nodes. Further guidance on this can be provided on request.&#x20;
{% endhint %}

<details>

<summary>Prerequisites</summary>

* Obtain your Workplace AI licence from Aiimi.

- Download and Install .NET SDK [(v8.0)](https://dotnet.microsoft.com/en-us/download/dotnet/8.0).

* Download and Install the .NET Core and Hosting Bundle [(v9.0)](https://learn.microsoft.com/en-us/aspnet/core/host-and-deploy/iis/hosting-bundle?view=aspnetcore-9.0\&preserve-view=true).
  * This is used to run InsightEngine agents and middleware as well as host web components.
* .NET Core and Hosting bundle (.NET installs used to run InsightMaker agents and middleware as well as host web components)&#x20;

If you installed Elasticsearch and Kibana previously you may already have the following downloads.

* Install [Notepad++](https://notepad-plus-plus.org/) or similar text editing software.
* Download and install [NSSM ](https://nssm.cc/download)to run the Tika Agent as a service
* Download your Workplace AI distribution. _Your Aiimi contact can help you with this if you don't have it._
* Download the Tika file in the Workplace AI distribution.

</details>

## Download Software

{% hint style="info" %}
The following guide assumes everything is being stored in the C: drive. You can use any drive but we recommend installing to the root of it.
{% endhint %}

1. Check your Workplace AI distribution is extracted into C:\InsightMaker
   * If not, download the insightmaker-windows.zip from GitHub.

<figure><img src="../../.gitbook/assets/image (142).png" alt="" width="563"><figcaption></figcaption></figure>

2. Extract the zip file to C:\InsightMaker using the following code in an Admin PowerShell.

<pre class="language-powershell" data-overflow="wrap" data-line-numbers><code class="lang-powershell"><strong>Expand-Archive -Force C:\Downloads\insightmaker-win*.zip C:\InsightMaker
</strong></code></pre>

3. Download the redistributables and dotnet bundle by running the following code in an Admin PowerShell.

<pre class="language-powershell" data-overflow="wrap" data-line-numbers><code class="lang-powershell"><strong>Start-BitsTransfer -Source "https://aka.ms/vs/17/release/vc_redist.x86.exe" -destination "C:\Downloads";
</strong>Start-BitsTransfer -Source "https://aka.ms/vs/17/release/vc_redist.x64.exe" -destination "C:\Downloads";
Start-BitsTransfer -Source "https://builds.dotnet.microsoft.com/dotnet/aspnetcore/Runtime/8.0.16/dotnet-hosting-8.0.16-win.exe" -destination "C:\Downloads"
</code></pre>

***

## Prepare Files

1. Run the following script in an admin PowerShell window. These commands stop Windows silently blocking files.

{% hint style="warning" %}
Check the storage path in this script before running it. For example: (C:\\).
{% endhint %}

{% code overflow="wrap" lineNumbers="true" %}
```powershell
gci C:\InsightMaker\Plugins\*.dll | Unblock-File;
gci C:\InsightMaker\Scripts\*.ps1 | Unblock-File
```
{% endcode %}

2. Update the Agent file names by running the following Script in an admin PowerShell.

{% hint style="warning" %}
Check the storage path in this script before running it. For example: (C:\\).
{% endhint %}

{% code overflow="wrap" lineNumbers="true" %}
```powershell
$Filename = "C:\InsightMaker\ContentAgent";
Copy-Item -Path "$filename\appsettings.default.json" -Destination "$filename\appsettings.json" -Force;
Copy-Item -Path "$filename\log4net.default.config" -Destination "$filename\log4net.config" -Force;

$Filename = "C:\InsightMaker\EnrichmentAgent";
Copy-Item -Path "$filename\appsettings.default.json" -Destination "$filename\appsettings.json" -Force;
Copy-Item -Path "$filename\log4net.default.config" -Destination "$filename\log4net.config" -Force;

$Filename = "C:\InsightMaker\JobAgent";
Copy-Item -Path "$filename\appsettings.default.json" -Destination "$filename\appsettings.json" -Force;
Copy-Item -Path "$filename\log4net.default.config" -Destination "$filename\log4net.config" -Force;

$Filename = "C:\InsightMaker\MigrationAgent";
Copy-Item -Path "$filename\appsettings.default.json" -Destination "$filename\appsettings.json" -Force;
Copy-Item -Path "$filename\log4net.default.config" -Destination "$filename\log4net.config" -Force;

$Filename = "C:\InsightMaker\OCRAgent";
Copy-Item -Path "$filename\appsettings.default.json" -Destination "$filename\appsettings.json" -Force;
Copy-Item -Path "$filename\log4net.default.config" -Destination "$filename\log4net.config" -Force;

$Filename = "C:\InsightMaker\SecurityAgent";
Copy-Item -Path "$filename\appsettings.default.json" -Destination "$filename\appsettings.json" -Force;
Copy-Item -Path "$filename\log4net.default.config" -Destination "$filename\log4net.config" -Force;

$Filename = "C:\InsightMaker\SourceAgent";
Copy-Item -Path "$filename\appsettings.default.json" -Destination "$filename\appsettings.json" -Force;
Copy-Item -Path "$filename\log4net.default.config" -Destination "$filename\log4net.config" -Force;
```
{% endcode %}

3. Update the App File names by running the following Script in an admin PowerShell.

{% hint style="warning" %}
Check the storage path in this script before running it. For example: (C:\\).
{% endhint %}

{% code overflow="wrap" lineNumbers="true" %}
```powershell
$Filename = "C:\InsightMaker\Apps\Admin\Api";
Copy-Item -Path "$filename\appsettings.default.json" -Destination "$filename\appsettings.json" -Force;
Copy-Item -Path "$filename\log4net.default.config" -Destination "$filename\log4net.config" -Force;
Copy-Item -Path "$filename\web.default.config" -Destination "$filename\web.config" -Force

$Filename = "C:\InsightMaker\Apps\Admin\app";
Copy-Item -Path "$filename\web.default.config" -Destination "$filename\web.config" -Force;

$Filename = "C:\InsightMaker\Apps\search\api";
Copy-Item -Path "$filename\appsettings.default.json" -Destination "$filename\appsettings.json" -Force;
Copy-Item -Path "$filename\log4net.default.config" -Destination "$filename\log4net.config" -Force;
Copy-Item -Path "$filename\web.default.config" -Destination "$filename\web.config" -Force;

$Filename = "C:\InsightMaker\Apps\web\api";
Copy-Item -Path "$filename\web.default.config" -Destination "$filename\web.config" -Force;

$Filename = "C:\InsightMaker\Utils\InsightMaker.IndexUtilities";
Copy-Item -Path "$filename\appsettings.default.json" -Destination "$filename\appsettings.json" -Force;
Copy-Item -Path "$filename\log4net.default.config" -Destination "$filename\log4net.config" -Force;

$Filename = "C:\InsightMaker\Utils\InsightMaker.Security.BuiltinSecurityUtilities";
Copy-Item -Path "$filename\appsettings.default.json" -Destination "$filename\appsettings.json" -Force;
Copy-Item -Path "$filename\log4net.default.config" -Destination "$filename\log4net.config" -Force;
```
{% endcode %}

***

## Aiimi Insight Configurations

1. Update your AppSettings Json file by running the following script in an admin PowerShell.

{% hint style="warning" %}
Check the storage path and update it where it says "Text input" with the relevant information. Ensure the following information is input correctly:

1. Elastic Certificate Password, Elastic password, Elastic Prefix, RemoteApi Certificate Password, License Key and License Signature.
   1. Your license signature should be a unique value for this system.
   2. Your license signature must be encrypted.
{% endhint %}

<pre class="language-powershell" data-overflow="wrap" data-line-numbers><code class="lang-powershell">cd C:\InsightMaker\Utils\InsightMaker.SettingsUtilities;
<strong>.\InsightMaker.SettingsUtilities.exe patch -i C:\InsightMaker\ -a "elastic.certificate.path" -v "C:\Apps\certs\elastic-stack-ca.p12";
</strong><strong>.\InsightMaker.SettingsUtilities.exe patch -i C:\InsightMaker\ -a "elastic.certificate.password" -v "Text input";
</strong><strong>.\InsightMaker.SettingsUtilities.exe patch -i C:\InsightMaker\ -a "elastic.password" -v "Text input";
</strong>.\InsightMaker.SettingsUtilities.exe patch -i C:\InsightMaker\ -a "elastic.prefix" -v "Text input";
.\InsightMaker.SettingsUtilities.exe patch -i C:\InsightMaker\ -a "elastic.server" -l "https://localhost:9200";
.\InsightMaker.SettingsUtilities.exe patch -i C:\InsightMaker\ -a "plugins.locations" -l "C:\InsightMaker\Plugins"
.\InsightMaker.SettingsUtilities.exe patch -i C:\InsightMaker\ -a "remoteApi.certificate.path" -v "C:\Apps\certs\elastic-certificates.p12";
.\InsightMaker.SettingsUtilities.exe patch -i C:\InsightMaker\ -a "remoteApi.RemoteAddress" -v "https://localhost";
.\InsightMaker.SettingsUtilities.exe patch -i C:\InsightMaker\Apps\Admin\api -a "remoteApi.RemoteAddress" -v "https://localhost/admin/api";
.\InsightMaker.SettingsUtilities.exe patch -i C:\InsightMaker\Apps\Search\api -a "remoteApi.RemoteAddress" -v "https://localhost/api";
.\InsightMaker.SettingsUtilities.exe patch -i C:\InsightMaker\ -a "remoteApi.certificate.password" -v "Text input";
.\InsightMaker.SettingsUtilities.exe patch -c -i C:\InsightMaker\ -a "licenseKey" -v "Text input";
.\InsightMaker.SettingsUtilities.exe patch -c -i C:\InsightMaker\ -a "licenseSig" -v "Text input";
</code></pre>

***

## Json Web Token Config

1. Update your JWT config key by running the following script in an admin PowerShell.

{% hint style="warning" %}
Check the path of the storage location in this script and update it where it says "Text input" with the relevant information.

* The JWT configuration key must be at least 32 characters.
  * For assistance creating a random 32 character key see [https://www.random.org](https://www.random.org/).
{% endhint %}

{% code overflow="wrap" lineNumbers="true" %}
```powershell
.\InsightMaker.SettingsUtilities.exe patch -i C:\InsightMaker\ -a "jwtConfiguration.Key" -v "Text input"; 
```
{% endcode %}

***

## Configure Log File Storage

Each agent has a log4net.default.config file. This file defines the path for the log directory. This is C:\tmp\logs by default.&#x20;

1. Update the logs into their own subfolders by running the following script in an admin PowerShell.

{% hint style="warning" %}
Check the storage path in this script before running it. For example: (C:\\). **Don’t output the log files to the InsightMaker folder.**
{% endhint %}

{% code overflow="wrap" lineNumbers="true" %}
```powershell
$Filename = "C:\InsightMaker\ContentAgent\log4net.config";
((Get-Content -path $filename -Raw) -replace 'c:/tmp/logs/InsightMaker.ContentAgent.log','C:/tmp/logs/agents/InsightMaker.ContentAgent.log') | Set-Content -Path $filename;

$Filename = "C:\InsightMaker\EnrichmentAgent\log4net.config";((Get-Content -path $filename -Raw) -replace 'c:/tmp/logs/InsightMaker.EnrichmentAgent.log','C:/tmp/logs/agents/InsightMaker.EnrichmentAgent.log') | Set-Content -Path $filename;

$Filename = "C:\InsightMaker\JobAgent\log4net.config";
((Get-Content -path $filename -Raw) -replace 'c:/tmp/logs/InsightMaker.JobAgent.log','C:/tmp/logs/agents/InsightMaker.JobAgent.log') | Set-Content -Path $filename;

$Filename = "C:\InsightMaker\MigrationAgent\log4net.config";
((Get-Content -path $filename -Raw) -replace 'c:/tmp/logs/InsightMaker.MigrationAgent.log','C:/tmp/logs/agents/InsightMaker.MigrationAgent.log') | Set-Content -Path $filename;

$Filename = "C:\InsightMaker\OCRAgent\log4net.config";
((Get-Content -path $filename -Raw) -replace 'c:/tmp/logs/InsightMaker.OCRAgent.log','C:/tmp/logs/agents/InsightMaker.OCRAgent.log') | Set-Content -Path $filename;

$Filename = "C:\InsightMaker\SecurityAgent\log4net.config";
((Get-Content -path $filename -Raw) -replace 'c:/tmp/logs/InsightMaker.SecurityAgent.log','C:/tmp/logs/agents/InsightMaker.SecurityAgent.log') | Set-Content -Path $filename;
```
{% endcode %}

2. Update the remaining logs into their own subfolders by running the following script in an admin PowerShell.

{% code overflow="wrap" lineNumbers="true" %}
```powershell
$Filename = "C:\InsightMaker\SourceAgent\log4net.config";
((Get-Content -path $filename -Raw) -replace 'c:/tmp/logs/InsightMaker.SourceAgent.log','C:/tmp/logs/agents/InsightMaker.SourceAgent.log') | Set-Content -Path $filename;

$Filename = "C:\InsightMaker\Apps\Search\api\log4net.config";
((Get-Content -path $filename -Raw) -replace 'c:/tmp/logs/InsightMaker.Middleware.search.log','C:/tmp/logs/agents/InsightMaker.Middleware.search.log') | Set-Content -Path $filename;

$Filename = "C:\InsightMaker\Apps\Admin\api\log4net.config";
((Get-Content -path $filename -Raw) -replace 'c:/tmp/logs/InsightMaker.Middleware.Admin.log','C:/tmp/logs/InsightMaker.Middleware.Admin.log') | Set-Content -Path $filename;

$Filename = "C:\InsightMaker\Utils\InsightMaker.IndexUtilities\log4net.config";
((Get-Content -path $filename -Raw) -replace 'c:/tmp/logs/InsightMaker.IndexUtilities.log','C:/tmp/logs/InsightMaker.IndexUtilities.log') | Set-Content -Path $filename;

$Filename = "C:\InsightMaker\Utils\InsightMaker.Security.BuiltinSecurityUtilities\log4net.config";
((Get-Content -path $filename -Raw) -replace 'c:/tmp/logs/InsightMaker.Security.BuiltinSecurityUtilities','C:/tmp/logs/InsightMaker.Security.BuiltinSecurity.log') | Set-Content -Path $filename;
```
{% endcode %}

***

## Initialise Control Hub Parameter

1. To initialise Control Hub run the following script from an admin PowerShell.&#x20;
   * These commands configure the default elastic mappings for InsightEngine indices and create some useful default entities etc.

{% hint style="warning" %}
Check the path of the storage location in this script before running it. For example: (C:\\).
{% endhint %}

{% code overflow="wrap" lineNumbers="true" %}
```powershell
cd C:\InsightMaker\Utils\InsightMaker.IndexUtilities;
.\InsightMaker.IndexUtilities.exe map
.\InsightMaker.IndexUtilities.exe initialise -fmsci
.\InsightMaker.IndexUtilities.exe initialise --collection-types;
.\InsightMaker.IndexUtilities.exe initialise --theme;
.\InsightMaker.IndexUtilities.exe upgrade --generate-entity-groups;
```
{% endcode %}

***

## Agent Services

1. Run the following script in an admin PowerShell to create the agents needed.

{% hint style="warning" %}
Check the path of the storage location in this script before running it. For example: (C:\\).
{% endhint %}

{% code overflow="wrap" lineNumbers="true" %}
```powershell
cd C:\InsightMaker\Utils\InsightMaker.IndexUtilities; 
 
sc.exe create InsightMakerContentAgent binPath= C:\InsightMaker\ContentAgent\InsightMaker.ContentAgent.exe DisplayName= "InsightMaker Content Agent" start= auto; 
 
sc.exe create InsightMakerEnrichmentAgent binPath= C:\InsightMaker\EnrichmentAgent\InsightMaker.EnrichmentAgent.exe DisplayName= "InsightMaker Enrichment Agent" start= auto; 
 
sc.exe create InsightMakerJobAgent binPath= C:\InsightMaker\JobAgent\InsightMaker.JobAgent.exe DisplayName= "InsightMaker Job Agent" start= auto; 
 
sc.exe create InsightMakerMigrationAgent binPath= C:\InsightMaker\MigrationAgent\InsightMaker.MigrationAgent.exe DisplayName= "InsightMaker Migration Agent" start= auto; 
 
sc.exe create InsightMakerOcrAgent binPath= C:\InsightMaker\OcrAgent\InsightMaker.OcrAgent.exe DisplayName= "InsightMaker Ocr Agent" start= auto; 
 
sc.exe create InsightMakerSecurityAgent binPath= C:\InsightMaker\SecurityAgent\InsightMaker.SecurityAgent.exe DisplayName= "InsightMaker Security Agent" start= auto;  
 
sc.exe create InsightMakerSourceAgent binPath= C:\InsightMaker\SourceAgent\InsightMaker.SourceAgent.exe DisplayName= "InsightMaker Source Agent" start= auto; 
```
{% endcode %}

### Update Descriptions

1. Run the following Commands in an admin PowerShell to update the descriptions for these agents.

{% code overflow="wrap" lineNumbers="true" %}
```powershell
sc.exe description InsightMakerContentAgent "InsightMaker Content Agent"; 
 
sc.exe description InsightMakerEnrichmentAgent "InsightMaker Enrichment Agent"; 
 
sc.exe description InsightMakerJobAgent "InsightMaker Job Agent"; 
 
sc.exe description InsightMakerMigrationAgent "InsightMaker Migration Agent"; 
 
sc.exe description InsightMakerOcrAgent "InsightMaker Ocr Agent"; 
 
sc.exe description InsightMakerSecurityAgent "InsightMaker Security Agent"; 
 
sc.exe description InsightMakerSourceAgent "InsightMaker Source Agent"; 
```
{% endcode %}

***

## Install Tika

1. Move the Tika server file using the following command in an admin PowerShell.

{% hint style="warning" %}
Check the path of the storage location and release names match the required version before running this script. For example: (C:\\), (tika-server-standard-3.1.0).
{% endhint %}

{% code overflow="wrap" lineNumbers="true" %}
```powershell
mkdir C:\Utils\Tika; 
copy-item "C:\InsightMaker\Tika\tika-server-standard-3.1.0.jar" -Destination "C:\Utils\Tika"; 
```
{% endcode %}

2. Create a run-tika.bat using the following command in Admin PowerShell.
   * If your Elasticsearch is stored in a folder with spaces in the name, the Java path will need to be in quotation marks.

{% hint style="warning" %}
Check the path of the storage location and release names match the required version before running this script. For example: (C:\\), (tika-server-standard-3.1.0).
{% endhint %}

{% code overflow="wrap" lineNumbers="true" %}
```powershell
'"C:\Apps\elasticsearch-8.17.3\jdk\bin\Java" -jar C:\\Utils\Tika\tika-server-standard-3.1.0.jar' | Out-File -FilePath C:\Utils\Tika\run-tika.bat -encoding ascii; 
```
{% endcode %}

3. Create the Tika service using the following commands in an admin PowerShell.
   * This will open an NSSM service installer modal.

{% hint style="warning" %}
Check the path of the storage location in this script before running it. For example: (C:\\).
{% endhint %}

{% code overflow="wrap" lineNumbers="true" %}
```powershell
C:\Utils\nssm-2.24\win64\nssm.exe install InsightMakerTika; 
```
{% endcode %}

4. **Path:** Select the ... button and point this field to C:Utils\Tika\run-tika.bat.
   * We recommend you don't copy and paste the file path.
5. **Startup Directory:** Select the ... button and point this field to C:Utils\Tika.
   * We recommend you don't copy and paste the file path.

<figure><img src="../../.gitbook/assets/image (862).png" alt="" width="401"><figcaption></figcaption></figure>

{% hint style="info" %}
If you want to run Tika without installing it from powershell navigate to the Tika folder. Run the `.\run-tika.bat serve` file. This can help you to identify any issues which are less obvious when going straight for the install.
{% endhint %}

6. Start the Tika service by running the following command in an admin PowerShell.

{% code overflow="wrap" lineNumbers="true" %}
```powershell
C:\Utils\nssm-2.24\win64\nssm.exe start InsightMakerTika;
```
{% endcode %}

### Check Tika Services

1. Check the status of Tika by navigating to http://localhost:9998 in your browser.
   * It should great you with "Welcome to the Apache Tika X.X.X-SNAPSHOT Server".

<figure><img src="../../.gitbook/assets/image (105).png" alt="" width="563"><figcaption></figcaption></figure>

***

## IIS Configuration

{% hint style="danger" %}
The '.NET Core and HostingBundle' must be installed before you continue. If not, the middleware will not be able to run in IIS.
{% endhint %}

1. Enable IIS by running the following command in an admin PowerShell.

{% code overflow="wrap" lineNumbers="true" %}
```powershell
Enable-WindowsOptionalFeature -Online -FeatureName IIS-WebServerRole, IIS-WebServer, IIS-CommonHttpFeatures, IIS-ManagementConsole, IIS-HttpErrors, IIS-HttpRedirect, IIS-WindowsAuthentication, IIS-StaticContent, IIS-DefaultDocument, IIS-HttpCompressionStatic, IIS-DirectoryBrowsing 
```
{% endcode %}

2. Create a self-signed certificate using the following commands in an admin PowerShell.
   * This is used later and can be updated for production builds.

{% code overflow="wrap" lineNumbers="true" %}
```powershell
$newcert = New-SelfSignedCertificate -dnsname "InsightEngine20" -KeyLength 2048 -CertStoreLocation cert:\LocalMachine\My -NotAfter (Get-Date).AddYears(20) 
```
{% endcode %}

3. Create new https (443) bindings and remove http (80) bindings using the following commands in an admin PowerShell.

{% code overflow="wrap" lineNumbers="true" %}
```powershell
New-WebBinding -Name "Default Web site" -IP "*" -Port 443 -Protocol https
Get-WebBinding -Port 80 -Name "Default Web Site" | Remove-WebBinding
```
{% endcode %}

### IIS Application Pools Setup

1. Create a new application pool using the following commands in Admin PowerShell.

{% code lineNumbers="true" %}
```powershell
$newAppPool = New-WebAppPool -Name "Admin";
$newAppPool.autoStart = "true";
$newAppPool | Set-Item;
```
{% endcode %}

2. There are a number of application that need to be added using the following commands in Admin PowerShell.

{% code overflow="wrap" lineNumbers="true" %}
```powershell
Import-Module WebAdministration;

Set-ItemProperty "IIS:\Sites\Default Web site" -name physicalPath -value "C:\InsightMaker\Apps\Search\app";
New-WebApplication -Name "API" -Site "Default Web Site" -PhysicalPath "C:\InsightMaker\Apps\Search\api" -ApplicationPool "DefaultAppPool";
New-WebApplication -Name "Admin" -Site "Default Web Site" -PhysicalPath "C:\InsightMaker\Apps\Admin\app" -ApplicationPool "Admin";
New-WebApplication -Name "Admin\api" -Site "Default Web Site" -PhysicalPath "C:\InsightMaker\Apps\Admin\api" -ApplicationPool "Admin";
```
{% endcode %}

### IIS Assign Certificate to Binding

This sets up the default website on the server. It means it can be accessed using 'localhost' in any browser and the other apps using their alias. For example admin is accessed using localhost/admin.

1. Ensure the account that IIS runs under has read access to your Elasticsearch certificates.
2. Open IIS and navigate to the Default web site.

<figure><img src="../../.gitbook/assets/image (103).png" alt="" width="563"><figcaption></figcaption></figure>

3. Select Bindings from Edit Site within the actions bar.&#x20;
4. Select port 443 and Edit.

<figure><img src="../../.gitbook/assets/image (104).png" alt="" width="563"><figcaption></figcaption></figure>

5. **SSL certificate:** Select the new certificate you created.
6. Access the following link to check this is set up correctly. [https://localhost/#/login ](https://localhost/#/login)
   * If you see a blank screen it's possible that IIS didn't set up correctly. You may need to restart IIS.

***

## Password Encryption

We recommend you encrypt your build. For help encrypting your build [see our Installation Security area](installation-security.md) and return to this guide.

***

## Restart Agent Services

1. Restart all the agent services using the following commands in Admin PowerShell.

{% code overflow="wrap" lineNumbers="true" %}
```powershell
restart-service InsightMakerContentAgent;
restart-service InsightMakerEnrichmentAgent;
restart-service InsightMakerJobAgent;
restart-service InsightMakerMigrationAgent;
restart-service InsightMakerOcrAgent;
restart-service InsightMakerSecurityAgent;
restart-service InsightMakerSourceAgent;
iisreset;
```
{% endcode %}

***

## Accessing Control Hub

1. Navigate to [http://localhost/admin](http://localhost/admin).
2. Login with the elastic username and password generated or that you created.
3. Assuming you can login, you should see your agents on the configuration page. They will all be empty.

***

## Installing OData API (Optional)

1. Navigate to C:/Insightmaker/Apps/OData.
2. Open appsettings.default.json in a source code editor like NotePad++.
3. Check the details are correct:
   * The Plugins path points to the plugins folder. _Likely C:\InsightMaker\Plugins_
   * The elastic certificate path points to the elastic-stack-ca.p12 file. This was created when you installed Elasticsearch.
   * The correct password is set.
   * The Elasticsearch credentials are set to the elastic login you created.
   * The prefix is set to the correct value and consistent across all components.
4. Add your two Workplace AI licences to the root of the json:
   * "licenseKey": "your key"
   * "licenseSig": "your sig"
5. Check the remoteAddress is set to ‘[http://localhost/analytics/‘](http://localhost/analytics/).
6. Save this file, do not change the name or location.
7. Within C:/Insightmaker/Apps/OData open log4net.default.config.
8. Change the file paths to where you’d like log files to save.
   * This can not be the in InsightMaker folder.
9. Save this file, do not change the name or location.
10. Remove the '.default' from each of the following file names:
    * 'appsettings.default.json'
    * 'log4net.default.config'
    * 'web.default.config'
11. Open the web.config file.
    * Check the module is modules="AspNetCoreModuleV2".
12. Open Internet Information Services (IIS)
13. Open the dropdown on the left and Right click on default website.
14. Click add new application, call the alias “analytics”.
15. Set the physical path to the ‘API’ folder in InsightMaker/Apps/OData.
    * You should be able to view the OData metadata document using localhost/analytics/odata/$metadata.
