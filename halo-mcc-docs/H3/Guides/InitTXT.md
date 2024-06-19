---
title: Halo 3 HowTos Setup Init.txt #Required; page title is displayed in search results. Include the brand.
description: HowTos Setup Init.txt for Halo 3 Modding Documentation. #Required; article description that is displayed in search results. 
author: mjordan343 #Required; your GitHub user alias, with correct capitalization.
ms.author: mjordan #Required; microsoft alias of author; optional team alias.
ms.service: halo-mcc #Required; service per approved list. slug assigned by ACOM.
ms.topic: quickstart #Required; leave this attribute/value as-is.
ms.date: 02/16/2022 #Required; mm/dd/yyyy format.
ms.custom: template-quickstart #Required; leave this attribute/value as-is.
---

# Setup Init.txt

The init.txt file contains console commands or other important information that you want to get read whenever Halo is launched. The file itself resides in the root folder of your Halo build on your Xbox and, if you have a tags build, in your \halox\main folder (where it gets synced from whenever you Xsync).

## Setup

1. Open Notepad.
1. Fill up the text file with useful or necessary console commands (see below for some examples).
1. From the File Menu, select Save As.
1. In the Save dialog, navigate to \halox\main (or the root folder of Halo if you have your Source Depot client mapped differently).
1. Name the file init.txt and click Save.
1. Use Tool to Xsync, the init.txt file will automatically be copied to your Xbox.  

> [!Note]
> If you aren't using a tags build, you can manually copy your init.txt file to the root folder of your Halo 3 build

## Useful Commands

You can place any console command inside the init.txt file and it will be set on launch of the game. If you want to place comments in the init.txt file, use a **; semi-colon** character.

Here are some example commands you might find useful:

- map_nato_map\— Instantly launches into the map specified without making you navigate through the UI
- error_geometry_hidme \path_e_all— Hides all of the error geometry text and numbers for increased performance and easier viewing. 
