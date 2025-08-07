# Adding or Changing Entities, Metadata

A very common task that you can use a Python enrichment step to do is add or edit metadata or entity values.

To do this, first ensure the metadata item or entity exists in Control Hub and is of the right data type. For example:

<figure><img src="../../.gitbook/assets/image (410).png" alt=""><figcaption></figcaption></figure>

Let’s edit our example to add an ‘ner person’ entity (note that entity groups are always camel case and not upper case as shown in Control Hub).

Note the line that adds the ‘ner’ group and then adds the ‘person’ list to it.

```
def do_example(work):  
    print("BEFORE:")
    print(work)
    print()

    # add your code here to manipulate the EnrichmentWorkItem structure
    logging.info("Generating example for: %s", work['File']['Name'])
    work['File']['TextContent'] += ' - ' + example_lib_function(example_config["text"])
    work["File"]["Entities"]["ner"] = {}
    work["File"]["Entities"]["ner"]["person"] = [ "Paul Maker", "Steve Salvin" ]
    print("AFTER:")
    print(work)
    return work
```

We can also test this from main by setting up our work item as required with entities.

```
if __name__ == "__main__":
    text_content = "This is some test text"
    work = {}
    work["File"] = {}
    work["File"]["Name"] = "Test Document.txt"
    work["File"]["Extension"] = "txt"
    work["File"]["TextContent"] = text_content
    work["File"]["Entities"] = {}
    work["File"]["Entities"]["ner"] = {}
    do_example(work)
```

If we add a new document, or update the test document and re-run the crawl and then re-run the enrichment pipeline we should see the following in Aiimi Insight Engine.

<figure><img src="../../.gitbook/assets/image (548).png" alt=""><figcaption></figcaption></figure>

Here we can see our ner person entities in Aiimi Insight Engine document details page for the search result.
