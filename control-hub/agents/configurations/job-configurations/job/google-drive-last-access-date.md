# Google Drive Last Access Date

This job calculates and updates the last accessed date for files indexed by the Google Drive Connector.

### Prerequisites <a href="#prerequisites" id="prerequisites"></a>

* A Google Directory Secondary Security Sync is run using the Google Directory Secondary Security Sync plugin.
* An initial crawl is run using the Google Drive Connector plugin.
* The Last Accessed Date Job must be configured to use the same Google Directory Secondary Security Sync and Google Drive Connector configurations.
* A service account associated with the relevant project is needed to perform tasks for the connector.

### Source <a href="#source" id="source"></a>

1. **Source Configuration** - Enter the ID of the source configuration the job will extract data from.
2. **Drive Source Configuration -** Enter the ID of the Google Drive source the job will apply extracted data to.

<figure><img src="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FzxkNZKiPvsadhOX6ove1%2Fuploads%2FKLUVKMt4nN39NS94d1gX%2Fimage.png?alt=media&#x26;token=12304b6d-7e3e-4331-b470-4c2a1aa16011" alt="" width="563"><figcaption></figcaption></figure>

### Security <a href="#security" id="security"></a>

1. **Security Configuration** - Select the Google Security Sync you want to use for this job.

<figure><img src="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FzxkNZKiPvsadhOX6ove1%2Fuploads%2FtflCFzjYDkIvUj787vcG%2Fimage.png?alt=media&#x26;token=0bb4043a-6e96-483a-8ccf-d3b9a78e11de" alt="" width="563"><figcaption></figcaption></figure>

### Mappings <a href="#mappings" id="mappings"></a>

1. **The Data Model ID -** Enter the ID of the data model to use.
2. **Last Accessed Date Attribute ID -** Enter the ID for the data models Last Accessed Date attribute.
3. **Last Accessed Email Attribute ID -** Enter the ID for the data models Last Accessed Email attribute.
4. **Creator Attribute ID -** Enter the ID for the data models Creator Email attribute.

<figure><img src="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FzxkNZKiPvsadhOX6ove1%2Fuploads%2F6icnaw97oqQBXnEWZrNj%2Fimage.png?alt=media&#x26;token=a9ff3fca-4c35-414e-8e94-3299ed1a969d" alt="" width="563"><figcaption></figcaption></figure>

### Advanced <a href="#advanced" id="advanced"></a>

1. **Parallel Folder Crawling** - Enter the maximum number of folders that can be processed at the same time.
2. **Batch Size** - Enter the maximum number of files that can be retrieved from Google Drive per batch.

<figure><img src="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FzxkNZKiPvsadhOX6ove1%2Fuploads%2FGNE06sWN0ENrw350S58Q%2Fimage.png?alt=media&#x26;token=22284ee2-5296-4669-9ba3-c211f493e77d" alt="" width="563"><figcaption></figcaption></figure>
