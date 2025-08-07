# Azure Active Directory

Synchronise users and groups from your Azure Active Directory (Azure AD). Azure AD is an identity management service provided by Microsoft used by Office 365.&#x20;

It is cloud only, and stores user and group information. These can come from Office 365 or synchronised from a traditional domain. It is not an LDAP compatible directory store and uses a different API. It has reduced functionality so It cannot authenticate users. Authentication must come from another source like ADFS orWindows Integrated Authentication.

1. **Security System:** Select Active Directory from the dropdown.

## General

1. **Authority URL:** Enter the URI for your directory.&#x20;
   * Often this is [https://login.microsoftonline.com/](https://login.microsoftonline.com/) followed by the tenant name. This may not be the case for some types of Office 365 e.g. Educational or Governmental.
2. **Credential:** Choose the relevant credential for this token from the dropdown.
3. **Scopes:** Enter the scopes requested to access a protected API. Example scope form, ResoucreUri/.default.
4. **Featured Domain Name:** Enter the old style NETBIOS domain name.&#x20;
   * This will be used when qualifying synced objects from an on-premise domain.
5. **Managed Domain Name:** Enter the Azure Domain Name.&#x20;
   * This will get qualifying objects created from Azure Active Directory.

***

## Groups Sync

This filter will be used when synchronising groups. Use the filter parameter syntax to retrieve a subset of a collection based on its properties. [Support for creating a Parameter Syntax](https://learn.microsoft.com/en-us/graph/filter-query-parameter?tabs=http) and [How to determine group sync properties](https://learn.microsoft.com/en-us/graph/api/resources/group?view=graph-rest-1.0#properties).&#x20;

Only synchronise security enable groups is a predefined filter equal to (securityEnabled eq true). Enable this to synchronise only groups that can be used to secure access.

<figure><img src="../../../../../.gitbook/assets/Screenshot 2023-02-13 at 16.37.36.png" alt=""><figcaption></figcaption></figure>

***

## Users Sync

The user sync area should be used to filter in and out users from synchronising and also adding group.

1. **Users Filters:** Create filters used when synchronising users to Aiimi Insight Engine. Create the filters using Parameter Syntax.
2. **Synchronise Checkbox Setting:** Control what users synchronise by checking either:
   * Synchronise federated (on-premise) users.
   * Synchronise managed (Azure AD) users.
     * All users will be synced, including some users that are neither federated or managed when neither are ticked.
3. **Only Synchronise Licensed Users:** Check this to filter out any expired accounts.&#x20;
   * This is a predefined filter equivalent to (accountEnabled eq true).
4. **Only Synchronise Enable Users:** Check this to filter out users without an Office 365 license.

<figure><img src="../../../../../.gitbook/assets/Screenshot 2023-02-13 at 16.38.28.png" alt=""><figcaption></figcaption></figure>

5. **Additional Group:** You can add a user group to Additional Groups. This must include the appropriate qualifier.
6. **Excluded Groups:** Enter any groups from users that you want to remove. This must include the appropriate qualifier.
