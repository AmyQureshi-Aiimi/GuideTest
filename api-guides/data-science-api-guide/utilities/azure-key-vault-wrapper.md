# Azure Key Vault Wrapper

The AzureKeyVault class is a wrapper for Azure's Key Vault service. It provides simplified access to secrets, certificates, and keys stored within a specified vault. It extends the KeyVault class and utilises Azure SDK clients to interact with the vault. It is particularly useful in applications that require secure storage and retrieval of sensitive information.

{% hint style="info" %}
For support building queries [use our Query Builder guide.](query-builders.md)
{% endhint %}

## Initialisation&#x20;

`AzureKeyVault(vault_url=None)`

* **Parameters:**&#x20;
  * `vault_url`: A string representing the URL of the Azure Key Vault. If not provided, the class attempts to retrieve it from the VAULT\_URL environment variable.&#x20;
* **Raises:**&#x20;
  * Exception: If no vault URL is found either through the parameter or the environment variable.&#x20;
* **Notes:**&#x20;
  * The class uses DefaultAzureCredential for authentication, which supports various authentication methods, including managed identity and environment variables.&#x20;

***

## Attributes&#x20;

* `secret_client`: An instance of SecretClient for managing secrets.&#x20;
* `cert_client`: An instance of CertificateClient for managing certificates.&#x20;
* `key_client`: An instance of KeyClient for managing keys.&#x20;

***

## Methods&#x20;

### Get Secret

`get_secret(name: str) -> str` \
Retrieves the value of a secret from the Azure Key Vault.&#x20;

* **Parameters:**&#x20;
  * `name`: A string representing the name of the secret.&#x20;
* **Returns:**&#x20;
  * A string containing the value of the secret.&#x20;

### Get Certificate

`get_certificate(name: str)` \
Retrieves a certificate from the Azure Key Vault and returns it in PEM format.&#x20;

* **Parameters:**&#x20;
  * `name`: A string representing the name of the certificate.&#x20;
* **Returns:**&#x20;
  * A string containing the certificate in PEM format.&#x20;

### Get Key

`get_key(name: str)`\
Retrieves a key from the Azure Key Vault and returns it in PEM format. Supports both public and private RSA keys.&#x20;

* **Parameters:**&#x20;
  * `name`: A string representing the name of the key.&#x20;
* **Returns:**&#x20;
  * A string containing the key in PEM format.&#x20;
* **Raises:**&#x20;
  * `ValueError`: If the key is not of type RSA.&#x20;
* **Notes:**&#x20;
  * The method checks for the presence of private key components to determine whether to return a private or public key.&#x20;

#### Example&#x20;

```python
from aiimi_insight_engine.key_vault.azure_key_vault import AzureKeyVault 
vault = AzureKeyVault("https://mysecurevault.vault.azure.net/") 
my_secret = vault.get_secret("secret_name") 
```
