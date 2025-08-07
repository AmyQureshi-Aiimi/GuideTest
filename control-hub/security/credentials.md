# Credentials

Within the Control Hub you can manage all the credentials needed from one centralised place. The credentials are used for the configurations and are assigned during their creation or editing.

## New Credentials

1. Select New Credential.
2. Select the Credential Type.
   * Choose between Username and Password, Client ID and Secret, Secret Only, Certificate.
   * Certain configurations need certain types of credentials.

### Username and Password

1. **Credential ID** - Enter an ID for this credential.
2. **Credential Name** - Enter a user friendly name for this credential.
3. **Username** - Enter the Username that is needed for access.
4. **Password** - Enter the password needed for this credential.
   * This will show a single dot once entered for security.&#x20;
5. **Notes** - Add any information that can help identify what it can be used for.
   * Do not put the password or any clues here.
6. **Expiry Date** - Enter an Expiry Date for this credential.
   * This date will be used as a reminder that it needs updating. Even when it has expired it will continue to be used.&#x20;
7. Select Create.

<figure><img src="../../.gitbook/assets/image (84).png" alt="" width="563"><figcaption></figcaption></figure>

### Client ID and Secret

1. **Credential ID** - Enter an ID for this credential.
2. **Credential Name** - Enter a user friendly name for this credential.
3. **Client ID** - Enter the Client ID that is needed for access.
4. **Secret** - Enter the secret needed for this credential.
   * This will show a single dot once entered for security.&#x20;
5. **Notes** - Add any information that can help identify what it can be used for.
   * Do not put the secret or any clues here.
6. **Expiry Date** - Enter an Expiry Date for this credential.
   * On this date the credential will no longer be used.
7. Select Create.

<figure><img src="../../.gitbook/assets/image (83).png" alt="" width="563"><figcaption></figcaption></figure>

### Secret Only

1. **Credential ID** - Enter an ID for this credential.
2. **Credential Name** - Enter a user friendly name for this credential.
3. **Client ID** - This will display N/A and cannot be edited.
4. **Secret** - Enter the secret needed for this credential.
   * This will show a single dot once entered for security.&#x20;
5. **Notes** - Add any information that can help identify what it can be used for.
   * Do not put the secret or any clues here.
6. **Expiry Date** - Enter an Expiry Date for this credential.
   * On this date the credential will no longer be used.
7. Select Create.

<figure><img src="../../.gitbook/assets/image (82).png" alt="" width="563"><figcaption></figcaption></figure>

### Certificate

1. **Credential ID** - Enter an ID for this credential.
2. **Credential Name** - Enter a user friendly name for this credential.
3. **Client ID** - This will display N/A and cannot be edited.
4. **Password** - Enter the password needed for the certificate.
   * This will show a single dot once entered for security.&#x20;
5. **Notes** - Add any information that can help identify what it can be used for.
   * Do not put any clues here.
6. **Expiry Date** - Enter an Expiry Date for this credential.
   * On this date the credential will no longer be used.
7. **Import Certificate** - Drag and drop the certificate file or select browse files to find it within your file explorer.
   * The cert file must be a one of the following supported certificates:
     * `application/x-pkcs12` - .pfx or .p12
     * `application/pkix-cert` - .cer
     * `application/x-x509-ca-cert` - .cert
8. Select Create.

<figure><img src="../../.gitbook/assets/image (81).png" alt="" width="563"><figcaption></figcaption></figure>

***

## Find a Credential

You can find all your credentials within the Control Hub credentials space.

### Searching for a Credential

1. Select the search bar on the credentials page.
2. Enter any part of a credential except the password to find it.
   * As you type within the search the list will start to refine.
   * When you enter a search it will look at all the fields including the notes and what it is used by but not the password.

### Sorting Credentials

#### Credentials

Select the triangles or the table heading 'Credentials' to sort the table in alphabetical order. Credentials will be sorted based on the user friendly name.

* Select it once to order them reverse alphabetically Z - A.
* Select it again to order them alphabetically A - Z.

To reset the list order refresh the page.

#### Expiry Date

Select the triangles or the table heading 'Expiry Date' to sort the table in date order.

* Select it once to order them longest time left to shortest time left, then expired.
* Select it again to order them expired, shortest time left then longest time left.

To reset the list order refresh the page.

***

## Edit a Credential

You can edit any part of a credential except the Credential ID. This is helpful when Passwords or Usernames need updating.

1. Find the credential you need to edit.
2. Select the action menu of that credential (Ellipses).
3. Select Delete from the menu.
   * This will open an edit credential modal.&#x20;
4. Edit the fields you need to change.
   * If you need to change the Credential ID you need to create a new credential.&#x20;
5. Select Save.

Any sources using an edited credential will automatically use the edited details once saved.

<figure><img src="../../.gitbook/assets/image (874).png" alt="" width="563"><figcaption></figcaption></figure>

***

## Delete a Credential

Credentials can only be deleted if they are not being used by a configuration. Within the Credentials table you can see if it is being used and by what in the Use By column.

1. Find the credential you want to delete.
2. Select the action menu of that credential (Ellipses).
3. Select Delete.
   * This will open a modal for you to confirm you want to delete this credential.&#x20;
   * If you delete the wrong credential you will need to create it again as a new credential.&#x20;

<figure><img src="../../.gitbook/assets/image (579).png" alt="" width="563"><figcaption></figcaption></figure>
