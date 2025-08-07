# Delivery Settings

## General

Enter the details of the email provider and how it ill be connected to.&#x20;

1. **Email Providers -** Select your Email Provider from the Dropdown list.&#x20;
   * Choose between SMTP and Exchange Online.

### SMTP Provider

1. Select the credential and secret needed to access the provider from the Select Credential dropdown list.
2. Enter the email that all emails will be sent from within From Address.
   * This must be a valid email address.
3. Enter the SMTP host server address within Host.
   * For example smtp.gmail.com
4. Enter the Port for the SMTP server within Port.
5. Enter a HELO Message that will be used to start communication with the server.
   * Usually made up of the Domain Name and IP address of the SMTP client.
   * For example HELO client.example.com.
6. Check SSL Authentication Enabled if the server requires SSL.

<figure><img src="../../../../.gitbook/assets/image (641).png" alt=""><figcaption></figcaption></figure>

### Exchange Online Provider

1. Select the credential and secret needed to access the provider from the Select Credential (Client ID / Secret) dropdown list.
2. Select the username and password needed to access the provider from the Select Credential (Username / Password) dropdown list.
3. Enter the email that all emails will be sent from within From Address.
   * This must be a valid email address.
4. Enter the host server address within Host.
   * For example https://outlook.office365.com/ews/exchange.asmx
5. Enter the Tenant ID within Tenant.&#x20;

<figure><img src="../../../../.gitbook/assets/image (656).png" alt=""><figcaption></figcaption></figure>
