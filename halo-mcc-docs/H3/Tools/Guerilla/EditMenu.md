---
title: Halo 3 Guerilla Edit Menu #Required; page title is displayed in search results. Include the brand.
description: Guerilla Edit Menu for Halo 3 Modding Documentation. #Required; article description that is displayed in search results. 
author: mjordan343 #Required; your GitHub user alias, with correct capitalization.
ms.author: mjordan #Required; microsoft alias of author; optional team alias.
ms.service: halo-mcc #Required; service per approved list. slug assigned by ACOM.
ms.topic: quickstart #Required; leave this attribute/value as-is.
ms.date: 02/10/2022 #Required; mm/dd/yyyy format.
ms.custom: template-quickstart #Required; leave this attribute/value as-is.
---

# Edit Menu

The Edit menu is similar to the standard edit menu that appears in most windows programs. There are the common commands like undo, cut, copy, and paste— which all allow you to easily manipulate text strings— along with some other commands which are unique to Guerilla.

> [!NOTE]
> Some of the items on this menu only appear when a tag is opened for editing.

![View of the edit menu for the Guerilla tool](./media/H3_Guerrilla_EditMenu.png)

Figure 1 - Guerilla's Edit Menu

- **Undo**— Undoes the last change you made to a particular tag.
- **Cut**— When an item (block of text, image, etc) is selected, this functions deletes it from the tag and moves it to the Windows clipboard (for use in pasting elsewhere).
- **Copy**— When an item (block of text, image, etc) is selected, this function makes a copy of it and places the copy on the Windows clipboard (for use in pasting elsewhere).
- **Paste**— Pastes a previously copied/cut piece of data.
- **Clear**— Clears (deletes) the selected piece of data.
- **Hold**— Saves the current state of the open tag without permanently saving it. You can "hold" a tag, Xsync, and view your changes in the game engine without having to save the tag. Then, if you don't like the changes, you can select "Fetch" and restore the tag to its previous state.
- **Fetch**— Restores a tag with a "hold" on it to the state it was in when the hold was set.
- **Expert Mode**— Allows access to some sections of tags that are normally not editable. You should not be using this feature if you don't already know what it does!
- **Import Tag**— Uses tool command to import a tag into Guerilla.
- **Remote Command View**— Legacy option, no current functionality.
- **Show Block Sizes**— When this option is selected (checkmark appears next to it in the menu), the file size of all blocks in a tag appear next to the block titles.
