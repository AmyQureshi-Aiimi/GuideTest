# Data Views

The graph allows you to visualise the items Workplace AI has crawled, processed or enriched. You can choose to view your data in a way that works for you.

### **Graph Options**

<details>

<summary>Category</summary>

Choose how your data is grouped. Changing your category will adjust the graph to show the selected category.

* **Status** - Group items scanned or enriched by Workplace AI by their status.
* **Extension** - Group items scanned or enriched by Workplace AI by their file extensions.
* **Source** - Group items scanned or enriched by Workplace AI by their source system.

</details>

<details>

<summary>X-Axis (Interval)</summary>

Choose the timescale to compare your data. See how things have changed over time and see exactly when an issue started.

</details>

<details>

<summary>Y-Axis (Throughput)</summary>

Choose the value used to plot the data on your graph.

* **Number of Results** - The total count of all items in each category.
* **Size of Files** - The total size (MB) of all items in each category.

</details>

<figure><img src="../../../.gitbook/assets/image (751).png" alt=""><figcaption></figcaption></figure>

### **Filtering Your Graph**

Applying filters from the filters panel will impact the bar graph and breakdown table. For example If you select a source in the filters, the graph will adjust to show the data for that source only.

### Breakdown Table

The breakdown table has the headline stats broken down by source and sub source. You can see the discovered, enriched and failed files in more detail.

You can hide and show any sub source by expanding the parent source row.

### Examples:

1. Compare the size of files in a source over a number of months.
   * This could help identify sources that aren't used, use the most storage or may take the longest to crawl.\
     &#xNAN;_&#x43;ategory - Source_\
     _X-Axis (Interval) - Months_\
     _Y-Axis (Throughput) - Size of Files_
2. Compare the types of files that are being created over time.
   *   This could help identify software that is no longer needed, need updating, or are just the most popular.\
       &#xNAN;_&#x43;ategory - Extension_\
       _X-Axis (Interval) - Any time period you want to see_

       _Y-Axis (Throughput) - Number of Results_
3. See what exception statuses each source has to help identify sources that need investigating.
   1. _Filter - Select a source to investigate._\
      _Category - Status_\
      _X-Axis (Interval) - Any time period you want to see_\
      _Y-Axis (Throughput) - Number of Results_



