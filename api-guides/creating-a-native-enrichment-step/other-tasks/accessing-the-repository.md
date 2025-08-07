# Accessing the Repository

You may want to access other indexes from your enrichment step, perhaps to look up values before assigning values to the current work item.

To do this you will need to create an InsightMaker Elasticsearch context.

```
var elasticContext = new ElasticContext(LocalConfigurationManager.Elastic);
elasticContext.Connect();
string index = elasticContext.PrefixedIndexName("my_lookup_index");
Then you can issue searches against a source.
var response = elasticContext.Client.Search<IndexedFile>(s => s
                    .Index(index)
                    .From(0)
                    .Size(10)
                    .Query(q => q.Terms(c => c.Field("my_field").Terms(values)))
                    .SearchType(SearchType.DfsQueryThenFetch));
```

You can obtain more detailed guide on search syntax from the Elasticsearch NEST documentation.

Note that you will want to add an appsettings.json file to your console app that contains connection details for Elasticsearch if you want to test the step.

```
{
  "elastic": {
    "server": [
      "https://localhost:9200"
    ],
    "username": "elastic",
    "password": "changeme",
    "prefix": "dev",
    "enableTracing": false,
    "certificate": {
      "path": "C:\\elasticsearch-6.6.0\\config\\certs\\elastic-stack-ca.p12",
      "password": "changeme"
    }
  }
}
```

