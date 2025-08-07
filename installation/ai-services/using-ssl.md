# Using SSL

The AI Services use a Python library called Waitress, which does not support HTTPS/SSL. We recommend using Waitress with a reverse proxy for SSL.

## Reverse Proxy

To enable SSL you need to configure a reverse proxy with SSL and proxy requests through to the AI Services.

You can either use the Windows IIS reverse proxy module, or something like NGINX on Linux. Please consult the respective documentation to set this up.

***

## CherryPy

The AI Classification, Enrichment and Model services now support CherryPy as an alternative to Waitress where SSL hosting is required. To run CherryPy, serverCerts, serverCertsPassword and serverPrivateKey are required. This information lives in the config/config.json file for the respective services.

{% hint style="info" %}
You will need to update the service registration to use https. This can we done by updating your`config/config.json` and restarting the service.&#x20;
{% endhint %}
