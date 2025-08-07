# Gateway and User Interface

The gateway provides authentication and authorisation services controlling what users can do. The authorisation aspects control the functionality, data and document users can see. This is controlled through permission trimming.

As standard the control hub communicates with all the repositories and agents. The Insight app also communicates with the repository, security agent and source agent. The communication with all components is through the gateway API.

### Gateway hosts

APIs and apps are hosted on Internet Information Services (IIS) on a Windows operating system or Apache on Linux. The APIs are used by any app that interacts with Workplace AI.

* Insight API
* Insight App
* Data Science API
* Control Hub API
* Control Hub App

Aiimi provides a series of apps out of the box, these are single page HTML/CSS/JavaScript based apps. They are hosted on the same server as the API as they have a tiny resource need. They only need network bandwidth for the initial app download.

#### Example Internet Information Server configuration

<figure><img src="../../.gitbook/assets/image (434).png" alt=""><figcaption></figcaption></figure>
