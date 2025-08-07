# Data and Document Security

There are a few ways you can control your data and document security. You can limit the data certain users can access, add flags for high risk items, anonymise information and much more.

## Access Controls

Fundamental to Workplace AI is the enforced access control rules. The access control rules dictate who can see a piece of data or content.

Users are members of groups, that are usually synchronised from an Active Directory. Every piece of data and content has a list of groups that can access it. When a user performs a search they will only see items where their group has the relevant permissions.

<img src="../../.gitbook/assets/image (648).png" alt="" data-size="original">

***

## Progressive and Privileged Access

The use of progressive and privileged access is fully audited and must be explicitly granted by an administrator.

### Progressive Access

If a user has been granted progressive access they can see items they can't access in their results list but, they won't be able to open them. They can request access to an item from the item's owner.

For more information [see our guide on application access.](../../control-hub/security/application-access.md)

{% hint style="info" %}
Progressive access is an optional feature and must be explicitly granted by an administrator.
{% endhint %}

### Privileged Access

Privileged access gives select users a controlled way to bypass permissions. Users with privileged access can see all search results even if they don’t have permission to access an item. Unlike progressive access, they will see the item, preview, and metadata.&#x20;

For more information [see our guide on application access.](../../control-hub/security/application-access.md)

{% hint style="info" %}
Privileged access is an optional feature and must be explicitly granted by an administrator. It is not available to any user by default​.
{% endhint %}

<figure><img src="../../.gitbook/assets/image (208).png" alt="" width="375"><figcaption></figcaption></figure>

***

## Source Scope and Visibility Within Apps

Sources represent either different repositories or areas of a repository. For example, you may have a source for SharePoint HR and SharePoint Asset.

* Control which sources are visible within each app of Workplace AI.
  * You can limit the application it is available within from the source configuration.&#x20;
  * If you disable a source in Enterprise Search, even if a user has permission to see the documents, they will never see this content via the Search app.
* Limit who can see and access a source anywhere in the application. Within a source's configuration, you can add which users and groups can access it.

For more information [see our guide on configuring a source.](../../control-hub/agents/configurations/source-configurations/)

<figure><img src="../../.gitbook/assets/image (894).png" alt="" width="563"><figcaption></figcaption></figure>

***

## Classification

Workplace AI can automatically classify data and content. This could be business classifications, such as types of accounts payable document, i.e., invoice, purchase order, goods receipts. Or it could be security classifications, such as public, internal, restricted and top secret.

Using classifications, you can also add additional controls like, who can see items, or where information can be sent. You can also use these classifications to help inform and automate information security policies.

For more information [see our guide on AI Studio Classifications](../../ai-studio/classifications/).

<figure><img src="../../.gitbook/assets/image (210).png" alt="" width="375"><figcaption></figcaption></figure>

***

## Advanced Security Controls

### Security Classifications

Security classifications allow you to apply additional security on top of the standard access control lists.

* Users are given the right to see one or more security classification.
  * For a user to have access they must have access via the standard access control list. Or they must have all the security classifications that appear on the data or content.
* Data and content may also have one or more security classifications applied.

<figure><img src="../../.gitbook/assets/image (464).png" alt="" width="375"><figcaption><p>An example of a user with the ‘secret’ classification and a corresponding document with the protective classification ‘secret'.</p></figcaption></figure>

### Risk Ratings

The Workplace AI can calculate the potential risk of a piece of data or content.&#x20;

It's based on the items PII data:&#x20;

* The number of people referenced
* Amount of personal information
* Visibility to your workforce
* Frequency of use
* Specific keywords that indicate risk

It's a key feature of our PII and DSAR solution. Risk ratings can also be used in a similar way to classifications, and used to restrict what people can see.

For more information on Risk Ratings see [our enrichment guide for Setting Document Risk. ](../../control-hub/agents/configurations/enrichment-configurations/creating-a-pipeline/steps/set-document-risk.md)

<figure><img src="../../.gitbook/assets/image (211).png" alt="" width="563"><figcaption></figcaption></figure>

### Redaction and Anonymisation

Redact the information in your documents within a SAR or Collection. You can redact specific parts like PII and PCI or select the sections of content you want to redact. The redacted items are only available on Workplace AI, the source is not affected.&#x20;

For support setting up redaction use [our guide on redacting information.](../../control-hub/global-settings/viewer.md#redacted-document-storage)

#### Automated Redaction

PII and other sensitive keywords can be auto removed using the anonymisation enrichment step.&#x20;

* For example, during enrichment, if a 'high-risk' piece of content is found it can be automatically anonymised.

For support creating an anonymiser see [our guide on the enrichment anonymiser.](../../control-hub/agents/configurations/enrichment-configurations/creating-a-pipeline/steps/anonymiser.md)

<figure><img src="../../.gitbook/assets/image (330).png" alt="" width="563"><figcaption></figcaption></figure>

### Banned Words

You can create a list of banned words, if these words appear in a document, the document is marked sensitive.

* Sensitive documents do not appear in a users results, even if they match a search.&#x20;

This feature is a useful safety guard against things that may end up in the wrong place. Typical banned words include things such as; p45, harassment, CV, Disciplinary etc.

### Mark as Sensitive

Users may find results in their search that they consider sensitive. They can manually mark a result as sensitive, it is temporarily hidden until it is investigated.&#x20;

This is a good way of crowd sourcing and quickly removing items that require review. Administrators can review files that have been marked as sensitive. They are reinstated if they are deemed not to a risk.

### Audit Controls

The actions of all users' are audited and stored in an audit log. It can be used to detect misuse, show the use and accuracy of the system and support advanced recommendation algorithms.&#x20;

The audit stores a users activity, what they searched, what they opened and if they have collaborated on a collection or DSAR.

<figure><img src="../../.gitbook/assets/image (325).png" alt="" width="563"><figcaption></figcaption></figure>
