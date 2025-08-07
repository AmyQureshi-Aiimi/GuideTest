# Reuters Connect

Connect Reuters News to Workplace AI to make the most of everythign available to you. Once you have selected a Source System type more detail will expand to customise this.

## Connection

1. Enter the Authentication Url for your Reuters connection.
2. Enter the Base API Url.
3. Select the credential to use from the Select Credential dropdown.
   * _For support setting up credentials use_ [_our guide on managing credentials._](../../../../security/credentials.md)
4. Enter a number in the Rate limiter calls.
   * This will be the number of API calls that can be made in the rate limiter period.
5. Enter a time period in the in Rate limiter period.
   * This is the time in seconds that the limiter is set to.
6. Enter a maximum date range, in seconds, for a single search in Search request window.
   * This will break searches into smaller windows of this length.
   * This helps prevent a request reaching the result count limit.
7. Select the Searches tab.

<figure><img src="../../../../../.gitbook/assets/image (738).png" alt="" width="563"><figcaption></figcaption></figure>

## Searches

You can add specific searches and queries for a Reuters connection. If you add a search this source will only include results from Reuters that match that search.

1. Select Add to add new search perimeters.
2. Add a Channel Alias to search a specific channel from Reuters.
3. Add a location to Geography if you are looking for information about a certain area or location.
4. Enter a Query string to search for specific information on Reuters.

You can add more searches by selecting Add or remove them by selecting Delete next to the search.

### Search Options

1. Check Include bulletins to include all Reuters bulletins as well.
2. Check Include sports sources to include all sports news from Reuters as well.
3. Enter a Number of days to load on first crawl.
   * This will crawl multiple days of data on your first crawl to give you a history of information.
   * This must be less than 30 days.
4. Select the Entity Mapping tab.

<figure><img src="../../../../../.gitbook/assets/image (739).png" alt="" width="563"><figcaption></figcaption></figure>

## Entity Mapping

1. Check Retrieve entities to retrieve the entities for each item.
   * This will double the number of API calls made.
2. Check Extract geo locations to add any locations identified to the items metadata.

### Entity Options

You can directly map the OpenCalais entities from Reuters to Workplace AIs entities. You can also map multiple OpenCalais entities to one Workplace AI entity.

1. Select Add new item to add an entity details.
2. Enter the OpenCalais name in the first (left) box.
   * The Uri prefix is not needed and must be removed.
   * Example - Person or Geo/County
3. Enter the Workplace AI entity name in the second (right) box.
   * This must be fully qualified.
   * Example - entities.ner.person

<figure><img src="../../../../../.gitbook/assets/image (740).png" alt="" width="563"><figcaption></figcaption></figure>
