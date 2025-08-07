# Migrating ACS to Azure AD with Sites.Read.All

Using Azure Communication Services for authentication with Sites.FullControl.All permissions is being deprecated. If you are using this, you must migrate away from it by 2nd April 2026. &#x20;

The preferred way of authenticating is using an Azure Portal App Registration. It gives an application an Entra ID (previously Azure AD). The Entra ID manages the authentication and allows invocation of supported apps. This includes SharePoint via API permission scopes. &#x20;

The SharePoint connector may need to run against API permissions granting Read-Only access. This means, at an API level, the app can only read SharePoint objects. It cannot create, update or delete SharePoint objects. &#x20;

This guide explains how to configure an application in Azure Portal and any Control Hub changes. It can assist anyone migrating from ACS to Azure AD while using Read-Only API permissions. &#x20;

<details>

<summary>Prerequisites</summary>

* You must grant access to the IPs listed under the [SharePoint section of Microsofts URLs and IP Address Ranges document](https://learn.microsoft.com/en-us/microsoft-365/enterprise/urls-and-ip-address-ranges?view=o365-worldwide#sharepoint-online-and-onedrive-for-business).

</details>

***

## Azure Portal - Application Registration

To register the SharePoint connector application within Azure Portal, follow these steps:&#x20;

1. Navigate to [https://portal.azure.com](https://portal.azure.com/)
2. Ensure you are in the correct Azure Directory.&#x20;
3. In the search bar, type “App Registrations” or click the shortcut under Azure Services.&#x20;
4. Select New registration.&#x20;
5. **Name** - Give the application a user friendly name.&#x20;
6. **Supported account types** - Consider if the application will only be used in this directory or others within your organisation. &#x20;
7. **Redirect URI (optional)** – This is not required.&#x20;
8. Select Register.&#x20;

This will take you to the registered application page with an overview of your application. You'll need the Application (client) ID and Directory (tenant) ID from this page later in the process.

***

## Azure Portal - Certificates & Secrets&#x20;

You can now create and apply a self-signed X.509 certificate. This will authenticate and invoke SharePoint Online via the registered application.&#x20;

Alternatively, you can use an X.509 certificate issued by your preferred Certificate Authority (CA). Although the certificate is not client facing. &#x20;

This guide explains creating the self-signed certificate and manifest settings using a Cmdlet. They're needed to use SharePoint CSOM via app-only API permissions. You create them using the PnP.PowerShell Cmdlet, New-PnPAzureCertificate. [See Microsoft's app only security documentation for more information on this.](https://learn.microsoft.com/en-us/sharepoint/dev/solution-guidance/security-apponly-azuread)

#### Cmdlet requirements

* Running PowerShell 7 in Administrator mode.&#x20;
* The PnP.PowerShell module to be installed.&#x20;

### Running the Cmdlet

1. Open a new administrator PowerShell terminal and run the following command.&#x20;

{% code overflow="wrap" lineNumbers="true" %}
```powershell
New-PnPAzureCertificate -OutPfx pnp.pfx -OutCert pnp.cer -CertificatePassword (ConvertTo-SecureString -String "<Your Password>" -AsPlainText -Force) 
```
{% endcode %}

2. Save the certificate files in your preferred location and give them a strong password. &#x20;
   * Make sure both the .cer and .pfx files are saved.  \
     The .cer (public key) will be uploaded to the registered application in Azure Portal.  \
     The .pfx (private key) will be uploaded to the Credential Store in Workplace AI Control Hub.&#x20;

### Apply the certificate to the registered application&#x20;

1. In Azure Portal, select Certificates & Secrets. &#x20;
2. Ensure you are on the Certificates tab.&#x20;
3. Select Upload certificate.&#x20;
4. Select the generated .cer file you created using **New-PnPAzureCertificate**.&#x20;
5. **Description** – Add a description of how the certificate will be used.&#x20;
6. Select Add.&#x20;

This certificate is now associated with the registered application in Azure.&#x20;

### Create a secret for the registered application&#x20;

1. In Azure Portal, select Certificates & Secrets.&#x20;
2. Ensure you are on the Client Secrets tab.&#x20;
3. Select New Client Secret.&#x20;
4. **Description** – Add a description to the secret of what it will be used for.&#x20;
5. **Expires** – Give the secret an appropriate expiry date.&#x20;
6. Select Add.&#x20;
7. Be sure to save your secret to a secure vault such as LastPass as you will not be able to view it again.&#x20;

This secret is now associated with the registered application in Azure.&#x20;

It's important to have both authentication methods set up. We use both to leverage Graph APIs Read-Only capabilities where necessary. The certificate is required for the CSOM (Client-Side Object Model) library for SharePoint. While the secret is required for the Graph API.

***

## Azure Portal - API Permissions

Now you have a registered application with a certificate and secret, you can add API Permissions.  &#x20;

1. In Azure Portal, navigate to your registered application.&#x20;
2. Under Manage, select API Permissions.&#x20;
   * There will always be Microsoft Graph, **User.Read** permissions. This is required and should remain in place.&#x20;
3. Select Add a permission.&#x20;
4. Under Microsoft APIs, select SharePoint.&#x20;
5. Select Application permissions.&#x20;
   * This ensures user credentials aren't required for authentication and the context is not scoped to one user.&#x20;
6. From the available permissions, select **Sites.Read.All**.&#x20;
7. Select Add permission.
8. Select Add permission again.
9. Select Graph API&#x20;
10. Select Application permissions.&#x20;
11. From the available permissions, select **Sites.Read.All**.&#x20;
12. Select add permission.&#x20;
    * The permissions have been applied but not yet granted to the registered application.&#x20;
13. You must grant admin consent for any permission applied.&#x20;
    * This allows silent authentication for APIs. Without this the application needs a user invoked authentication flow.&#x20;
14. Select Grant admin consent for \<organisation>.&#x20;
15. Select Yes to confirm this selection.&#x20;

The **Sites.Read.All** API permission has been applied to the registered application for SharePoint and the Graph API.&#x20;

***

## AIE Control Hub – Credentials&#x20;

Now everything is configured in Azure Portal, you need to create credentials in Workplace AI's Control Hub.&#x20;

### Create a Certificate credential&#x20;

1. Within the Control Hub select Credentials.&#x20;
2. On the Credentials page, select New Credential.&#x20;
3. **Credential Type** – Select Certificate.&#x20;
   * This will reveal the relevant input fields for uploading a certificate.&#x20;
4. **Credential ID** – Enter an ID for this credential.&#x20;
   * It must be lowercase, with no spaces or special characters.&#x20;
5. **Credential Name** – Enter a user friendly name for this credential.&#x20;
6. **Password** – Enter the password associated with the certificate you generated earlier.&#x20;
7. **Expiry Date (DD-MM-YYYY)** – This will automatically populate according to the certificate’s expiry. &#x20;
   * You can add a date to the certificate expiry if needed. It must not be in the past or after the certificate’s expiry date.&#x20;
8. **Import Certificate** – Either, drag and drop the .pfx file or find it using the “browse files” link.&#x20;
   * If using “browse files” in Windows Explorer you must enable “All Files (\*.\*)" when searching.&#x20;
   * Only valid certificates can be uploaded.&#x20;
9. Select Create.&#x20;

Your new certificate credential is now in the Workplace AI Credential Store.&#x20;

### Troubleshooting

Certificates are validated at the point of creation. Validation checks things like passwords, expiry dates and user profile capabilities.&#x20;

#### Applying the certificate to the Credential Store&#x20;

If you get an error about the expiry date or network password, check they are correct in the credential.&#x20;

#### An error stating “The file cannot be found”&#x20;

1. Open Internet Information Services (IIS) on the web server running AIE Control Hub.&#x20;
2. Open Internet Information Services (IIS) on the web server running AIE Control Hub.&#x20;
3. Confirm which AppPool used for the admin API.&#x20;
   1. Navigate to Sites -> Default Web Site -> admin -> api.&#x20;
      * Open Basic Settings for the api and observe the AppPool used.&#x20;
   2. Navigate to the AppPool  - Application Pools -> \<YouAdminAppPool> &#x20;
   3. Open Advanced Settings for the Admin AppPool.&#x20;
   4. Under Process Model, ensure “Load User Profile” is set to True.&#x20;
   5. Restart IIS, this will also recycle your Application Pools too.&#x20;

&#x20;You should now be able to your certificate to the Credential Store in the Control Hub.&#x20;

### Create a Client ID Secret Credential&#x20;

1. Within the Control Hub select Credentials.&#x20;
2. On the Credentials page, select New Credential.&#x20;
3. **Credential Type** – Select Client ID and Secret.&#x20;
4. **Credential ID** – Enter an ID for this credential.&#x20;
   * It must be lowercase, with no spaces and no special characters.&#x20;
5. **Credential Name** – Enter a user friendly name for this credential.&#x20;
6. **Secret** – Enter the secret associated with the registered application in Azure.&#x20;
7. **Expiry Date (DD-MM-YYYY)** – Enter the expiry date&#x20;
   * It must not be in the past or after the secret’s expiry date.&#x20;
8. Select Create.&#x20;

Your new secret credential is now in the Workplace AI Credential Store.&#x20;

***

## AIE Control Hub – Security Configuration&#x20;

If you enabled “Use Graph API for permissions” you will likely want to discover members of SharePoint groups in the following scenario: &#x20;

A file or folder, which is shared with a SharePoint group, is discovered via the SharePoint source connector. The connector will tag files with the name of the SharePoint group in the permission object.&#x20;

{% hint style="info" %}
For permission trimming in Workplace AI, we must know the SharePoint groups a user belongs to.
{% endhint %}

Members of a SharePoint group are exploded onto an item during crawl time when using **Sites.FullControl.All**. If using the Graph API for permissions, we can only access the SharePoint group names not who is in them. &#x20;

The SharePoint Security plugin allows for a secondary security sync. It maps users from SharePoint to users in Workplace AI. The SharePoint group membership is applied to each principles Groups property. This is done in a secondary security index.&#x20;

### Creating a SharePoint Security configuration&#x20;

{% hint style="info" %}
If you're running a permissionless crawl, a SharePoint Security Sync isn't needed. You can skip this step.
{% endhint %}

1. Within the Control Hub select New Configuration.&#x20;
2. Select Security.
3. **Configuration ID** – Enter an ID for this configuration.
   * It must be lowercase, with no spaces or special characters.&#x20;
4. **Configuration Description** – Add a description of what the configuration will be used for.&#x20;
5. **Source System** - Select SharePointSecurity from the dropdown.

#### Primary Connection

6. **Client ID** – Enter the Application (client) ID of the registered application.&#x20;
   * You can find this in the Overview on the Azure Portal.&#x20;
7. **Directory (Tenant) ID** – Enter the Directory (tenant) ID for the registered application. &#x20;
   * You can find this in the Overview on the Azure Portal.&#x20;
8. **Select Credential** – Select the certificate credential associated with the .pfx file.&#x20;

#### Secondary Connection&#x20;

9. **Select Credential** – Select the secret associated with your registered application in Azure.&#x20;
   * [Use our guide for SharePoint Security Configurations for support completing the remaining properties.](../../control-hub/agents/configurations/security-configurations/security-source/sharepoint-security.md)
10. The SharePoint security configuration is designed to run with Read-Only API permissions.&#x20;
    * The only limitation to this is when discovering members of limited access or sharing links groups. These groups require the API permission to be **Sites.FullControl.All** in Azure.&#x20;
    * If you don't need to synchronise these groups, you can run the configuration with [**Sites.Read**](http://sites.read/)**.All** API permissions in Azure.&#x20;

***

## AIE Control Hub – Source Configuration&#x20;

Now the registered application, credentials and security are set up, you can configure a SharePoint source. &#x20;

1. Within the Control Hub select New Configuration.&#x20;
   * If you're applying this to an existing source, find the configuration and select edit.
2. On the Source tab, select SharePoint from the Source System dropdown.&#x20;

#### Primary Connection

1. **Client ID** – Enter the Application (client) ID of the registered application. &#x20;
   * You can find this in the Overview on the Azure Portal.&#x20;
2. **Directory (Tenant) ID** – Enter the Directory (tenant) ID for the registered application. &#x20;
   * You can find this in the Overview on the Azure Portal.&#x20;
3. **Select Credential** – Select the certificate credential associated with the .pfx file.

#### Secondary Connection

1. Check “Use Graph API for site discovery”.
2. **Directory (Tenant) ID** – Enter the Directory (tenant) ID for the registered application. &#x20;
   * You can find this in the Overview on the Azure Portal.&#x20;
3. **Select Credential** – Select the secret associated with your registered application in Azure. &#x20;

#### If Using Graph API for Permissions

1. Check “Use Graph API for permissions”.
   * Only enable this if permissions on files are needed. Otherwise run the crawl as permissionless under the Advanced tab.&#x20;

#### If you're indexing permissions

1. On the Permissions tab.
2. **Security Configuration** – Enter the configuration ID of the SharePoint Security configuration you made earlier.&#x20;
   * This is not required if you are running permissionless crawls.
   * This is very important for permission trimming in Workplace AI. It is validated when saving the source configuration.&#x20;
3. Select Save.&#x20;

You are now ready to run a crawl using Read-Only API permissions instead of ACS.&#x20;
