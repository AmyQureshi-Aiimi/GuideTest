# Classifications

Classifications are used to give data and documents more detail. The classification tool automatically groups and labels items. It classifies them based on set rules, statistical analysis or a blend of both.

* A well-organised repository can reduce the time you spend looking at the wrong thing.&#x20;
* Classify documents to help you stay compliant. For example, contracts can be classified to ensure they are handled correctly.&#x20;
* Classified documents can trigger actions or approvals. For example, invoices are sent straight to the finance team for processing.

## New Classification

1. Select New Classification
   * This will open the New Classification Configuration modal.
2. **Configuration ID:** Enter a unique ID for this classification.
3. **Configuration Name:** Enter a user friendly name for this classification.
4. **Description:** Enter more information about the classification.&#x20;
   * This could be information to help others understand why it's used.
5. **Classification Edit Access:** Add users or groups who can edit the classification applied to an item.
   * This will only allow them to edit items that fall into this classification.
6. **Classification Storage Entity:** Choose which entity this classification should be written to.
   * This allows users to filter results by the classifications.
7. Select Create.

<figure><img src="../../../.gitbook/assets/image (844).png" alt="" width="563"><figcaption></figcaption></figure>

#### Editing a classification

You can edit the details of a classification by selecting the relevant classification from the list then Edit. This will open up a modal containing the information you can change.

#### Deleting a Classification

You can delete a classification by selecting the relevant classification from the list then Delete. Deleting a classification will remove all associated Classes and Class rules.&#x20;

Any class from this list applied to an existing items will have the class removed immediately.&#x20;

## Displaying Classifications

The order of your classifications determines what class is shown on a result. If an item has multiple classes assigned, the class from the highest classification will be displayed.&#x20;

### Reordering Classifications

1. Drag and reorder the cards in your classification list to change the priority.

### Source specific priorities

If you want a source to prioritise showing classes from one classification you can set a priority in the source config. This setting takes priority over the order of the classifications.&#x20;

{% hint style="info" %}
Classifications must be configured before you can change this setting.&#x20;
{% endhint %}

1. Go to Configurations.
2. Find the Source you are looking for.
3. Select edit and go to the General tab.
4. Priority Classification Configuration: Choose a classification to show over any other from the dropdown.&#x20;
   * This ensures if an item in this source has a class from that classification it will be shown in the result.&#x20;
