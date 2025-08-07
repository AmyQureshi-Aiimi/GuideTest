# Authentication

Configure the authentication method best for your business. You can use Windows, SAML 2 or ADFS to authenticate Workplace AI. There are also some additional authentication security features that can be used in dev or test environments.

## Windows Authentication

Use Windows Authentication to authenticate objects, services and users. It will help verify how genuine an object is and for services and people that the credentials are authentic.

1. Check Windows Authentication to use Windows Authentication.

<figure><img src="../../.gitbook/assets/image (675).png" alt=""><figcaption></figcaption></figure>

***

## SAML2 Authentication

SAML2 is an open standard that allows single sign-on (SSO) of applications. It is used to authenticate a user and allow them to gain access to Workplace AI.&#x20;

1. **SAML 2 Authentication** - If checked SAML2 will be used for Workplace AIs Authentication.
2. **Application identifier** - Enter the identifier of the Application in the identity provider.
3. **Issuer** - Enter the issuer of the Identity Provider.&#x20;
4. **Sign On URL** - Enter the endpoint URL for signing in to the authenticator.
5. **Logout URL** - Enter the endpoint URL for logging out of the authenticator.
6. **App URL** - Enter the endpoint for Workplace AI Search application that will complete the login.&#x20;
   * Use {0} as a placeholder for the host and port to access the API.
7. **Signature Validation Certificate** - Enter the filepath for the public certificate used to validate token signatures.&#x20;

<figure><img src="../../.gitbook/assets/image (52).png" alt="" width="563"><figcaption></figcaption></figure>

***

## ADFS

Workplace AI supports ADFS for single sign on. A private key needs to be generated and network changes are required before ADFS is enabled. The copy of the certificate will need to be added to each server running IIS and hosting Workplace AI.&#x20;

1. Check Enable ADFS Authentication use ADFS.&#x20;
2. **ADFS URL** - Enter the ADFS URL.
3. **Redirect URL** - Enter your Redirect URL.&#x20;
4. **Certificate Path** - Enter the path to the certificate/private key.
5. **Certificate Password** - Enter the password for your certificate.&#x20;

<figure><img src="../../.gitbook/assets/image (663).png" alt=""><figcaption></figcaption></figure>

***

## Security

{% hint style="danger" %}
These settings impact the safety, security and integrity if your system. Proceed with caution.
{% endhint %}

### Enable Swagger API Documentation

Get information about your APIs during development and testing. This exposes your API details and should only be enabled in dev or test environments. To use Swaggers inbuilt testing the Bearer Token Authentication must be enabled.

### Enable Bearer token authentication

Allow tokens to be stored in an auth header not just HTTP. This increases your security risk and should only be enabled in dev or test environments. This must be enabled to use Swaggers inbuilt testing.

### Valid logged out tokens

If enabled, logged out tokens will only be invalidated upon expiry. This is only recommended for dev or test environments.
