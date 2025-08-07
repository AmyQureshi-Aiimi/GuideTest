# Azure Portal and Azure AD Authentication

Azure Communication Services (ACS) are being deprecated. Authentication via Azure Portal and Azure AD is the modern way to manage app registration, communication and authentication.

You can use an Azure Registered Application with a certificate to connect to SharePoint Online. This allows for modern API Permission management scopes such as Sites.Selected via the SharePoint API in Azure.

<details>

<summary>Prerequisites</summary>

* Ensure you have an Azure Registered Application in Azure Portal.

- Grant the desired Application API Permissions for SharePoint in the Azure Portal.

* Ensure you grant admin consent for your organisation.

- Your Azure Registered Application Client ID and Tenant ID.

* You must grant access to the IPs listed under the [SharePoint section of Microsofts URLs and IP Address Ranges document](https://learn.microsoft.com/en-us/microsoft-365/enterprise/urls-and-ip-address-ranges?view=o365-worldwide#sharepoint-online-and-onedrive-for-business).

{% hint style="info" %}
You can follow Microsoft's guide for help [Granting access via Azure AD](https://learn.microsoft.com/en-us/sharepoint/dev/solution-guidance/security-apponly-azuread?WT.mc_id=M365-MVP-9698).
{% endhint %}

</details>

***

### Available SharePoint API Application permissions:

* **Sites.FullControl.All** - Allows the app full control of all site collections without a signed in user.
  * This allows for add, edit and delete operations on ALL site objects.
  * This has the ability to add, edit, delete entire site collections and document libraries.
* **Sites.Selected** - Allow the application to access a subset of site collections without a signed in user. The specific site collections and the permissions granted will be configured in SharePoint Online or via the Graph API.
  * This will only work if you grant **Sites.Selected** for the Registered Application used to connect to SharePoint Online. (Application A).
  * You must then use another Azure Registered Application with Graph API Application permissions of **Sites.FullContrl.All** to add the SharePoint application to each sites granted identities. (Application B)
  * This requires the highest level of permissions to change.

{% hint style="info" %}
This can be achieved with PowerShell cmdlets or by calling the Graph API directly.
{% endhint %}

<details>

<summary>Site.Selected Grant Site Granular Level Permissions</summary>

If you are using Sites.Selected you must grant access to the Azure registered application responsible for crawling SharePoint for each selected site.&#x20;

You must do this on a per site basis.

### Using PowerShell

1. Connect to the site using PowerShell.
   * {% code overflow="wrap" %}
     ```
     Connect-PnPOnline -ClientId "<Application-B-Client-ID>" -CertificatePath ".\pnp.pfx" -CertificatePassword (ConvertTo-SecureString -AsPlainText "changeme" -Force) -Url "<SITE-URL>" -Tenant "aiimiqa.onmicrosoft.com"
     ```
     {% endcode %}
2. Grant access to the application, by adding it to the sites grantedToIdentities.
   * {% code overflow="wrap" %}
     ```
     Grant-PnPAzureADAppSitePermission -AppId "<Application-A-Client-ID>" -DisplayName "SharePoint Connector CSOM AD" -Permissions Read -Site "<SITE-URL>"
     ```
     {% endcode %}

### Using GraphAPI

1. Alternatively the Graph API can also be used to achieve this with the following endpoint:
   1. {% code overflow="wrap" %}
      ```
      POST https://graph.microsoft.com/v1.0/sites/<Graph-API-Site-ID>/permissions
      ```
      {% endcode %}
2. And following body:
   * {% code overflow="wrap" %}
     ```
     {
       "roles": ["read"],
       "grantedToIdentities": [
         {
           "application": {
             "id": "Application-A-Client-ID",
             "displayName": "SharePoint GRAPH API App"
           }
         }
       ]
     }
     ```
     {% endcode %}

</details>

<details>

<summary>Sites.Selected Permissions Limitation</summary>

If you're using SharePoint API Application Permissions Sites.Selected and only granting the application the "Read" only role, the SharePoint connector cannot retrieve file permissions. It must be run in permissionless mode.&#x20;

* Within the Source to to Advanced and check Permissionless Crawl.
* To retrieve an item permissions you must run the SharePoint connector with Sites.FullControl.All or Sites.Selected with a role of "FullControl" granted at the site level.

### Recycle Bin Access

Another limitation of using Sites.Selected with Read access is we cannot track folders which have been deleted and any deleted children. This requires access to the Recycle Bin which requires FullControl.

Because of this, we recommend you don't run delta token crawls while using Sites.Selected with anything less than FullControl.

</details>

***

## Certificate and Credential

A signed certificate is needed to authenticate and connect between the two systems.&#x20;

1. Create a signed certificate for your application. This may be self signed depending on company policies.
   * You can use a PnP cmdlet to help.
     * {% code overflow="wrap" %}
       ```
       New-PnPAzureCertificate -OutPfx pnp.pfx -OutCert pnp.cer -CertificatePassword (ConvertTo-SecureString -String "<Your Certificate Password>" -AsPlainText -Force)
       ```
       {% endcode %}
2. Ensure you have uploaded the generated certificate to the Registered Azure Application in Azure Portal.
3. Create a Certificate Credential within Workplace AI using the .pfx certificate file.
   * For support setting up credentials use [our guide on managing credentials.](../../../../../security/credentials.md)
