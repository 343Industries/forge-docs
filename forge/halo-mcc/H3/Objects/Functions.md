---
title: Halo 3 Objects Functions #Required; page title is displayed in search results. Include the brand.
description: Objects Functions for Halo 3 Modding Documentation. #Required; article description that is displayed in search results. 
author: mjordan343 #Required; your GitHub user alias, with correct capitalization.
ms.author: mjordan #Required; microsoft alias of author; optional team alias.
ms.service: halo-mcc #Required; service per approved list. slug assigned by ACOM.
ms.topic: quickstart #Required; leave this attribute/value as-is.
ms.date: 03/17/2022 #Required; mm/dd/yyyy format.
ms.custom: template-quickstart #Required; leave this attribute/value as-is.
---

# Object Functions

There is only one object function that can be read by poops: unique_id, used so that each instance object will have a slightly different value.

Example: You could set a tint range in a poop .shader and then use unique_id to pick a value from that range (see Figure 1 for an example).

![Tint range for the albedo color showing a gradient between defined colors.](./media/H3_Objects_TintRange.png)

Figure 1 - Albedo Color.
