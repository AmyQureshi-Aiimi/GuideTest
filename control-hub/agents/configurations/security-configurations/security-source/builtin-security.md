# Builtin Security

{% hint style="warning" %}
This should not be used for Test or Production systems.
{% endhint %}

The Builtin Security Synchroniser allows user security principals to be retrieved from Elastic.&#x20;

* Users will not be kept in sync with the master security source.
* Need to be manually modified, disabled, deleted as roles change.
* Elastic security principals are not mapped to anything beyond Elastic.
* Passwords are not verified against any account and password policies.
* Passwords can not be managed unless using Kibana.

The Builtin Security Synchroniser uses Elastic to manage and authenticate non-reserves users. The native security realm contains users managed directly by Elastic. In LDAP or oauth2, users are synchronised from a third-party system.&#x20;

The plugin will synchronise all native Elastic users with the insightmaker\_user role. Management of users is via a command line.
