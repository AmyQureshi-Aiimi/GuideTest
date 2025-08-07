# Source - Advanced

The advanced tab controls the permissions for the source. These fields are non-compulsory and can be ignored.

* **Primary Shards -** Choose the number of primary shards to use when creating indexes. If you are changing an existing indices, this will only take after a reindex.
  * The default number of replica shards is equal to the number of data nodes in the Elasticsearch Cluster.
* **Replica Shards -** Choose the number of replica shards to use when creating indexes. If you are changing an existing indices, this will only take after a reindex.
  * The default number of replica shards is equal to the number of data nodes in the Elasticsearch Cluster.
* **Number of Indexing Threads -** Enter the number of indexing operations allowed to run at the same time in the crawl.
* **Read Permissions to Add -** Choose the read permissions assigned to all documents.
* **Read Permissions to Remove -** Create a RegEx for read permissions that should not be assigned to the indexed document.
* **Write Permissions to Add -** Choose the write permissions assigned to all documents.
* **Write Permissions to Remove -** Create a RegEx for write permissions that should not be assigned to the indexed document.
* **Delete Permissions to Add -** Choose the delete permissions assigned to all documents.
* **Delete Permissions to Remove -** Create a RegEx for delete permissions that should not be assigned to the indexed document.
* **User and Group Access -** Restrict who can see and access this source throughout the application. Enter only the users and groups that should have access to this source.
  * If this is left blank, all users can see this source, even if the document count is 0.
  * Users with privileged access will not see this source unless they are added to the access list.
* **Clear Content, Entities and Metadata during delta Crawls -** Check this field to remove content, entities and metadata during a delta crawl.
* **Store Anonymised Content -** Anonymised content created during enrichment will be stored in Elastic when Checked. If the index exists, unchecking this will not remove it.
* **Track Versions -** For supported source types, check this to track versions.
* **Allow permission-less crawls -** If checked, the permissions of files will not be retrieved.&#x20;
  * This will improve performance, but impact security as permissions will not be tracked.
  * This is currently only available for Google Drive, FileSystem and SharePoint Crawls.

### **Content Management**

* **Allow Add Actions -** Check this field to allow add actions for this source.
* **Allow Update Actions -** Check this field to allow update actions for this source.
* **Allow Delete Actions -** Check this field to allow delete actions for this source.
* **Allow modify permission actions -** Check this field to allow modify permission for this source.
* **Action Timeout -** Enter the maximum number of seconds any Content Management Actions will wait for a client response.
  * The minimum is 100 seconds and the maximum is 500 seconds.

