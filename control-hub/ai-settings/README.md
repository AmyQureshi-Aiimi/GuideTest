# AI Settings

This section guides you through configuring how items in your system are classified.&#x20;

Within the Control Hub you can manage all the classifications used from one place. The classifications are used to identify, group and label items in your system.&#x20;

## Document Classification Journey

1. An item starts going through the rules of the first shema.
   * The item is compared to the rules for this schema in order.
2. If an item matches a defined rule it has the relevant classification assigned.
   * This item will not go through any more rules in the schema.
3. The item will then move on to the next schema in the list.
   * If an item does not match any rules in a schema it will also continue to the next schema.
4. And, the loop will continue until there are no classifications left.&#x20;

***

## Classification Configuration

There are a number of steps to go through in order to set up document classification.&#x20;

1. Create a schema.
2. Create classifications within this schema.
3. Assign Class Rules or AI classification to identify document classifications.
   * By default the enrichment will try to match a document to any class rules. If there are no matches and AI classification is enabled a document will then go through this.
4. Create an enrichment step to run the classification against your items.
   * For more information on creating this [see our guide on configuring enrichment steps](../agents/configurations/enrichment-configurations/creating-a-pipeline/).

### Key Terms

**Schema:** Schemas are groups of classifications.

**Classifications:** Classifications are added to an item to give users further information. They can be determined by Class Rules or AI Classification.

**Class Rules:** Class Rules determine what class an item will have applied. They use regular expressions to find information within an item.

**AI Classification:** This uses AI to determine what class an item will have applied. It uses AI and any prompts to identify an items classification.

#### Example

**Schema:** Risk Score

**Classifications:** No Risk, Low Risk, Medium Risk, High Risk

**Class Rules for High Risk:** The file name contains Confidential.

