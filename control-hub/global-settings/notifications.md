# Notifications

Aiimi Insight Engine can send notifications within the apps notifications area or to a users email. Notifications and alerts are based on a user’s permissions and role.&#x20;

Aiimi Insight Engine supports SMS notifications using the Pinpoint provider, however, you will need an account with Pinpoint to use this.

{% hint style="info" %}
You will need to configure the Notifications Processor Job to run notifications.
{% endhint %}

## General Configuration

1. **Notifications Interval (seconds)** - Choose how frequently Aiimi Insight Engine checks for new notifications. Enter the time between checks within Notification Interval in seconds.&#x20;
   * Having these too frequently can cause system performance problems.
2. **Record Events to enable User Notifications** - Check this to enable users to receive notifications.

<figure><img src="../../.gitbook/assets/image (613).png" alt="" width="563"><figcaption></figcaption></figure>

***

## Email Configuration

1. **Email Providers** - Choose the email provider to configure from the dropdown.

#### Exchange Online

1. **Select Credential (Client ID/Secret)** - Select the Client ID and the secret for the O365/Exchange Online configuration from the dropdown.
2. **Select Credential (Username/Password)** - Select the account and password that authenticates the specified mail server.
3. **From Address** - Enter the email address the notifications will come from.
4. **Host** - Enter the URI of the exchange service.
5. **Tenant** - Enter the ID of the tenant.
6. **Send Test Email** - Select this to send a test email to ensure emails send correctly.

<figure><img src="../../.gitbook/assets/image (284).png" alt="" width="563"><figcaption></figcaption></figure>

#### SMTP&#x20;

1. **Select Credential** - Select the Client ID and the secret for the server configuration from the dropdown.
2. **From Address** - Enter the email address the notifications will come from.
3. **Host** - Enter the SMTP server address of the exchange service.
4. **Port** - Enter the port for the SMTP server.
5. **HELO** - Enter A HELO Message to set the command for the SMTP server to initiate the SMTP conversation.&#x20;
   * The domain name or IP address of the SMTP client is usually sent as an argument together with the message (e.g. “HELO client.example.com”).
6. **SSL Authentication** - Check this if the email server requires SSL.
7. **Send Test Email** - Select this to send a test email to ensure emails send correctly.

<figure><img src="../../.gitbook/assets/image (269).png" alt="" width="563"><figcaption></figcaption></figure>

***

## SMS Configuration

1. Enable SMS notifications - Check this If you want to send SMS notifications.
2. **SMS Providers** - Select Pinpoint from the dropdown.
   * We only support Pinpoint as an SMS provider at the moment.
3. **Application ID** - Enter your Amazon Pinpoint Application ID.
4. **Select Credential** - Select the Client ID and the secret for the configuration from the dropdown.
5. **Region** - Enter the Region your Amazon Pinpoint server is hosted.
6. **Message Type** - Choose the Message Type from the dropdown.&#x20;
   * Transactional messages should be used for time sensitive applications such as recovery or login codes.
   * Promotional messages should be used for non critical messages such as marketing messages.
7. **Send Test SMS** - Select this to send a test SMS to ensure messages send correctly.

<figure><img src="../../.gitbook/assets/image (320).png" alt="" width="563"><figcaption></figcaption></figure>
