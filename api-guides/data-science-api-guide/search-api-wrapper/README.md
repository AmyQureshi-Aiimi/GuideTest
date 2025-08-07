# Search API Wrapper

The Aiimi Insight Engine Search API wrapper is the best way to test Aiimi Insight Engine. It provides the same results in python as you would see in the UI.&#x20;

With the Search API wrapper, python developers can manage collections, perform searches, download files and use search flows.&#x20;

### Example Usage

<pre class="language-python" data-overflow="wrap" data-line-numbers><code class="lang-python">from aiimi_insight_engine.api.search_api import SearchAPI 
 
# Search API is a wrapper for AIE functionality available through the web browser 
# In python, we use it for either managing collections, or impersonating users 
# When SearchAPI is instantiated, the user will be prompted to authenticate in the command line 
# N.B. Most customer installs with have CSRF enabled, set the CSRF flag as appropriate. 
search = SearchAPI("localhost", verify=False, https=True, csrf=False) 

# For SAML Authenticated systems, use the saml Flag. This will open a browser window for the user to log in and 
# it requires the optional requirement libraries selenium and webdriver-manager to be installed 
# search = SearchAPI("https://aie.aiimi.com/api/", saml=True) 
 
# If wanted, privileged access mode can be activated 
# search.enable_privileged_access() 

# Collection types 
# With the search API we can view all available collection types 
collection_types = search.get_collection_types() 
for collection_type in collection_types: 
    print(collection_type.id(), collection_type.name()) 

# We can also create new collections 
# Collection type is optional, and we default to general-collection 
new_collection = search.new_collection("Demo Collection", collection_type=collection_types[0]) 

<strong># We can add documents to this new collection: e.g. 
</strong># new_collection.add_document("miro_aiimi", "uXjVMPgNn4c=") 

# We can also add permissions to a collection 
new_collection.add_permissions("read", "reader") 
new_collection.add_permissions("write", "writer") 
new_collection.add_permissions("delete", "deleter") 
print(new_collection.permissions()) 

<strong># To view all documents in a collection we can access files 
</strong>print(new_collection.files()) 

# If files are added to a collection a different way, we can update the collection from AIE 
new_collection.update() 

# We can view all available collections 
for collection in search.search_collections(): 
    print(collection.name()) 

# We can view collections associated with particular users 
# By default this pulls our-self 
user = search.get_user() 
print("username: " + user.username()) 
for collection in user.collections(): 
    print(collection.name()) 

# And delete collections as required 
new_collection.delete() 

# And of course, the search api can be used to.... search! 
search_results = search.search("Hello World") 
# (Optionally, datasets, search_flow_id, page_size and access_level can all be specified) 

# Search results use the same data sample object as the DS API, allowing results to be accessed as a pandas data frame
print(search_results.df) 
</code></pre>
