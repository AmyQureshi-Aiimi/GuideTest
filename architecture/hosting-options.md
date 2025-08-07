# Hosting Options

Aiimi Insight Engine can be hosted in several ways depending on your preferences and IT set up.&#x20;

## On-Premises <a href="#toc126235859" id="toc126235859"></a>

{% hint style="info" %}
This requires servers or virtual machines that can host the right Windows Server or Linux.
{% endhint %}

The platform can be hosted on-premises in your data centre. This is best if all agent servers, repositories and web servers also run on local servers.&#x20;

***

## Cloud

The platform can be hosted in the cloud using any provider that offers PaaS.&#x20;

This is best if all agent servers, repositories and web servers also run on cloud-based servers. We can accommodate all of the main cloud platforms, Including but not limited to, Amazon AWS, Microsoft Azure and Google Compute Platform.&#x20;

Using cloud platforms can simplify scaling, especially for the repository tier. This is great if you need more Elasticsearch nodes as the volume of data grows, or demand increases.

***

## Hybrid

The best solution if you have information on the cloud and on-premises servers.&#x20;

Putting source, content, and enrichment agents on-premises can improve the discovery and enrichment time. It is helpful for large on-premise sources such as SharePoint or network file systems. Some have on-premises agents for certain source systems and cloud agents for their cloud sources.&#x20;

Running the repository, API and User Interface in the cloud, can make scaling easy. It can also make end-user access easy since users do not need to be on the corporate network/VPN. _This depends on the security needed for Aiimi Insight Engine and how users access the platform._

#### A common hybrid configuration

* The agents are run on-premises.
* The repository and web components are run on the cloud.&#x20;
