# Security Agent

The security agent has two main services:

1. Synchronise users, groups and user information from identity systems such as Active Directory.
2. Authenticate users when they access the end user apps.

### Synchronisation Plug-ins

Synchronisation is provided by a series of plug-ins, several are provided out of the box.&#x20;

At the time of writing these are: Active Directory, Azure Active Directory, OpenText Content Server and Workplace AI Built-In Accounts.&#x20;

> Aiimi, our customers and partners can create security plugins using the Microsoft.NET framework. The only limitation is the given user must be the same across all security repositories.

### Synchronisation Schedule

Synchronisation runs on a defined schedule. Generally this is once a day, usually overnight but can be more or less frequent.&#x20;

The time taken to complete a synchronisation will depend on the number of users and groups.

### User Authentication

User authentication is handled by an API call that the security agent exposes. It is then called by the gateway layer (end user apps **do not** call this directly).

#### Single sign-on

Single sign-on options are available and users are not prompted for credentials. A call is still made to the security agent to fetch the user’s details.

> If you are unsure what is best for your organisation your contact at Aiimi will be able to help.
