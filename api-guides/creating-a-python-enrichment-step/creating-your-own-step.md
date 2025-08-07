# Creating Your Own Step

It is simple to create your own step using the example as a base. Simply copy and rename the file and get to work.

Things to bear in mind and remember:

* Add your step to the endpoints.json file.
* Use a configuration file to store configuration, rather than maintaining variables in your code.
* You can load data from anywhere to support your enrichment step. For example, loading CSV data to map values into entities (see next section).
* Be aware of steps that take a long time to run. If you do have steps that take a long while to run then make sure the timeout in the timeout parameter (option on the REST step in Control Hub) is high enough.
* If your step takes a long time to run, and that is because it uses a large amount of CPU resources, then consider limiting the concurrency (option on the REST step in Control Hub). A high value for concurrency will simply cause lots of parallel steps to start, and increases the probability of timeouts.
