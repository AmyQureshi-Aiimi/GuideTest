# Migration Agent

The migration agent is a separate service that migrates the content from one system or location to another. It relies on a source and target for the migration.

* The source is the content to be migrated. It will be an index created from a source agent crawl.
* The target is a source configuration telling the migration how to add the content to the target system.

### Configuring a Migration

* The source index
* Any filters applied on the index to get a list of content to migrate
* Metadata mappings of everything from the source to the target system
* A schedule for when the migration agent runs

### Migration Test

Migrations are tested by migrating a defined number of documents from the source to the target system. This tests connectivity, metadata mappings and validates the migration is ready to run.

### Migration Schedule

A migration will run on a user defined schedule. It will stop and start as required so it doesn't impact business hours. For example, it could run after 7pm weekdays until 6am and all day on weekends.
