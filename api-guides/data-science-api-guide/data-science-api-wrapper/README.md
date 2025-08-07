# Data Science API Wrapper

The data science API wrapper is designed to be used by data scientists when developing scripts which utilise Aiimi Insight Engine data. It is authenticated via API key (as defined in Control Hub) and was the original use case for the python library.&#x20;

{% hint style="info" %}
The DS API may be retired in a future Aiimi Insight Engine release, we recommend using the Search API wrapper as an alternative if possible.
{% endhint %}

### Example

<pre class="language-python" data-overflow="wrap" data-line-numbers><code class="lang-python"># First import the Insight Engine API 
from aiimi_insight_engine.api import AiimiInsightEngine 

<strong># Initialise an API instance, as a minimum you must provide the host server, or it will assume localhost 
</strong><strong>
</strong># The code tries to avoid requiring key or username entry here, but it is possible. 
# By default Aiimi Insight Engine looks for the key in "ds.key", you can also provide a path to a .key file anywhere on your machine, 
# or simply provide the key string - this is using the 'key' parameter. 
# Aiimi Insight Engine will use your local domain username, so rarely will you need to specify this, the only real case will be if you 
# are using a service account or similar. This would be using the 'username' parameter. 
<strong>aie = AiimiInsightEngine(host="aiimi-az-el05.aiimi.shared") 
</strong>
print("") 
 
# First get an idea of what datasets are available 
datasets = aie.datasets() 
print("Datasets:") 
for dataset in datasets: 
    print("{} : {}".format(dataset.description(), len(dataset))) 
print("") 

# Let's choose the first one to play with 
play_dataset = datasets[0] 

# Now lets get some statistics for this dataset so we can understand it better 
stats = aie.stats(datasets = play_dataset) 
# stats can be parsed as a DataFrame for ease of exploration 
stats_df = stats.to_data_frame() 
print(stats_df) 
print("") 

# Lets clean up our list by striping out any features which appear on less than half of our document set 
stats_df = stats_df[stats_df["percentage"] >= 0.5] 
print("Cleaned:") 
print(stats_df) 
print("") 

# Now let's do a search for these features on AiimiInsightEngine 
results = aie.search("*", dataset = play_dataset, fields = stats_df.index, size = 50) 
# Results is a DataSample object, which as a DataFrame as a property, we can print that 
print(results.df) 

# N.B. "*" was used as the search query to return all. You may also enter full lucene syntax here, a Elasticsearch 
# query DSL dictionary or use one of the helper objects from aiimi_insight_engine.api.query_builders (such as ExistsQuery, 
# RegexQuery, RangeQuery and many more). 
# The logical operators, &#x26;, | and ~ may be applied to query helper objects to build more complex expressions.
</code></pre>
