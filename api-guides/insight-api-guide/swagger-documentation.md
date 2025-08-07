# Swagger Documentation

Workplace AI is configured out of the box to provide dynamic Swagger documentation. This documentation allows you to inspect the API endpoints and test them.

To access the Swagger documentation open a browser and navigate to:

* [swagger.aiimi.cloud](http://swagger.aiimi.cloud)
* Replace the server address with that or your Workplace AI instance.

### Authentication

To authenticate you need to send your username and password to the login endpoint and get a bearer token. This bearer token is then sent with all subsequent requests.

<figure><img src="../../.gitbook/assets/image (591).png" alt=""><figcaption></figcaption></figure>

You should see the following response:

<figure><img src="../../.gitbook/assets/image (635).png" alt=""><figcaption></figcaption></figure>

You will need to copy the response body which contains the bearer token and add it with the authorise button (be sure to copy just the token and not the surrounding quotes).

<figure><img src="../../.gitbook/assets/image (461).png" alt=""><figcaption></figcaption></figure>
