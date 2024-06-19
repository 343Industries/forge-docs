---
title: Halo 3 Misc Console Commands #Required; page title is displayed in search results. Include the brand.
description: Misc Console Commands for Halo 3 Modding Documentation. #Required; article description that is displayed in search results. 
author: mjordan343 #Required; your GitHub user alias, with correct capitalization.
ms.author: mjordan #Required; microsoft alias of author; optional team alias.
ms.service: halo-mcc #Required; service per approved list. slug assigned by ACOM.
ms.topic: quickstart #Required; leave this attribute/value as-is.
ms.date: 03/17/2022 #Required; mm/dd/yyyy format.
ms.custom: template-quickstart #Required; leave this attribute/value as-is.
---

# Console Commands

Console commands allow you to access the game via a command prompt, allowing you to view and set scripts and functions.

There are four types of console commands:

- **hs_function** — defines behavior, such as object_set_permutation

- **hs_global** — defines data, such as debug_objects

- **scripts** < from .hsc file

- **globals** < from .hsc file

## **Entering Console Commands**

### ** Access the Console**

Press tilde (~) key to access the in-game command prompt. Use \~ for Sapien. This will allow you to type in console commands.

### **Autocomplete Commands**

You can autocomplete any string you type in by just hitting the tab key. This will list all of the commands that start with the given string.

For example, if you type sa and press tab, you will see Figure 1.

![View of the console commands with autocompleted suggestions.](./media/H3_Misc_AutoComplete.png)

Figure 1 - Autocompleted Command.

### **Find**

Type find and any string will list all of the commands that include the given string.

For example, if you type find physic, you will see Figure 2.

![View of the console commands with the Find output after typing find physic.](./media/H3_Misc_FindCommand.png)

Figure 2 - Find Command Output.

### **Help**

Type in help and a console command will list the command and the required parameters plus a description of the console command. Find is available for hs_functions only— other command types are not supported.

For example, if you type help object_set_permutation, you will see Figure 3:

![View of the console commands telling you the required parameters after typing help object underscore set underscore permutation.](./media/H3_Misc_HelpCommand.png)

Figure 3 - Help Command Output.

### **Debug Menu**

The most common console commands have been wrapped in a GUI known as the Debug Menu. Press the back and start keys simultaneously to bring up the debug menu.

> [!NOTE]
> Press the back key first then hold it then press the start key to avoid bringing up the game ui.

![View of the debyug menu G U I in game.](./media/H3_Misc_DebugMenu.png)

Figure 4 - The Debug Menu.

Creating Text List of All Halo Script Commands (script_doc)

You can export a list of the current hs_functions by typing in script_doc on the PC console (inside Sapien). This will create \halo3\main\hs_doc.txt.

Example:

```
(object_set_permutation \<object> \<string_id> \<string_id>)
```
