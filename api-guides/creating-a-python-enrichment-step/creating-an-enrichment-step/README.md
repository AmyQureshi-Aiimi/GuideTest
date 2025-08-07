# Creating an Enrichment Step

The installation and configuration guide for the Python REST Service provides an excellent insight into the folder structure of the service and how it works. This guide will therefore focus on the things specific to creating a Python enrichment step.

### Example Enrichment Step

An example enrichment step ships with the Python REST Service, which provides a good starting point for a new enrichment step. This can be found alongside the other enrichment steps in the endpoints subfolder.

#### Walkthrough&#x20;

First we import the libraries that we require for the base functionality of a REST step, which include flask, logging, json and some os calls.

```
import flask
from flask import request, jsonify
import logging
import logging.config, yaml,logging
import json
import os
```

Next, we work out where we are in the folder tree. We do this so we can run the file both directly for development and debugging purposes, and from within the actual service. More will become clear about this shortly.

```
module_location = os.path.dirname(os.path.abspath(__file__))
```

The example makes use of a config file for some settings. The convention is to store these in the config sub-folder, although you do not need to do this.

```
config_file = open(module_location + '/../config/endpoints/example.json')
example_config = json.load(config_file)["example"]
config_file.close()
```

If we are running the file directly we configure logging and pull in our example library. If we are running within the REST Service then logging will be configured for us already.

```
if __name__ == "__main__":
    logging.config.dictConfig(yaml.safe_load(open(module_location + '/../config/logging.conf')))
    from example_libs.example_lib import *
else:
    from .example_libs.example_lib import *
```

You can define an initialise function which will be called on start up once. You can also simply include this code inline if you wish.

```
def initialise():
    logging.info('Example initialise code goes here')
```

The end point file must contain a function with the same name. Here we just chain onto a do\_\<endpoint> method which does the work. We do this to make testing easy (this will become clear shortly).

The request will contain the JSON payload that is sent to the step by Aiimi Insight Engine. We call this the ‘work item’. Essentially, the step manipulates this structure and returns it.

```
# this is the function that will get called
def example():   
    return jsonify(do_example(request.get_json()))
```

This is the actual function that does the work. We print out the ‘work item’, call an example library function to get some text, and then append that to the text content of the work item.

```
# this is the function that will get called
def do_example(work):  
    print("BEFORE:")
    print(work)
    print()

    # add your code here to manipulate the EnrichmentWorkItem structure
    logging.info("Generating example for: %s", work['File']['Name'])
    work['File']['TextContent'] += ' - ' + example_lib_function(example_config["text"])
    print("AFTER:")
    print(work)
    return work
```

We include a main in the Python code so we can call the step directly from the command line. This makes development easy. You need to create a work item structure (there is a simple one here). You can print out what Aiimi Insight Engine sends you to and then code up something from this. For this type of testing you only need to include the fields that you are using an not the whole work item.

```
if __name__ == "__main__":
    text_content = "This is some test text"
    work = {}
    work["File"] = {}
    work["File"]["Name"] = "Test Document.txt"
    work["File"]["Extension"] = "txt"
    work["File"]["TextContent"] = text_content
    do_example(work)
```
