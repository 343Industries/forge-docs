---
title: Halo 3 Instance Objects Pathfinding Policy #Required; page title is displayed in search results. Include the brand.
description: Instance Objects Pathfinding Policy for Halo 3 Modding Documentation. #Required; article description that is displayed in search results. 
author: mjordan343 #Required; your GitHub user alias, with correct capitalization.
ms.author: mjordan #Required; microsoft alias of author; optional team alias.
ms.service: halo-mcc #Required; service per approved list. slug assigned by ACOM.
ms.topic: quickstart #Required; leave this attribute/value as-is.
ms.date: 03/17/2022 #Required; mm/dd/yyyy format.
ms.custom: template-quickstart #Required; leave this attribute/value as-is.
---

# Pathfinding Policy

Poops can now have a pathfinding policy specified in their name by adding a special character just after the %.

```
%ex01
```

Poops without any special characters default to pathfinding policy cut-out as brother Damian calls it. This means that AI will pathfind around them but will not be able to walk on them. This is good for things like columns which are z-buffered into the floor. Of the three poop pathfinding policies, this is in the middle in terms of memory usage.

```
%-ex02
```

Poops with a minus just after the percent will use pathfinding policy none. This means that AI will pathfind as if the poop wasn't there. This is good for things that aren't near playable space like rafters on the ceiling. This uses the least amount of memory.

```
%+ex03
```

Poops with a plus just after the percent will use pathfinding policy static. This means that AI will fully pathfind on them. This is good for things like catwalks, stairs, etc. It uses the most amount of memory.

The astute amongst you might be wondering, "Those pathfinding policies are the same as the ones we can specify for scenery and machines, but they have one more called dynamic. What about pathfinding policy dynamic? The answer is that we could add it, but since poops can't move they don't need the dynamic pathfinding policy and it's much more efficient to bake it into the pathfinding graph.
