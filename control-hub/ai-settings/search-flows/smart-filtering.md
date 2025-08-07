# Smart Filtering

Search Flows can be configured to auto-select one or more source. If this is used the sources filter will be hidden from the filter panel in the main application.

## Static Term Matches

These allow you to ally static term matches to search steps. For example, classification = 'invoice'.

## Smart Term Matches

These are similar to static term matches, but will only be applied if the users query results in results that match the terms uses. This avoids returning no results if a term does not match. It is more forgiving that static term matches.&#x20;

## Smart Query String Term Matches

These allow you to analyse the query string and extract and select matching filters.

For example, you can map stw-brighton to a site code filter, and is this term appears in the query string it will be automatically selected.
