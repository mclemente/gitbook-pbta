# Making Changes to Existing Worlds

If you have to make changes to your system's sheet settings after you've already created actors and NPCs, you can return to the PbtA Sheet Configuration settings and make the changes that you need.

{% hint style="danger" %}
### Warning! Make a backup first!

Making changes to your sheet configuration after there are already actors and items using the configuration is inherently risky. Always make a backup of your world before changing the sheet configuration if you have existing actors and items.
{% endhint %}

Most changes should be safe to implement (such as adding new attributes or changing the label of existing attributes), but some changes are more severe and could cause partial data loss on  your actors. Whenever you click the **Save Configuration** button, you will be given a second prompt called **Confirm Changes** that will outline what changes are expected to occur and you'll have three options: Confirm, Confirm + Update, or Cancel.

Here's an example of what that looks like:

![](<.gitbook/assets/image (4).png>)

## Options to Confirm the Changes

There are three options when you've read through the changes and are ready to confirm them:

* **Confirm:** This will update your system's configuration, but it will not retroactively apply those changes to existing actors. However, in most cases you'll want to apply those updates to existing actors using the next option. This can be useful if you have a large number of actors, as it may be better to save the changes immediately and update the actors later with a macro (contactk me at `asacolips#1867` in Discord for assistance on that).
* **Confirm + Update:** This will update your system's configuration and apply those changes to existing actors and tokens. You'll usually want to take this route, but make sure to backup your world first.
* **Cancel:** This will exit the dialog without saving changes.

## Destructive Changes

The following changes will cause data loss for any attributes listed under them if you choose the Confirm + Update option:

* **Deletions:** Any attributes flagged for deletion will be deleted from actors.
* **Type changed** **(attribute will be reset):** Some type changes (such as changing from Text to Clock) will cause those attributes to be deleted and then recreated with empty data. However, if the "attribute will be reset" portion isn't present, those attributes will be fine due to the data being compatible (such as going from a Clock to a Resource).

## Safe Changes

Most other change types are safe to do. For example, adding new stats, attributes, or move types won't cause data loss since you're only updating actors to have new options. Similarly, changing the label or description on attributes will not cause data loss.

