# Installation Security

## Elastic Password Encryption

{% stepper %}
{% step %}
To encrypt the Elastic password in the appsettings.json run the following script in an admin PowerShell.

{% code overflow="wrap" lineNumbers="true" %}
```powershell
cd C:\InsightMaker\Utils\InsightMaker.SettingsUtilities;
.\InsightMaker.SettingsUtilities.exe encryptstring "ELASTICPASSWORD"
```
{% endcode %}
{% endstep %}

{% step %}
Enter the encrypted password into the below command and run it from an admin PowerShell.&#x20;

{% code overflow="wrap" lineNumbers="true" %}
```powershell
.\InsightMaker.SettingsUtilities.exe patch -i C:\InsightMaker\ -a "elastic.password" -v "REPLACE WITH ENCRYPTED PASSWORD";
```
{% endcode %}
{% endstep %}
{% endstepper %}

***

## Elastic Certificate Password Encryption

{% stepper %}
{% step %}
To encrypt the Elastic Certificate password that resides in the appsettings.json run the following script. This must be run in an admin PowerShell.

{% code overflow="wrap" lineNumbers="true" %}
```powershell
cd C:\InsightMaker\Utils\InsightMaker.SettingsUtilities;
.\InsightMaker.SettingsUtilities.exe encryptstring "CERTIFICATE PASSWORD";
```
{% endcode %}
{% endstep %}

{% step %}
Enter the encrypted password into the below command and run it from an admin PowerShell.

{% code overflow="wrap" lineNumbers="true" %}
```powershell
.\InsightMaker.SettingsUtilities.exe patch -i C:\InsightMaker\ -a "elastic.certificate.password" -v "REPLACE WITH ENCRYPTED PASSWORD";
```
{% endcode %}
{% endstep %}

{% step %}
To encrypt the Remote API Certificate password that resides in the appsettings.json run the following script from an admin PowerShell.

{% code overflow="wrap" lineNumbers="true" %}
```powershell
.\InsightMaker.SettingsUtilities.exe encryptstring "CERTIFICATE PASSWORD ";
```
{% endcode %}
{% endstep %}

{% step %}
Enter the encrypted password into the below command and run it from an admin PowerShell.

{% code overflow="wrap" lineNumbers="true" %}
```powershell
.\InsightMaker.SettingsUtilities.exe patch -i C:\InsightMaker\ -a "remoteApi.certificate.password" -v "REPLACE WITH ENCRYPTED PASSWORD";
```
{% endcode %}
{% endstep %}
{% endstepper %}

***

## System Secret Encryption

{% stepper %}
{% step %}
&#x20;To encrypt the System Secret Key that resides in the appsettings.json run the following script in an admin PowerShell.

* For assistance creating a random 32 character key see [https://www.random.org](https://www.random.org/).

<pre class="language-powershell" data-overflow="wrap" data-line-numbers><code class="lang-powershell"><strong>cd C:\InsightMaker\Utils\InsightMaker.SettingsUtilities; 
</strong>.\InsightMaker.SettingsUtilities.exe encryptstring "ENTER 32 RANDOM CHARS"; 
</code></pre>
{% endstep %}

{% step %}
Enter the encrypted System Secret into the below command and run it from an admin PowerShell.

{% code overflow="wrap" lineNumbers="true" %}
```powershell
.\InsightMaker.SettingsUtilities.exe patch -i C:\InsightMaker\ -a "systemSecret" -REPLACE "WITH ENCRYPTED KEY";
```
{% endcode %}
{% endstep %}
{% endstepper %}
