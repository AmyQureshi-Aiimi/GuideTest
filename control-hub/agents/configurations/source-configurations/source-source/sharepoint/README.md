# SharePoint

Connect your SharePoint source to Aiimi Insight Engine to make the most of your data. Once you have selected a Source System type more detail will expand to customise this.

## Recommended SharePoint API Application Permissions

The two recommended permission options for your SharePoint API are Sites.Full.Control.All or Sites.Selected.

**Sites.FullControl.All** - Allows the app full control of all site collections.

* This allows add, edit and delete operations on **ALL** site objects.
* This can add, edit, delete entire site collections and document libraries.

**Sites.Selected** - Allows the application to access a subset of sites. The specific sites and the permissions granted are configured for each sites granted identities and must use **FullControl**.

* This only works if you grant **Sites.Selected** for the Registered Application used to connect to SharePoint Online. (Application A).
* You must then use another Azure Registered Application with Graph API Application permissions of **Sites.FullControl.All** to add the SharePoint application to each sites granted identities. (Application B)
* This requires the highest level of permissions to change.

<details>

<summary>Azure Portal Azure AD Authentication</summary>

Azure Communication Services (ACS) are being deprecated. Authentication via Azure Portal and Azure AD is the modern way to manage app registration, communication and authentication.

You can use an Azure Registered Application with a certificate to connect to SharePoint Online. This allows for modern API Permission management scopes such as Sites.Selected via the SharePoint API in Azure.

For support setting this up use [our guide on Azure Portal and Azure AD Authentication.](azure-portal-and-azure-ad-authentication.md)

</details>

***

## Connection

### **Primary**

1. **Authentication Mode** - Select the type of authentication to use when connecting to SharePoint.
2. **Client ID** - Enter the SharePoint online or Azure Registered Application Client ID to use.
3. **Directory (Tenant) ID** - Enter the SharePoint online or Azure Registered Application Tenant ID to use.
4. **Select Credential (Username & Password)** - Choose the credentials to use.
   * For support setting up credentials use [our guide on managing credentials.](../../../../../security/credentials.md)
5. **Select Credential** - If your SharePoint Online does not have a Username and Password you must use a secret or certificate. Select the matching SecretOnly or Certificate credential for your SharePoint.
   * This will be the Azure Portal/Azure AD Certificate credential if required.
     * For support setting this up use [our guide on Azure Portal and Azure AD Authentication.](azure-portal-and-azure-ad-authentication.md)

### Secondary

1. **Use Graph API for Permissions -** If checked, the Graph API will be used to retrieve permissions.
2. **Use Graph API for Site Discovery** - If checked, the Graph API will be used to retrieve all sites, site collections and one drives.
   * If this is checked the Admin Centre URL won't be used.
3. **Graph API Endpoint -** Enter the Graph API endpoint.
   * In most situations the default does not need changing.
4. **Directory (Tenant) ID -** Enter the SharePoint online or Azure Registered Application Tenant ID to use.
   * This can be found in Azure Enterprise Application configuration page.
5. **Authentication Endpoint -** Enter the endpoint that's needed to authenticate requests.
   * The default does not need changing in most cases.
6. **Select Credential -** Select the Client ID secret for SharePoint Online.

<figure><img src="../../../../../../.gitbook/assets/image (40).png" alt="" width="563"><figcaption></figcaption></figure>

***

## Sites

1. **Site Discovery Type -** Choose the type of sites should be discovered during crawl.
   * Choose SharePoint, OneDrive, or Both.
2. **Admin Centre URL** - Enter the root URL of the site collection that should be crawled.
   * To use the admin centre URL Aiimi Insight Engine requires the highest level of access.
   * Format - https://\[site]-admin.sharepoint.com
3. **Sites** - Choose the sites within the root collection to crawl.&#x20;
   * Enter in specific Sites or leave blank to crawl all sites.
   * If you enter a site to crawl the Site Discovery Type setting will be ignored.
4. **Sites to Exclude** - If sites need excluding from the Crawl add them to Sites to Exclude.
5. **Included libraries** - Add specific libraries to crawl. This list overrides any exclusions if there is an overlap.
6. **Excluded libraries** -  Libraries can be excluded from the Crawl by adding them to the Excluded Libraries list.
   * The default excluded libraries can be removed or edited as needed.

<figure><img src="../../../../../../.gitbook/assets/image (29).png" alt="" width="563"><figcaption></figcaption></figure>

***

## Permissions

**Synchronisation**

1. **Security Configuration** - Enter the ID of the security configuration the connector will use to synchronise objects with Aiimi Insight Engine Users. This field is required for permission trimming.
   * The ID must match a SharePoint Security Configuration. [See our SharePoint security configuration guide for help setting this up.](../../../security-configurations/security-source/sharepoint-security.md)

