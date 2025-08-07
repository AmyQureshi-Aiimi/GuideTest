# Certificates in a Key Vault

You can use a Key Vault to store and manage passwords (or secrets) and certificates. This reduces any risk associated with storing and sensitive information on a local filesystem. At the moment we only support Azure Key Vault, this means we are unable to support password protected certificates.

Credentials and certificates stored within the Control Hub Credentials are not impacted by this.

{% hint style="info" %}
When loading certificates from an Azure key vault, they cannot be password protected as the password is removed by the vault.  When loading a certificate from the filesystem, it can be password protected.
{% endhint %}

## **Vault Setup**

Aiimi Insight Engine determines how to retrieve passwords and certificates based on the configurations in your appsettings.json files. If a key vault is configured, that is tried first. If that fails or is not configured it will revert to looking locally for passwords and certificates.&#x20;

1. **Set up certificates -** Within your Key Vault you need to set up your certificates, secrets and passwords.
   * We recommend adding a year to the certificate names. This can help with certificate management and switching certificates.
2. **Vault Access -**  You need to grant access to the vault, this varies depending on the vault plugin.
3. **Update appsettings.json -** Add the Key Vault details to the root of each appsetting.json file.
   * This can be done manually or via a bulk update.

<details>

<summary>Manual appsettings.json Update</summary>

We recommend starting with the index utils file. This way you can confirm the settings are correct before changing all of the others.

1. Add the below settings to every appsettings.json file:
   * Replace the values between the <> for your chosen key vault.

{% code lineNumbers="true" %}
```json
{
  "keyVault": {
    "type": "<AzureKeyVault>",
    "enableTracing": false,
    "azureKeyVault": {
      "vaultUri": "https://<vaultId>.vault.azure.net/"
    }
  }
}
```
{% endcode %}

</details>

<details>

<summary>Bulk appsettings.json Update</summary>

You can add the keyVault settings to every file using a JSON file and PowerShell. We recommend running a back up before completing this incase something goes wrong.

1. Create a JSON file containing the below information:
   * Replace the values between the <> for your chosen key vault.

{% code overflow="wrap" lineNumbers="true" %}
```json
{
  "keyVault": {
    "type": "<AzureKeyVault>",
    "enableTracing": false,
    "azureKeyVault": {
      "vaultUri": "https://<vaultId>.vault.azure.net/"
    }
  }
}
```
{% endcode %}

2. Save this a .json file.
3. Open PowerShell as an admin.
4. Run: im-settings add --installation-folder \<F:\InsightMaker\\> \<C:\tmp\akv.json>
   * Replace the values between the <> to match your file paths. The first should be where your insight maker files are stored. The second is the path for the json file you just created.

</details>

{% hint style="info" %}
During set up you can set "enableTracing" to true to help debugging.&#x20;

This could log sensitive information and must be set to false once it is working correctly.
{% endhint %}

4. Replace any certificate and password values with the certificate or secret name in the vault.
   * Certificate passwords are handled by the vault and should be set to "".

<details>

<summary>Annotated Example</summary>

1. The certificate used to validate connections to the Elastic server. It is retrieved from the vault by downloading the certificate `elastic-stack-ca`.
2. The certificate password is not needed as it's managed by the vault.
3. The `elastic` user password is retrieved from the vault by downloading the secret `elasticPassword`.
4. The certificate to encrypt HTTPS connections to the API endpoint is retrieved from the vault by downloading the certificate `elastic-certificates`.
5. The system secret is retrieved from the vault by downloading the secret `systemSecret`.
6. The vault configuration section. This uses the `AzureKeyVault` plugin to access a vault at `https://pandora.vault.azure.net/`.&#x20;

<pre data-overflow="wrap" data-line-numbers><code><strong>{
</strong>  "elastic": {
    "certificate": {
      "path": "elastic-stack-ca", 1️⃣
      "password": "" 2️⃣
    },
    "password": "elasticPassword", 3️⃣
    "prefix": "dev",
    "server": [
      "https://im.aiimi.com:9200"
    ],
    "username": "elastic",
    "enableTracing": false
  },
  "plugins": {
    "locations": [
      "c:\\InsightMaker\\Plugins"
    ]
  },
  "remoteApi": {
    "AllowedOrigins": [
      "*"
    ],
    "BindAddresses": [
      "0.0.0.0"
    ],
    "Port": 2221,
    "RemoteAddress": "https://im.aiimi.com",
    "certificate": {
      "path": "elastic-certificates", 4️⃣
      "password": "" 2️⃣
    }
  },
  "systemSecret": "systemSecret", 5️⃣
  "licenseKey": "",
  "licenseSig": "",
  "keyVault": { 6️⃣
    "type": "AzureKeyVault", 
    "azureKeyVault": {
      "vaultUri": "https://pandora.vault.azure.net/"
    }
  }
}
</code></pre>

</details>

***

## Azure Key Vault

This plugin allows Aiimi Insight Engine to retrieve certificates and passwords from Azure Key Vault. It accesses it via a URI provided in the config, and supports `DefaultAzureCredential`. This allows you to control access via secrets or passwords stored in environment variables, managed identities (if running in an Azure environment), Azure CLI/PowerShell or interactive.

This configuration requires the access to be encompassed by DefaultAzure Credentials. However, You should follow your existing procedures when configuring access to the vault.

{% hint style="info" %}
There is no authentication section to grant access to the vault, this must be setup via environment variables, managed identities, something compatible with `DefaultAzureCredentials`.
{% endhint %}
