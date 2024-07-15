---
title: Halo 3 Lightmap Resolution for Instances #Required; page title is displayed in search results. Include the brand.
description: Lightmap Resolution for Instances for Halo 3 Modding Documentation. #Required; article description that is displayed in search results. 
author: mjordan343 #Required; your GitHub user alias, with correct capitalization.
ms.author: mjordan #Required; microsoft alias of author; optional team alias.
ms.service: halo-mcc #Required; service per approved list. slug assigned by ACOM.
ms.topic: quickstart #Required; leave this attribute/value as-is.
ms.date: 03/17/2022 #Required; mm/dd/yyyy format.
ms.custom: template-quickstart #Required; leave this attribute/value as-is.
---

# Lightmap Resolution for Instances

When instanced geometry (poops) are initially imported with a BSP, they are given a default lightmap bitmap resolution of 64×64 (the lowest lightmap resolution). We do this because all instances of a definition need to have the same UV coordinates. There are many situations, however, when you may want a piece of instanced geometry that has a lightmap resolution similar to the BSP geometry around it (especially with some larger instances). In those cases, you can set the lightmap resolution specifically for that piece of instanced geometry (and each instance can have a different lightmap resolution, if you want).

The lightmap resolution is set by specifying the multiplier you want to use in the Instance name in 3ds Max. Following the name of the instance, include a number in parentheses. See below for examples.

## **Lightmap Resolution Settings**

|**Sample Name of Instanced Geometry**|**Lightmap Bitmap Resolution**|
|----|----|
|%default_poop|64×64|
|%mediumres_poop(4)|256×256|
|%hires_poop(8)|512×512|
|%superres_poop(16)|1024×1024|

>[!NOTE]
> You do not have to set the lightmap resolution as a power of 2 (or as even numbers) as in the examples given here. You can use any number you need in order to make more precise adjustments.
