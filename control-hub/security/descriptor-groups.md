# Descriptor Groups

Security descriptors can impact the permissions of your items. As files are crawled and added to Aiimi Insight Engine, so are their security descriptors.

These descriptors can control who has access to what items. You can create rules that mean a user's descriptors must match an item's to view it. These controls supersede all other permissions like read access and privileged access.

## New Descriptor Group

1. Select New Security Descriptor Group
   * This will open a New Security Descriptor Group modal
2. **Name -** Enter a name for the Security Group.
3. **Description-**  Enter a short description for this group.
   * This can help others understand what the group is used for.
4. **Match Mode -** From the dropdown choose how many descriptors a user must match to view an item.
   * **Single -** For an item with any number of descriptors, a user must match at least one to access it.
   * **All -** If an item has more than one descriptor, a user must match all of them to access it.&#x20;

<figure><img src="../../.gitbook/assets/image (130).png" alt="" width="563"><figcaption></figcaption></figure>

### Descriptor Mapping

Use the descriptor name and group name override to map item descriptors to users and groups with different names.&#x20;

1. **Descriptor Name -** Enter the descriptor from the item.
2. **Group Name Override -** Enter a User or Group you want to map the descriptor to if they are different.
   * You can only assign one user or group to a descriptor.
3. Select Add Descriptor
   * This will add the descriptor you just created to the group. It will also create another line so you can continue to add descriptor mappings.
4. Select Add once you are finished.

<figure><img src="../../.gitbook/assets/image (129).png" alt="" width="563"><figcaption></figcaption></figure>

***

## Managing Descriptor Groups

### Edit

1. Find the Security Descriptor Group you want to change. You can use the search box to find a descriptor group.
2. Select the edit button on the group you want to change.
   * This will open a Edit Security Descriptor Group modal.
3. You can then to amend every field and add or remove descriptor mappings.
4. Select Update to finalise your changes.

### Delete

1. Find the Security Descriptor Group you want to remove. You can use the search box to find a descriptor group.
2. Select the Delete button on the group you want to remove.
   * This will open a confirmation popup.
3. Confirm you are happy to remove the descriptor group.
