---
title: Halo 3 HowTos Build Cache Files Names #Required; page title is displayed in search results. Include the brand.
description: HowTos Build Cache Files for Halo 3 Modding Documentation. #Required; article description that is displayed in search results. 
author: mjordan343 #Required; your GitHub user alias, with correct capitalization.
ms.author: mjordan #Required; microsoft alias of author; optional team alias.
ms.service: halo-mcc #Required; service per approved list. slug assigned by ACOM.
ms.topic: quickstart #Required; leave this attribute/value as-is.
ms.date: 02/16/2022 #Required; mm/dd/yyyy format.
ms.custom: template-quickstart #Required; leave this attribute/value as-is.
---

# Build Cache Files

To build cache files, do the following:

1. Open up a command window and navigate to the root folder of the branch you're working in inside the depot (\halox\main, for example).

1. Type Tool **build-cache-file path_to_your_map** (levels\multi\zanzibar\zanzibar, for example). This builds a .map (cache) file and places it in a folder in your root branch directory called Maps (\halox\main\maps in most cases).

If you would like to sync the cache files to your Xbox as you build them, you can use the **build-cache-file-sync** command (the only difference is that it syncs the files to a tags build on your xbox after building them).
