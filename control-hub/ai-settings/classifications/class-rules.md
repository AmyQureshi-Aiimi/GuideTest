# Class Rules

An item will go through a list of class rules to determine if it should have a class applied. An item will go through the class rules to decide what classes should be applied. An item could have any number of classes applied and some will have no classes.

Class rules can be created for a number of variables using a RegEx query.&#x20;

## Enabling Class Rules

Items cannot be classified using class rules unless they are enabled. You can create and manage class rules while this is disabled.&#x20;

1. Use the Enable/Disable Class Rules toggle to turn these on or off.&#x20;

## New Class Rules

You can create rules based on a number of variables including the name, file extension and field values.

1. Within the relevant Classification then select the Class Rules tab.
2. Select Add Class Rule.
3. **Applied Class:** Select the class this rule will apply to from the dropdown list.
   * If you can't find the class you want, check you have the correct classification selected and the class exists in the classes tab.

### **Rules**

There is no limit to the number of rules you can create. You could have a single rule in one variable, multiple rules for one variable or multiple rules across multiple variables. All of the rules applied to a class must be met for an item to have that class applied.&#x20;

#### **File Name Regex Rules**

This checks if an items name matches the regex rules.&#x20;

1. Select New Rule.
2. Enter a RegEx to check the file name against.

#### **File Location Regex Rules**

This checks if an items location matches the regex rules.&#x20;

1. Select New Rule.
2. Enter a RegEx to check the file location against.

#### **Existing Field Rules**

This checks if a selected fields exist and are not null in an item.&#x20;

1. Select New Rule.
2. Select the field that should be present and not null in the file.&#x20;

#### **Field Value Rules**

This checks if a field exists and if the value in that field matches a value.

1. Select New Rule.
2. **Field #:** Select the field you want to check from the dropdown list.
3. **Field # Value:** Enter the value this field should match for this class.

#### **File Extension Rules**

This checks if the file extension matches the regex rule.&#x20;

1. Select New Rule.
2. Extension: Enter a file extension for items that should have for this class applied.
   * This can only be one extension.

<figure><img src="../../../.gitbook/assets/image (846).png" alt="" width="563"><figcaption></figcaption></figure>

## Rule Order

It's important to check the order of your rules. The order of your rules determines the order they are run.&#x20;

An item may pass the rules of multiple classes in one classification. But, once an item has a class assigned the remaining rules in that classification are skipped. The item will then move onto the next classification and it's rules.&#x20;

### Reordering Classifications

1. Drag and reorder the cards in your Class Rules list to change the priority.
