---
title: Halo 2 Guides Teleporters in MP #Required; page title is displayed in search results. Include the brand.
description: Teleporters in MP for Halo 2 Guides in MCC Modding Documentation. #Required; article description that is displayed in search results. 
author: mjordan343 #Required; your GitHub user alias, with correct capitalization.
ms.author: mjordan #Required; microsoft alias of author; optional team alias.
ms.service: halo-mcc #Required; service per approved list. slug assigned by ACOM.
ms.topic: quickstart #Required; leave this attribute/value as-is.
ms.date: 11/09/2022 #Required; mm/dd/yyyy format.
ms.custom: template-quickstart #Required; leave this attribute/value as-is.
---

# How-To - Set Up Teleporters in MP

## Teleporters

Teleporter source and destination locations are indicated with teleporter netgame flags. These are placed in Sapien, in the "mission\game data\netgame flags" directory.

Each teleporter requires a separate pair of source (src) and destination (dest) flags. A pair is defined by a matching identifier number. The team designator is not used for netgame flags, and so should be set to "Neutral" to avoid confusion.

Direction on a teleporter is tricky business. The facing on the source netgame flag should match the predicted direction of entry, the facing on the exit flag should match the desired direction of facing on exit. Sometimes you have to tweak this to get it right.

A teleporter flag has no associated model, that has to be placed independently as scenery. Generic teleporter scenery exists in "tags\objects\multi". Teleporters can also be designed into the environment, like Derelict from Halo 1 or Relic from Halo 2.
