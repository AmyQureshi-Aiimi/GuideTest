# DocuSign

Connect your DocuSign system to Workplace AI to make the most of the data.&#x20;

## Prerequisites&#x20;

<details>

<summary>(1) A new integration key must be created within DocuSign's eSignature Admin Dashboard in the Apps and Keys section.</summary>

* This will be used by Workplace AI to authenticate you with your DocuSign organisation. It will need admin consent to impersonate users. The user and key for this integration are needed for configuration in Workplace AI.

For information on creating an integration key [see DocuSign's documentation, Add Integration Keys.](https://support.docusign.com/s/document-item?language=en_US\&bundleId=pik1583277475390\&topicId=lzz1583277395470.html&_LANG=enus) ([https://support.docusign.com/s/document-item?language=en\_US\&bundleId=pik1583277475390\&topicId=lzz1583277395470.html&\_LANG=enus](https://support.docusign.com/s/document-item?language=en_US\&bundleId=pik1583277475390\&topicId=lzz1583277395470.html&_LANG=enus))

</details>

<details>

<summary>(2) An RSA keypair must be configured for this integration. </summary>

* This is configured during the Service Integration creation. The private key of this pair should be stored as a secret-only credential within Workplace AI.&#x20;

For information on configuring an RSA keypair [see DocuSign's documentation, Add Integration Keys.](https://support.docusign.com/s/document-item?language=en_US\&bundleId=pik1583277475390\&topicId=lzz1583277395470.html&_LANG=enus) ([https://support.docusign.com/s/document-item?language=en\_US\&bundleId=pik1583277475390\&topicId=lzz1583277395470.html&\_LANG=enus](https://support.docusign.com/s/document-item?language=en_US\&bundleId=pik1583277475390\&topicId=lzz1583277395470.html&_LANG=enus))

</details>

<details>

<summary>(3) Prove ownership of the domain that matches your users email.</summary>

* To do this your DocuSign account must have the SSO feature available, It does not need to be installed. This is setup through the organisation admin panel within DocuSign.

For information on making SSO available [see DocuSign's documentation Basic steps to setting up SSO.](https://support.docusign.com/s/document-item?language=en_US\&bundleId=rrf1583359212854\&topicId=ozd1583359139126.html&_LANG=enus) ([https://support.docusign.com/s/document-item?language=en\_US\&bundleId=rrf1583359212854\&topicId=ozd1583359139126.html&\_LANG=enus](https://support.docusign.com/s/document-item?language=en_US\&bundleId=rrf1583359212854\&topicId=ozd1583359139126.html&_LANG=enus))

</details>

<details>

<summary>(4) The integration must have administrative consent to impersonate users and retrieve their stored documents. </summary>

This is setup through the Connected Apps within DocuSign.

For information on authorising application [see DocuSign's documentation Authorize an Application](https://support.docusign.com/s/document-item?language=en_US\&bundleId=rrf1583359212854\&topicId=dnl1583359204821.html&_LANG=enus). ([https://support.docusign.com/s/document-item?language=en\_US\&bundleId=rrf1583359212854\&topicId=dnl1583359204821.html&\_LANG=enus](https://support.docusign.com/s/document-item?language=en_US\&bundleId=rrf1583359212854\&topicId=dnl1583359204821.html&_LANG=enus))

</details>

***

## Connection Settings

1. **DocuSign Base API:** Select which DocuSign API should be used for this crawl&#x20;
   * This is typically left as production unless you are testing with a demo environment.
2. **Integration ID:** Enter the ID of the API integration created as part of prerequisite 1.
3. **Select Credential:** Select the Secret-only credential with the RSA private key created as part of prerequisite 2.
   * _For support setting up credentials use_ [_our guide on managing credentials._](../../../../security/credentials.md)
4. **Admin Account ID:** Enter the admin user ID to use when authenticating this crawl.
5. **API Account ID:** Enter the account ID containing the integration created above.&#x20;

<figure><img src="../../../../../.gitbook/assets/image (186).png" alt="" width="563"><figcaption></figcaption></figure>

***

## Completed the Source section&#x20;

1. Once you have completed this section, select Crawl. [Learn how to complete the source Crawl set up.](../source-crawl.md)

