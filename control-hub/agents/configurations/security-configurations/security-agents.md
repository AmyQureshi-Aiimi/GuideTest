# Security - Agents

The Security Agent is primarily responsible for authentication and security within Workplace AI.

### Permissions for Elastic

It generates a list of domain users and groups from an Active Directory that is stored in Elastic. You can find these users, groups and permissions within Elastic under security principals and security group indices.

### Workplace AI Login

It also handles logging in to Workplace AI. The submitted username is checked against all stored security principals (users) to find a match. The Security Agent then passes to the configured Active Directory to verify the password.

{% hint style="info" %}
It is not involved when using ADFS or Windows Auth to login.&#x20;
{% endhint %}

## Security Agent Tab

* Simply select the Agent you want to use from the Agents Tab.&#x20;
