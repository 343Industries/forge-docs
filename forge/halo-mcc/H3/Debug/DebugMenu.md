---
title: Halo 3 Debug Menu #Required; page title is displayed in search results. Include the brand.
description: Debug Menu for Halo 3 Modding Documentation. #Required; article description that is displayed in search results. 
author: mjordan343 #Required; your GitHub user alias, with correct capitalization.
ms.author: mjordan #Required; microsoft alias of author; optional team alias.
ms.service: halo-mcc #Required; service per approved list. slug assigned by ACOM.
ms.topic: quickstart #Required; leave this attribute/value as-is.
ms.date: 03/16/2022 #Required; mm/dd/yyyy format.
ms.custom: template-quickstart #Required; leave this attribute/value as-is.
---

# Debug Menu

## **The Basics**

- The debug_menu_init.txt file is located in your \main\bin directory.

- You can create a custom debug menu, called debug_menu_user_init.txt which will append to the default debug menu (but which will still allow you to get the latest versions of the default menu without erasing your custom items). See below for instructions.

## **Create a custom debug menu**

- If the standard debug menu doesn't suit your needs, you can create a custom debug menu just for yourself, but which will still allow you to get the latest versions of the default menu without erasing your custom items. The custom menu simply appends to the bottom of the default one.

Here's how to set it up:

1. Create a text file named **debug_menu_user_init.txt**.

2. Using the same format as that found in the debug_menu_init file, place the commands you want in your menu in the file you just created.

3. Save the file and copy it to the bin folder. Ex: H3EK\bin

4. If you're running the game when you copy the file over, you'll have to restart the game to see your changes to the menu. 
