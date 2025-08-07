# Migrating ACS to Azure AD with Sites.FullControl.All

Migrating from ACS with Sites.FullControl.All permissions to Azure AD with Sites.FullControl.All permissions.&#x20;

Using Azure Communication Services for authentication with **Sites.FullControl.All** permissions is being deprecated. If you are using this, you must migrate away from it by 2nd April 2026.&#x20;

The preferred way of authenticating is using an Azure Portal App Registration. It gives an application an Entra ID (previously Azure AD). The Entra ID manages the authentication and allows invocation of supported apps. This includes SharePoint via API permission scopes.&#x20;

This document details how to configure an application in Azure Portal and Control Hub changes. It can assist anyone migrating from ACS to Azure AD.&#x20;

<details>

<summary>Prerequisites</summary>

* You must grant access to the IPs listed under the [SharePoint section of Microsofts URLs and IP Address Ranges document](https://learn.microsoft.com/en-us/microsoft-365/enterprise/urls-and-ip-address-ranges?view=o365-worldwide#sharepoint-online-and-onedrive-for-business).

</details>

***

## Azure Portal - Application Registration&#x20;

To register the SharePoint connector application within Azure Portal, follow these steps:&#x20;

1. Navigate to [https://portal.azure.com](https://portal.azure.com/)&#x20;
2. Ensure you are in the correct Azure Directory.&#x20;
3. In the search bar, type “App Registrations” or click the shortcut under Azure Services.&#x20;
4. Select New registration.&#x20;
5. **Name** - Give the application a user friendly name&#x20;
6. **Supported account types** - Consider if the application will only be used in this directory or others within your organisation.&#x20;
7. **Redirect URI (optional)** – This is not required.&#x20;
8. Select Register.&#x20;
9. This will take you to the registered application page with an overview of your application. You'll need the Application (client) ID and Directory (tenant) ID from this page later in the process. &#x20;

***

## Azure Portal - Certificates & Secrets&#x20;

You can now create and apply a self-signed X.509 certificate. This will authenticate and invoke SharePoint Online via the registered application.

Alternatively, you can use an X.509 certificate issued by your preferred Certificate Authority (CA). Although the certificate is not client facing.&#x20;

This guide explains creating the self-signed certificate and manifest settings using a Cmdlet. They're needed to use SharePoint CSOM via app-only API permissions. You create them using the PnP.PowerShell Cmdlet, **New-PnPAzureCertificate.** [See Microsofts app only security documentation for more information on this.](https://learn.microsoft.com/en-us/sharepoint/dev/solution-guidance/security-apponly-azuread)

#### Cmdlet Requirements&#x20;

* Running PowerShell 7 running in Administrator mode.&#x20;
* The PnP.PowerShell module to be installed.&#x20;

### Running the Cmdlet

1. Open a PowerShell terminal as an administrator and run the following command.&#x20;

{% code overflow="wrap" lineNumbers="true" %}
```powershell
New-PnPAzureCertificate -OutPfx pnp.pfx -OutCert pnp.cer -CertificatePassword (ConvertTo-SecureString -String "<Your Password>" -AsPlainText -Force) 
```
{% endcode %}

2. Save the certificate files in your preferred location and give them a strong password.&#x20;
   * Make sure both the .cer and .pfx files are saved. \
     The .cer (public key) will be uploaded to the registered application in Azure Portal. \
     The .pfx (private key) will be uploaded to the Credential Store in Aiimi Insight Engine Control Hub.&#x20;

### Apply the certificate to the registered application&#x20;

1. In Azure Portal, select Certificates & Secrets.&#x20;
2. Ensure you are on the Certificates tab.&#x20;
3. Select Upload certificate.&#x20;
4. Select the .cer file you created using **New-PnPAzureCertificate**.&#x20;
5. **Description** – Add a description to the certificate of what it will be used for.
6. Select Add.&#x20;

This certificate is now associated with the registered application in Azure.

***

## Azure Portal - API Permissions&#x20;

Now you have a registered application with a certificate, you can add API Permissions. &#x20;

1. In Azure Portal, navigate to your registered application.&#x20;
2. Under Manage, select API Permissions.&#x20;
   * There will always be Microsoft Graph, [**User.Read**](http://user.read) permissions. This is required and should remain in place.&#x20;
3. Select Add a permission.&#x20;
4. Under Microsoft APIs, select SharePoint.&#x20;
5. Select Application permissions.&#x20;
   * This ensures user credentials aren't required for authentication and the context is not scoped to one user.&#x20;
6. From the available permissions, select **Sites.FullControl.All**.&#x20;
   * This is currently the only API permission level we readily support for the SharePoint Online connector.&#x20;
   * Permission levels lower than this, **Sites.Read.All** for example are not yet proven and may have unintended consequences.&#x20;
   * We are actively working to allow the SharePoint Online connector to run in a read-only mode.&#x20;
7. Select Add permission.&#x20;
   * The permissions have been applied but not yet granted to the registered application.&#x20;
8. You must grant admin consent for any permission applied.&#x20;
   * This allows silent authentication for APIs. Without this the application needs a user invoked authentication flow.&#x20;
9. Select Grant admin consent for \<organisation>.&#x20;
10. Select Yes to confirm this selection when prompted.

The **Sites.FullControll.All** API permission has been applied to the registered application.&#x20;

***

## Aiimi Insight Engine - Credentials&#x20;

Now everything is configured in Azure Portal, you need to create credentials in Aiimi Insight Engine's Control Hub.&#x20;

1. Within the Control Hub select Credentials.&#x20;
2. On the Credentials page, select New Credential.&#x20;
3. **Credential Type** – Select Certificate.&#x20;
   * This will reveal the relevant input fields for uploading a certificate.&#x20;
4. **Credential ID** – Enter an ID for this credential.&#x20;
   * It must be lowercase, with no spaces or special characters.&#x20;
5. **Credential Name** – Enter a user friendly name for this credential.&#x20;
6. **Password** – Enter the password associated with the certificate you generated earlier. &#x20;
7. **Expiry Date (DD-MM-YYYY)** – This will automatically populate according to the certificate’s expiry. &#x20;
   * You can add a date to the certificate expiry if needed. It must not be in the past or after the certificate’s expiry date.&#x20;
8. **Import Certificate** – Either, drag and drop the .pfx file or find it using the “browse files” link.&#x20;
   * If using “browse files” in Windows Explorer you must enable “All Files (_._)" when searching.&#x20;
   * Only valid certificates can be uploaded.&#x20;
9. Select Create.&#x20;

Your new certificate credential is now in the Aiimi Insight Engine Credential Store.&#x20;

***

## Aiimi Insight Engine – Source Configuration&#x20;

Now the registered application and credentials are set up, you can configure a SharePoint source. &#x20;

1. Within the Control Hub select New Configuration.&#x20;
   * If you're applying this to an existing source, find the configuration and select edit.
2. On the Source tab, select SharePoint from the Source System dropdown.&#x20;
3. **Client ID** – Enter the Application (client) ID of the registered application. &#x20;
   * You can find this in the Overview on the Azure Portal.&#x20;
4. **Directory (Tenant) ID** – Enter the Directory (tenant) ID for the registered application. &#x20;
   * You can find this in the Overview on the Azure Portal.&#x20;
5. **Select Credential** – Select the certificate credential associated with the .pfx file.
6. Select Save.&#x20;

You are now ready to run a crawl without using ACS authentication.&#x20;