{% hint style="warning" %}
This field is required if you are using Graph API for permissions.
{% endhint %}

**Groups**

2. **Additional Included Groups** - Add any additional user groups that should have access to this source within Aiimi Insight Engine.&#x20;
   * Permissions need to be granted in SharePoint for these users to access any items.
3. **Excluded Groups** - Add any user groups that should not have access to this source.

<figure><img src="../../../../../../.gitbook/assets/image (41).png" alt="" width="563"><figcaption></figcaption></figure>

***

## Mappings

1. **Owner Content Type Mapping -** Enter the content field type name to be used as the owner of a file.&#x20;
   * Formatted like SharePoints internal naming conventions. Content\_x0020\_Owner
2. **Entity to meta tag mappings** - You can map the entity fields to meta tags from the web page.
   * Enter the full entity field in the left column. For example, entities.Websites.category.
   * Enter the meta tag name in the right column
3. **Metadata to meta tag mappings** - You can map the metadata fields to meta tags from the web page.
   * Enter the full metadata field in the left column. For example, metadata.webtype.
   * Enter the meta tag name in the right column

<figure><img src="../../../../../../.gitbook/assets/image (64).png" alt="" width="563"><figcaption></figcaption></figure>

***

## Advanced

### API Throttling&#x20;

1. **Page Load Throttling** - To reduce timeouts you can change the Page Load Throttling.
   * By changing this you can increase the wait time between Chromium Page loads.
   * Enter the time in MS (2000 ms = 2 seconds).
2. **Content Limit Per Request** - Enter the maximum number of requests that can be made to Sharepoint.
   * Increasing the limit can improve the crawls performance. But, this is at the risk of creating timeouts if your SharePoint libraries contain complex metadata.&#x20;
   * Lowering the Content Limit Per Request more requests will run but each run will be quicker.
   * We would recommend starting with a batch size of 500.
3. **SharePoint Client Context Timeout** - Set a timeout value for all requests made to Sharepoint.&#x20;
   * Enter a CSOM value into the SharePoint Client Context Timeout.&#x20;
   * By default this is set to -1.5.

<figure><img src="../../../../../../.gitbook/assets/image (65).png" alt="" width="563"><figcaption></figcaption></figure>

### Utility Paths

1. **Path to SharePoint Online (only) Cookie Utility** - Enter the path to your preferred cookie authentication utility.
   * This will handle authentication when processing ASPX pages.&#x20;
   * You must explicitly enter the full path including the .exe.
   * If this field is left blank Default utils install locations will be used.
2. **Path to Chromium (Chrome)** - If Chromium has been manually deployed enter the full path including chrome.exe.
   * If this field is left black it will be downloaded once.

<figure><img src="../../../../../../.gitbook/assets/image (67).png" alt="" width="563"><figcaption></figcaption></figure>

### Crawl Options

1. **Process without Delta Tokens** - Check this to NOT use the library delta tokens.&#x20;
   * This will do a reprocess of the full library at every crawl and can be enabled to sync an index. All documents will be retrieved from the library, regardless of changes. However, only necessary changes will be made to your index.
     * If this is not checked, only the changes since the last change token will be retrieved from the library. Likewise only the necessary changes will be made to your index.
   * To use SharePoint change tokens to enable delta crawls uncheck this option.&#x20;
2. **Build Site Caches** - Check to build a cache of all users with access to a site.
   * If unchecked validation will be processed with each document.
3. **Generate Edit in Browser Link** - Check to generate an Open In browser app as default (SP Online only).
4. **Get Permissions In Bulk** - Check to gather all document permissions for everything in a library at once.&#x20;
   * The higher the document count the more memory intensive it will be.&#x20;
   * Not retrieving the permissions in bulk will mean a permission request for every file indexed. This can get you rate limited by SharePoint if many requests are sent in quick succession.
5. **Generate Open in App Link (MS Office docs only)** - Check to generate an Open In link as SharePoint does.&#x20;
   * For example, Open in word on the Users Machine (SP Online).
   * This will override the open in browser option.

<figure><img src="../../../../../../.gitbook/assets/image (68).png" alt="" width="563"><figcaption></figcaption></figure>

### Document Link

1. **CSS Class Name** - To extract a document link in aspx pages, enter the CSS classname for the hyperlink element.
2. **Document URL** - To extract a document link in aspx pages, enter the document link URL.
3. **Metadata Field** - To extract a document link in aspx pages, enter the metadata field in the index to store the link.

<figure><img src="../../../../../../.gitbook/assets/image (69).png" alt="" width="563"><figcaption></figcaption></figure>
