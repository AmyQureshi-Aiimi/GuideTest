# Alfresco Kafka

Connect Alfresco and Kafka to Aiimi Insight Engine to make the most of your  data.

## Kafka

1. **Kafka Servers:** Enter the Kafka server URLs you want to connect to.&#x20;
   * You can include ports if needed.&#x20;
   * Use commas to separate multiple values.&#x20;
2. **Application ID:** Enter a unique ID for this source connector.
   * Kafka uses this to manage the messages consumed by the connector. This stops repeat messages being replayed and ensures only new messages are consumed.&#x20;

{% hint style="info" %}
Changing this once the connector is running will have unintended side effects.
{% endhint %}

3. **Topic Name:** Enter the Kafka queue name you want to watch for messages.
4. **Site ID:** If you only need to crawl one site, enter the hyphenated site ID.
   * For example: alfresco-site.
5. **Process Records From:** Enter a date to only process messages after that date.  Anything before this date will be ignored.
6. **Process Queue Limit:** Enter the maximum number of batches that can be processed at one time.
   * This can be adjusted to tune the performance of a deployed environment.
7. **Queue Batch Size:** Enter the maximum number of messages that will be processed together from a queue.
   * If that number isn't reached within 60 seconds a partial batch will be processed.
8. **Message Logging Enabled:** If checked, the result of every Kafaka message will be logged. It identifies if an item is added to the queue for processing and if it isn't then the reason why is logged.

<figure><img src="../../../../../.gitbook/assets/image (101).png" alt="" width="563"><figcaption></figcaption></figure>

***

## Alfresco

1. **Instance Name:** Enter the instance name to ensure it connects to the correct version.
   * This is important when you have multiple versions of Alfresco running and logging messages to Kafka.&#x20;
2. **Select Credential:** Select the Alfresco API Username and Password from the dropdown.
   * This will need suitable service account privileges to access everywhere document are stored.&#x20;
   * _For support setting up credentials use_ [_our guide on managing credentials._](../../../../security/credentials.md)
3. **Root Domain:** Enter the root domain for the instance you are connecting to.&#x20;
   * The root domain contains the multiple endpoints that need to be hit.
4. **Domain Prefix:** Enter the AD domain to prefix Groups and Users with when permissions are applied.&#x20;
   * The separating \ is automatically applied.
5. **Parallel API Calls:** Enter the maximum number of concurrent API calls that can be made to Alfresco.&#x20;
   * This can be adjusted to tune performance depending on the environment.
6. **Result Path Prefix:** Enter the string value that should be removed the Path displayed in the Result detail page.&#x20;
   1. This defaults to "/Company Home/Sites".
7. **Security Markings Enabled:** Check this to match any Alfresco security markings to configured security descriptors in Aiimi Insight Engine.&#x20;
   * This will apply permissions to items within Aiimi Insight Engine.&#x20;
8. **Lowercase Permissions:** Check this to allow the permissions to be stored in Elastic with optional lowercasing.
9. **Use Alfresco Groups:** Check this if Alfresco does not use AD groups to control permissions. It ensures queries are made to get the specific Users attached to an Alfresco Group.

<figure><img src="../../../../../.gitbook/assets/image (102).png" alt="" width="563"><figcaption></figcaption></figure>
