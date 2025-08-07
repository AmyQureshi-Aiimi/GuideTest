# Gateway (Web Server)

## Gateway Security Considerations

### Necessary Gateway Network Access

* Access to all agent servers.
* Access to any respective agent services.
* Access to the Elasticsearch cluster – [Read more about Workplace AI Firewalling.](firewalling.md)

### Internet Information Services Config or Apache Server Account Needs

* Read access to the Apps folder on your deployment.
* Read/write access to the Logs folder on your deployment.
* Read access to the certificates used to secure communications with Elasticsearch.

### Other Considerations

* From a defence in depth perspective the account should have the minimum privileges required to run the apps.
* End user access should be secured over HTTPS with a valid certificate for production deployments. **Not self-signed.**
* You can lock the Control Hub down to specific IP addresses.&#x20;
  * For example a remote desktop host. This provides additional security over and above the authentication required to access the app.
    * To do this you must lock the admin and the API sub-folder down to specific IP addresses.
