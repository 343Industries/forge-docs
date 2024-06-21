---
title: Halo 2 Guides Set Instanced Geometry Pathfinding Policy #Required; page title is displayed in search results. Include the brand.
description: Set Instanced Geometry Pathfinding Policy for Halo 2 Guides in MCC Modding Documentation. #Required; article description that is displayed in search results. 
author: mjordan343 #Required; your GitHub user alias, with correct capitalization.
ms.author: mjordan #Required; microsoft alias of author; optional team alias.
ms.service: halo-mcc #Required; service per approved list. slug assigned by ACOM.
ms.topic: quickstart #Required; leave this attribute/value as-is.
ms.date: 11/09/2022 #Required; mm/dd/yyyy format.
ms.custom: template-quickstart #Required; leave this attribute/value as-is.
---

# How-To - Set Instanced Geometry Pathfinding Policy

Instanced geometry ("Poops") can have a pathfinding policy specified in their name by adding a special character just after the ‘**%**’.

```
%mylittlepoop01
```

Poops **without any special characters** default to pathfinding policy “**cut-out**”. This means that ai will pathfind around them but will not be able to walk on them. This is good for things like columns which are z-buffered into the floor. Of the three poop pathfinding policies, this is in the middle in terms of memory usage.

```
%-mylittlepoop02
```

Poops with a **minus** just after the percent will use pathfinding policy “**none**”. This means that ai will pathfind as if the poop wasn’t there. This is good for things that aren’t near playable space like rafters on the ceiling. This uses the least amount of memory.

```
%+mylittlepoop03
```

Poops with a **plus** just after the percent will use pathfinding policy “**static**”. This means that ai will fully pathfind on them. This is good for things like catwalks, stairs, etc. It uses the most amount of memory.

These pathfinding policies are the same as the ones we can specify for scenery and machines, but they have one more called “dynamic”.

What about pathfinding policy “dynamic.” Since poops can’t move, they don’t need the dynamic pathfinding policy and it’s much more efficient to bake it into the pathfinding graph.
