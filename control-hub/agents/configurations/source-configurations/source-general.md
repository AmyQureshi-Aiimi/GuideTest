# Source - General

## Name and Description

1. **Config ID:** Enter a unique ID for your source configuration.&#x20;
   * This must be lowercase.
2. **Configuration Description:** Enter a friendly display name for the source crawl.&#x20;
   * This will be shown on your Configurations dashboard.
3. **Display Group:** Enter a user friendly source name If you want users to see a different name.
   * Multiple sources with the same Display Group will be grouped together in the filters.

<figure><img src="../../../../.gitbook/assets/Screenshot 2023-02-15 at 10.50.55.png" alt="" width="563"><figcaption></figcaption></figure>

***

## Visibility

4. **Visibility:** Check the applications and lenses that can access this source.
   1. All visible sources are available within the SAR application.
5. **Mapped Data Models:** Select the data models to map to this source from the dropdown.
   * If a model is not targeted it will increase the Elastic memory usage.
   * This is not needed if you are creating a SharePoint Crawl.
6. **Mapped Vectors:** Select the vectors able to use this source from the dropdown.
7. **Source Boost:** Choose the level of boost a search result from this source gets from the dropdown.
   * The higher the boost the higher in a result list items from this source will appear.
8. **Enable Search Suggestions:** Check this to allow items from this source to be included in search suggestions.&#x20;

<figure><img src="../../../../.gitbook/assets/Screenshot 2023-02-15 at 10.51.35.png" alt="" width="563"><figcaption></figcaption></figure>

***

## Multilingual search set up

Users can perform multilingual searches within Aiimi Insight Engine. The text analyser will parse the content of that source using the rules for each language.

1. **Text Analyzer (Language):** Choose the language of the source from the dropdown.&#x20;
   * This does not translate the search or results but will allow native language to be used for the source.
   * The systems default language will be used if nothing is selected.

{% hint style="danger" %}
If the text analyzer is changed after a source is created, it will need to be reindexed.&#x20;
{% endhint %}

<figure><img src="../../../../.gitbook/assets/image (347).png" alt="" width="563"><figcaption></figcaption></figure>
