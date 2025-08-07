# Active Directory

Synchronise users and groups from your Active Directory into Aiimi Insight Engine.

1. **Security System:** Select Active Directory from the dropdown.

## General

Add the details for the server including credentials and domain names.

1. **Server:** Enter the Server URL without the protocol at the beginning.
   * For example Server.domain.local
2. **Port:** Enter the Port to use on the directory server.
3. **TLS:** Check this for end to end security through a cryptographic protocol.
4. **Verify Certificate:** Uncheck this to allow self assigned certificates.&#x20;

{% hint style="danger" %}
This will reduce the security of Aiimi Insight Engine.
{% endhint %}

5. **Credential:** Choose the server credential to use from the dropdown.
6. **Authentication Type:** Assign the Authentication Type from the list.

<figure><img src="../../../../../.gitbook/assets/Screenshot 2023-02-13 at 16.59.00.png" alt="" width="563"><figcaption></figcaption></figure>

8. **Domain Name:** Enter a domain name.
   * If left blank the connector will take this from the Active Directory.
9. **Old Style Domain Name:** Enter an Old Style Domain Name.
   * If you are using the old style the Use old-style domain names must be checked.
10. **Limit Search Scope:** Check this to add a control object to paged LDAP searches.
    * Only uncheck this if your service does not support this.
11. **Skip Manager Lookup:** If checked the manager for users will not be searched.
12. **Group Lookup:** Check this to skip any group lookup for a user.
13. **Query Primary Groups:** Check this if a groups direct members are needed.&#x20;
    * This will run an additional query on every group to get any objects that list the group as their primary group.

<figure><img src="../../../../../.gitbook/assets/Screenshot 2023-02-13 at 17.00.42.png" alt="" width="563"><figcaption></figcaption></figure>

***

## Group Sync

Set the parameters that are used when syncing with groups.

1. **Groups Path:** Enter the directory location of the groups to sync.
2. **Groups Filters:** Enter any filters to be applied when searching for groups.&#x20;
   * This will ignore any unnecessary groups or find groups based off their properties.

<figure><img src="../../../../../.gitbook/assets/Screenshot 2023-02-13 at 17.01.52.png" alt="" width="563"><figcaption></figcaption></figure>

***

## Group Mappings

Match up the Aiimi Insight Engine property with the AD Field Name. If you have any variation in naming make sure they are updated within the AD Field Name field.&#x20;

<figure><img src="../../../../../.gitbook/assets/Screenshot 2023-02-13 at 17.29.29.png" alt=""><figcaption></figcaption></figure>

***

## User Sync

Enter the details to locate users that need syncing. This is filled in by default and only needs changing if your Active Directory settings are different.

1. **Users Path:** Enter the Directory Location for the Users that need to sync.
2. **Users Filters:** Enter any filters that need to be used when searching for users.
3. **Additional Group Membership:** Add users to groups for Aiimi Insight Engine only.&#x20;
   * This will not change any settings in your Active Directory.&#x20;
   * Any groups added here will not be domain verified.
4. **Excluded Group memberships:** Add groups here to remove them from a users membership.
   * Any groups added here will not be domain verified.
   * This will not change any settings in your Active Directory.&#x20;
5. **Unknown Domain SID Prefixes:** For members in unknown domains enter the SID Prefix to look them up.

<figure><img src="../../../../../.gitbook/assets/Screenshot 2023-02-13 at 17.30.06.png" alt=""><figcaption></figcaption></figure>

***

## User Mappings

Within User Mappings match up the Aiimi Insight Engine properties with the AD Field Name. Most of these should stay the same across all systems. If you have any variation in naming make sure they are updated within the AD Field Name field.&#x20;

<figure><img src="../../../../../.gitbook/assets/Screenshot 2023-02-13 at 17.28.48.png" alt=""><figcaption></figcaption></figure>

***

## Trusted Domains

1. **Left Field:** Add any LDAP servers that should be checked for group membership. These servers should be in the same forest, with the same login details from General.
2. **Right Field:** Enter the NETBIOS domain name for this server's tree.
   * This is a precaution incase the plugin cannot directly determine it.

Select the Cross to remove a domain and the Check to add a new Domain.

<figure><img src="../../../../../.gitbook/assets/Screenshot 2023-02-13 at 17.27.07.png" alt=""><figcaption></figcaption></figure>
