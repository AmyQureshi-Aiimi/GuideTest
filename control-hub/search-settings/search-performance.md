---
description: Control Hub > Global Settings > Search Performance
---

# Search Performance

## Accurate Totals For Pagination

Show users an accurate total number of results for their searches.

{% hint style="info" %}
For very large systems or systems near resource capacity we recommend disabling accurate totals for pagination.
{% endhint %}

<figure><img src="../../.gitbook/assets/image (588).png" alt=""><figcaption></figcaption></figure>

***

## Facets

When enabled, if a user unselects a source from their filters the number of matches in that source will not be requested or shown.

{% hint style="info" %}
This improves the performance of searches on large indexes that are used less frequently.
{% endhint %}

1. Check "Only fetch counts in facets for selected sources" to enable this.
2. Check Preload Advanced Search filter counts to have the filter counts preload. **This can be resource intensive.**&#x20;
   * If not checked, the advanced filter counts update when a user selects advanced search.

<figure><img src="../../.gitbook/assets/image (372).png" alt="" width="375"><figcaption></figcaption></figure>

***

## Lazy Loading Results

Configure how many and when results will load, you can also choose when to prompt users to changed their search or filters instead.

1. **Results per page load:** Enter how many results will load at the beginning and each time a user scrolls.
2. **Maximum lazy load pages:** Enter the maximum number of times new results will load automatically as a use scrolls.&#x20;
   * A button to load more results will appear after this point so users can continue to explore if they need to.
3. **Page loads before help prompt:** Enter the maximum number of times new results load before the help prompt appears.&#x20;

<figure><img src="../../.gitbook/assets/image (784).png" alt="" width="563"><figcaption><p>Lazy loading prompt on how to change or improve a search.</p></figcaption></figure>

***

## Group Emails

1. Check this to Group Emails from a conversation together in a thread.
   * Enabling this will impact your search performance. We recommend this is disabled when not needed.

<figure><img src="../../.gitbook/assets/image (97).png" alt="" width="375"><figcaption></figcaption></figure>

