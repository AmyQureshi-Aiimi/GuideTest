# Config Management

## Finding a Configuration

You can see all of your configurations and their status on the main configurations page of Control Hub.&#x20;

### Group Agents By

You can change the layout of your configurations cards with the Group Agents By selector.

* Host - Choose between your hosts and see each type of configuration in an individual card.
* Type - Choose between your configuration type and see the configurations fr each host in an individual card.

<figure><img src="../../../.gitbook/assets/image (180).png" alt="" width="563"><figcaption></figcaption></figure>

### Searching

If a configuration card has more than 1 page you can use the search bar to find something.

1. Select Search for a configuration.
2. Start typing the name or description of your configuration.
   * This will filter your list in that card as you type.

***

## Edit a Configuration

Configurations can be edited individually. Once you find the config that needs changing:

1. Select the Options menu on the config.
2. Select Edit.
   * This will open a modal where the information can be changed.
3. Edit any of the information.
4. Select Save.

***

## Delete a Configuration

Configurations can be deleted individually. Once you find the config that needs changing:

1. Select the Options menu on the config.
2. Select Delete.
   * This will open a confirmation modal as a configuration cannot be recovered once deleted.

***

## Stop a Configuration

Stopping a configuration takes anything running and sets it to idle. Configurations can be stopped individually or you can stop everything within a configuration card.

### Config Type Card

1. Select Stop from the Configuration Type Card you want to set to Idle.
   * If idle you can select start to begin running the configuration again.&#x20;
   * This does not impact anything that was already idle.

### Individual Configuration

1. Find the configuration you want.
2. Select the Options menu of the config.
3. Select Stop.
   * Select Start from this menu to set an idle configuration to running

***

## Refreshing

### The Page

The configuration page has an automatic refresh so you can monitor the the status of your configs.&#x20;

* Select the Refresh Every dropdown and select a different option to change the default refresh rate.
  * This is set to 30 seconds by default.
* Manually refresh the page by selecting Refresh next to this dropdown.

<figure><img src="../../../.gitbook/assets/image (299).png" alt=""><figcaption></figcaption></figure>

### A Configuration Card

You can refresh a configuration card independently at any time.  This does not refresh any of the configuration it just updates the data shown.

* Select Refresh on the relevant card.

***

## Monitoring Stats

You can see statistics for each of the configuration type within it's card. These can help when debugging an issue or monitor performance and accuracy.

1. Select Stats on the configuration type card you want to investigate.
   * Source - See when a crawl happened, how long they took and the totals and errors that came with it.
   * Enrichment - See the number of items that have passed or failed enrichment.
   * Security - See when each sync happened, how long it took and the outcome.
