# Elastic and Kibana Install (Windows)

This guide walks through the steps to set up a single node Elasticsearch cluster and an instance of Kibana. It should take around 2 hours to complete the Elastic and Kibana install.&#x20;

If you are setting up a production environment, you will want to set up an Elasticsearch cluster. More information on this can be found on the ElasticSearch website.

{% hint style="info" %}
The Elastic token needed to configure Kibana is only valid for 30 minutes. Once Elastic has been extracted you have 30 minutes to Install and Configure Kibana.  It is not a long process but it's important you have that time to complete these steps.
{% endhint %}

<details>

<summary>Prerequisites</summary>

* [ ] Check what version of Elastic and Kibana is needed for the Aiimi Insight Engine vesion you are deploying. You can find this  in the release notes for your distribution.&#x20;
* [ ] Obtain your XPack Elasticsearch licence (or you can enable a trial).

- [ ] Install [Notepad++](https://notepad-plus-plus.org/) or similar text editing software.

</details>

<details>

<summary>PowerShell Hint</summary>

Your PowerShell will continue to auto scroll down as the process remains running. \
If you select and highlight a section of the prompt window the auto scroll will stop. This will make it easier to find your password and token.&#x20;

</details>

***

## Folder Structure Set Up

A specific folder structure is needed for the installation of Elasticsearch and Kibana. You can create this structure using a PowerShell query or manually.

1. To create these folders using PowerShell run the following script in an admin Powershell.

{% hint style="warning" %}
Check the storage path in this script before running it. For example: (C:\\).
{% endhint %}

{% code overflow="wrap" lineNumbers="true" %}
```powershell
mkdir C:\Apps;
mkdir C:\InsightMaker;
mkdir C:\Downloads;
mkdir C:\Utils
```
{% endcode %}

***

## Download Software

1. Download the InsightEngine zip file from the GitHub area and put it in the Downloads folder you created.
   * If you do not have access to this reach out to your Aiimi contact.
2. Right click PowerShell and select Run as Administrator.
3. Copy the following script into the PowerShell to download the the additional software needed for Elastic and Kibana.

{% hint style="warning" %}
Check the storage path and release names match the required version before running this script. For example: (C:\\), (elasticsearch-8.17.3).
{% endhint %}

{% code overflow="wrap" lineNumbers="true" %}
```powershell
Start-BitsTransfer -Source "https://nssm.cc/release/nssm-2.24.zip" -destination "C:\Downloads";
Start-BitsTransfer -Source "https://github.com/notepad-plus-plus/notepad-plus-plus/releases/download/v8.4.9/npp.8.4.9.Installer.x64.exe" -destination "C:\Downloads";
Start-BitsTransfer -Source "https://www.7-zip.org/a/7z2201-x64.exe" -destination "C:\Downloads";
Start-BitsTransfer -Source "https://artifacts.elastic.co/downloads/elasticsearch/elasticsearch-8.17.3-windows-x86_64.zip" -destination "C:\Downloads";
Start-BitsTransfer -Source "https://artifacts.elastic.co/downloads/kibana/kibana-8.17.3-windows-x86_64.zip" -destination "C:\Downloads"
```
{% endcode %}

4. Go to your downloads folder and check the files have downloaded.
   * NSSM
   * Notepad ++
   * 7-Zip
   * Elasticsearch
   * Kibana

<figure><img src="../.gitbook/assets/image (2).png" alt="" width="563"><figcaption></figcaption></figure>

### Extract Software

1. Extract Elastic, Kibana, NSSM and Insight Engine zip files by running the following script in an admin PowerShell.

{% hint style="warning" %}
Check the storage path and release names match the required version before running this script. For example: (C:\\), (elasticsearch-8.17.3).
{% endhint %}

<pre class="language-powershell" data-overflow="wrap" data-line-numbers><code class="lang-powershell">Expand-Archive -Force C:\Downloads\elasticsearch-8.17.3-windows-x86_64.zip C:\Apps;
Expand-Archive -Force C:\Downloads\Kibana-8.17.3-windows-x86_64.zip C:\Apps;
Expand-Archive -Force C:\Downloads\nssm-2.24.zip C:\Utils;
<strong>Expand-Archive -Force C:\Downloads\insightengine-win.2025.5.7.zip C:\InsightMaker
</strong></code></pre>

2. Check the files have extracted to the correct locations.
   * Elasticsearch is in the Apps folder.&#x20;
   * Kibana is in the Apps folder.
   * NSSM is in the Utils folder.&#x20;
   * There should be 13 folders within the Insight Maker folder.

***

## Configure Elastic

There are a number of configuration that need to be updated in the Elastic config file. This ensures the different paths match your system.

1. Running the following script in an admin PowerShell to update these.

{% hint style="warning" %}
Check the storage path and release names match the required version before running this script. For example: (C:\\), (elasticsearch-8.17.3).
{% endhint %}

{% code overflow="wrap" lineNumbers="true" %}
```powershell
$Filename = "C:\Apps\elasticsearch-8.17.3\config\elasticsearch.yml";
((Get-Content -path $Filename -Raw) -replace '#cluster.name: my-application','cluster.name: ') | Set-Content -Path $Filename;
((Get-Content -path $Filename -Raw) -replace '#node.name:','node.name:') | Set-Content -Path $Filename;
((Get-Content -path $Filename -Raw) -replace '#path.data: /path/to/data','path.data: C:\Apps\Data') | Set-Content -Path $Filename;
((Get-Content -path $Filename  -Raw) -replace '#path.logs: /path/to/logs','path.logs: C:\tmp\logs') | Set-Content -Path $Filename;
((Get-Content -path $Filename -Raw) -replace '#network.host: 192.168.0.1','network.host: 0.0.0.0') | Set-Content -Path $Filename;
((Get-Content -path $Filename -Raw) -replace '#discovery.seed_hosts:','discovery.seed_hosts:') | Set-Content -Path $Filename;
((Get-Content -path $Filename -Raw) -replace 'host1','0.0.0.0') | Set-Content -Path $Filename;
((Get-Content -path $Filename -Raw) -replace ', "host2"','') | Set-Content -Path $Filename;
((Get-Content -path $Filename -Raw) -replace '#cluster.initial_master_nodes:','cluster.initial_master_nodes:') | Set-Content -Path $Filename;
((Get-Content -path $Filename -Raw) -replace ', "node-2"]',']')  | Set-Content -Path $Filename
```
{% endcode %}

***

## Install Elastic

1. Install Elastic as a service by running the following PowerShell script in a new Admin PowerShell.

{% hint style="warning" %}
Check the storage path and release names match the required version before running this script. For example: (C:\\), (elasticsearch-8.17.3).
{% endhint %}

{% code overflow="wrap" lineNumbers="true" %}
```powershell
cd C:\Apps\elasticsearch-8.17.3;
.\bin\elasticsearch.bat 
```
{% endcode %}

* <mark style="color:red;">Do not close PowerShell when this script has finished.</mark>

2. This will return a password for Elastic. Make a note of this for later.
3. It will also return a token needed for the Kibana install. Make a note of this for later.

<figure><img src="../.gitbook/assets/image (897).png" alt="" width="563"><figcaption></figcaption></figure>

### Test Install

1. Test if your install worked by opening a web browser and navigating to https://localhost:9200.
2. Login in using the username 'elastic' and the password from PowerShell.
3. It should show a block of code that contains build details. It should include, Build\_flavour, build\_type, build\_hash, etc.

<figure><img src="../.gitbook/assets/image (834).png" alt="" width="375"><figcaption></figcaption></figure>

***

## Install Kibana

1. Install Kibana by running the following PowerShell script in a new Admin PowerShell.

{% hint style="warning" %}
Check the storage path and release names match the required version before running this script. For example: (C:\\), (elasticsearch-8.17.3).
{% endhint %}

{% code overflow="wrap" lineNumbers="true" %}
```powershell
cd C:\Apps\kibana-8.17.3\bin;
.\kibana.bat
```
{% endcode %}

* <mark style="color:red;">Do not close PowerShell when this script has finished.</mark>

2. Once this has finished running a URL will appear. Navigate to that URL in your browser.&#x20;
3. Copy the token you got from the Elastic PowerShell.
4. Paste it into the Enrolment token in the Kibana session.
5. Select Configure Elastic.
   * The configuration may not complete. That's not an issue at this point.
6. In your web browser, navigate to http://localhost:5601.
7. Use the Elastic credentials you used earlier to login.&#x20;

***

## Update Elastic License

1. Copy the text of your Elastic license into a Notepad++ file.
2. Save this file as Dev-license.json in the root folder.
3. Within http://localhost:5601 navigate to the Management tab on the left and select Elastic License Management.
4. Upload the Dev-license.json file to Kibana via the license manager.&#x20;
   * It is normal for this to cause an access issue in Kibana. If it doesn't, check that Elastic hasn't previously been installed in 'Programs and Features' (and remove it if it's present).

<figure><img src="../.gitbook/assets/image (837).png" alt="" width="375"><figcaption></figcaption></figure>

***

## Create Elastic Certificate

1. Open another new PowerShell as an Admin.&#x20;
   * This should be the third PowerShell you have open.

### Create the CA Cert

1. Create an Elastic ca cert by running the following script in the admin PowerShell.

{% hint style="warning" %}
Check the storage path and release names match the required version before running this script. For example: (C:\\), (elasticsearch-8.17.3).
{% endhint %}

{% code overflow="wrap" lineNumbers="true" %}
```powershell
cd C:\Apps\elasticsearch-8.17.3\bin;
.\elasticsearch-certutil ca
```
{% endcode %}

3. When prompted for an output file, leave this empty and press Enter.
   * If asked if you want to overwrite the existing file, type Y and press enter.
4. When prompted for the CA password enter a secure password.
   * This password cannot include any special characters.

### Create the Certificate

1. Create an Elastic certificate by running the following Script.

{% hint style="warning" %}
Check the storage path and release names match the required version before running this script. For example: (C:\\), (elasticsearch-8.17.3).
{% endhint %}

{% code overflow="wrap" lineNumbers="true" %}
```powershell
./elasticsearch-certutil cert -ca C:\Apps\elasticsearch-8.17.3\elastic-stack-ca.p12;
```
{% endcode %}

2. When prompted enter the CA password you just created.
3. When prompted for an output file, leave this empty and press Enter.
4. When prompted enter a password for this certificate.
   * This password cannot include any special characters and should be different to the CA password.

<figure><img src="../.gitbook/assets/Certpassprmpts.png" alt="" width="563"><figcaption></figcaption></figure>

### Copy Certificates

1. Create a new folder and move the certificates to it by running the following script.

{% hint style="warning" %}
Check the storage path and release names match the required version before running this script. For example: (C:\\), (elasticsearch-8.17.3).
{% endhint %}

{% code overflow="wrap" lineNumbers="true" %}
```powershell
mkdir C:\Apps\certs;

copy-item C:\Apps\elasticsearch-8.17.3\*.p12 -Destination C:\Apps\certs

move C:\Apps\elasticsearch-8.17.3\*.p12 C:\Apps\elasticsearch-8.17.3\config\certs
```
{% endcode %}

***

## Secure Connection Configuration

To ass Xpack security a number of configurations need to be updated. This improves the security between Kibana and Elastic.

1. To make these changes run the following script to make these changes automatically.

{% hint style="warning" %}
Check the storage path and release names match the required version before running this script. For example: (C:\\), (elasticsearch-8.17.3).
{% endhint %}

{% code overflow="wrap" lineNumbers="true" %}
```powershell
$Filename="C:\Apps\elasticsearch-8.17.3\config\elasticsearch.yml";

((Get-Content -path $Filename -Raw) -replace 'http.p12','elastic-certificates.p12') | Set-Content -Path $Filename

((Get-Content -path $Filename -Raw) -replace 'transport.p12','elastic-certificates.p12') | Set-Content -Path $Filename;

((Get-Content -path $Filename -Raw) -replace '#action.destructive_requires_name: false','action.destructive_requires_name: true') | Set-Content -Path $Filename;

(Get-Content -path $Filename) | ? {$_.trim() -ne "" } | set-content $Filename
```
{% endcode %}

***

## Setup Elastic Keystore

The certificate password is used in a number of places and needs to be updated to match the certificate password you set.

1. Run the following scripts one by one to update the passwords.

{% hint style="warning" %}
Check the storage path and release names match the required version before running this script. For example: (C:\\), (elasticsearch-8.17.3).
{% endhint %}

{% code overflow="wrap" lineNumbers="true" %}
```powershell
cd C:\Apps\elasticsearch-8.17.3\bin;
.\elasticsearch-keystore add xpack.security.transport.ssl.keystore.secure_password
```
{% endcode %}

2. If asked if you want to overwrite the existing file, type Y and press enter.
3. When prompted enter the Certificate password.
4. Run the next script

{% code overflow="wrap" lineNumbers="true" %}
```powershell
.\elasticsearch-keystore add xpack.security.transport.ssl.truststore.secure_password
```
{% endcode %}

5. If asked if you want to overwrite the existing file, type Y and press enter.
6. When prompted enter the Certificate password.
7. Run the next script

{% code overflow="wrap" lineNumbers="true" %}
```powershell
.\elasticsearch-keystore add xpack.security.http.ssl.keystore.secure_password
```
{% endcode %}

8. If asked if you want to overwrite the existing file, type Y and press enter.
9. When prompted enter the Certificate password.
10. Run the next script

{% code overflow="wrap" lineNumbers="true" %}
```powershell
.\elasticsearch-keystore add xpack.security.http.ssl.truststore.secure_password
```
{% endcode %}

11. When prompted enter the Certificate password.

***

## Configure Secure Connection

1. Update the kibana.yml file by running the following script.

{% hint style="warning" %}
Check the storage path and release names match the required version before running this script. For example: (C:\\), (kibana-8.17.3).
{% endhint %}

{% code overflow="wrap" lineNumbers="true" %}
```powershell
$Filename="C:\Apps\Kibana-8.17.3\config\kibana.yml";

((Get-Content -path $Filename -Raw) -replace '#elasticsearch.ssl.verificationMode: full','elasticsearch.ssl.verificationMode: none') | Set-Content -Path $Filename
```
{% endcode %}

2. You can now close the Elastic and Kibana PowerShell consoles.
   1. Within each console press Ctrl + C.
   2. It will then ask if you want to terminate the session. Enter Y to confirm.

<figure><img src="../.gitbook/assets/kibanasslconfig.png" alt="" width="563"><figcaption></figcaption></figure>

***

## Install Elastic Service

{% hint style="warning" %}
Check the storage path and release names match the required version before running this script. For example: (C:\\), (elasticsearch-8.17.3).
{% endhint %}

1. Run the following command in PowerShell to install the Elastic Service.

{% code overflow="wrap" lineNumbers="true" %}
```powershell
C:\Apps\elasticsearch-8.17.3\bin\elasticsearch-service.bat install
```
{% endcode %}

2. Run the following command to start the elastic service.

{% code overflow="wrap" lineNumbers="true" %}
```powershell
C:\Apps\elasticsearch-8.17.3\bin\elasticsearch-service.bat start
```
{% endcode %}

3. Open your web browser and navigate to https://localhost:9200.
   * This may take a few minutes to load for the first time.
4. Login using the Elastic credentials.

***

## Install Kibana Service

1. Run the following command in PowerShell to install the Kibana Service.

{% hint style="warning" %}
Check the storage path and release names match the required version before running this script. For example: (C:\\), (nssm-2.24).
{% endhint %}

{% code overflow="wrap" lineNumbers="true" %}
```powershell
C:\Utils\nssm-2.24\win64\nssm.exe install insightenginekibana
```
{% endcode %}

2. Select the ... browse button in the top bar.
3. Go to Apps > Kibana > Bin and select Kibana.
4. Select Install Service.
5. Run the following command in PowerShell to start the Kibana service.

{% code overflow="wrap" lineNumbers="true" %}
```powershell
C:\Utils\nssm-2.24\win64\nssm.exe start "insightenginekibana"
```
{% endcode %}

6. Open your web browser and navigate to http://localhost:5601.
   * This may take a few minutes to load the first time.
7. Login using the Elastic credentials.
