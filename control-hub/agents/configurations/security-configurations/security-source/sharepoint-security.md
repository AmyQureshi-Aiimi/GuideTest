# SharePoint Security

Synchronise users and groups from your SharePoint system into Workplace AI.

1. **Security System:** Select SharePoint Security from the dropdown.

## Connection

#### Primary

1. **Client ID** - Enter the Client ID for the Azure Registered Application to use.
   * This can be found in Azure's Enterprise Application configuration pages.
2. **Directory (Tenant) ID** - Enter the Azure Application Directory or Tenant ID to use.
3. **Select Credential** - Select the matching Certificate credential for your SharePoint.

<figure><img src="../../../../../.gitbook/assets/image (32).png" alt="" width="563"><figcaption></figcaption></figure>

#### Secondary

1. **Graph API Endpoint** - Enter the Graph API endpoint.
   * In most situations the default does not need changing.
2. **Authentication Endpoint** - Enter the endpoint that's needed to authenticate requests.
   * In most situations the default does not need changing.
3. **Select Credential** - Select the matching Client ID Secret credential for your SharePoint.
   * This can be found in the Azure Enterprise Application configuration pages.

<figure><img src="../../../../../.gitbook/assets/image (33).png" alt="" width="563"><figcaption></figcaption></figure>

***

## Sync

#### Domain

1. **Federated Domain Name** - Add the relevant domain to sync a subset of users.&#x20;
   * This is your managed domain name.
   * If left blank all users across all domains will be synced.

<figure><img src="../../../../../.gitbook/assets/image (34).png" alt="" width="563"><figcaption></figcaption></figure>

#### Sites

1. **Site Discovery Type** - To sync certain users from certain site types, choose the type from the dropdown.
   * Choose SharePoint, OneDrive, or Both.
2. **Sites To Include** - Enter a site to only sync the users who have access to it.
   * If you enter a site to include the Site Discovery Type Setting will be ignored.
3. **Sites To Exclude** - Enter a Regex to select the sites that should not be synced.
   * For example you could not sync anything from files containing the words "Top Secret".

<figure><img src="../../../../../.gitbook/assets/image (35).png" alt="" width="563"><figcaption></figcaption></figure>

#### Groups

1. **Groups To Include** - Enter a regex to select the groups that should be included in a sync.
   * For example you could, only sync the owners of a site, ignoring members and viewers.
2. **Groups To Exclude** - Enter a regex to select the groups that should be excluded from a sync.
   1. Groups found in the Exclusions and inclusions list will be excluded.

<figure><img src="../../../../../.gitbook/assets/image (36).png" alt="" width="563"><figcaption></figcaption></figure>

***

## Mappings

#### Object Mapping

1. **Prefix Security Objects with Configuration ID** - If checked, the security objects will be prefixed with this configuration's ID.

#### User Mapping

2. **Match Users On** - Select how the SharePoint and Workplace AI usernames are linked.
   * Exact match - Both usernames match exactly.
   * Alternative Domain - The domain in SharePoint is different to Workplace AI.
3. **Alternative Domain** - Enter the domain in SharePoint used to identify users.

<figure><img src="../../../../../.gitbook/assets/image (37).png" alt="" width="563"><figcaption></figcaption></figure>

***

## Advanced

#### API Throttling

1. **SharePoint Client Context Timeout** - The time allowed for all requests made to SharePoint in CSOM using the Client Context.
   * The default is -1 which is equal to no limit.

#### Parallelism

2. **Parallel Queue Processing** - Enter the maximum number of items in a queue that can be processed at the same time.

<figure><img src="../../../../../.gitbook/assets/image (38).png" alt="" width="563"><figcaption></figcaption></figure>
