---
title: Halo 3 Lightmap Translucency #Required; page title is displayed in search results. Include the brand.
description: Lightmap Translucency for Halo 3 Modding Documentation. #Required; article description that is displayed in search results. 
author: mjordan343 #Required; your GitHub user alias, with correct capitalization.
ms.author: mjordan #Required; microsoft alias of author; optional team alias.
ms.service: halo-mcc #Required; service per approved list. slug assigned by ACOM.
ms.topic: quickstart #Required; leave this attribute/value as-is.
ms.date: 03/17/2022 #Required; mm/dd/yyyy format.
ms.custom: template-quickstart #Required; leave this attribute/value as-is.
---

# Lightmap Translucency

Below is a brief explanation of the way that transparency interacts with the lightmapper in the Halo 3 engine.

In order, from left to right (see Figure 1), direct lights were shined through the following materials:

- Shader with green 255 bitmap, two-sided, lightmap transparency color set to green 255
- Shader with green 255 bitmap, using alpha blended gradient
- Shader with green 255 bitmap, using alpha tested checker pattern
- Default shader using multiply blend mode
- Default shader using additive blend mode
- Default shader using double multiply blend mode

See figures two and three for other examples.

![Row of lights casting on different shaders to show how they are affected.](./media/H3_Lightmap_TestSet.png)

Figure 1 - The set of test shaders with direct lights on them.

![Row of shaders on a wall with a singular light to show the differences between them.](./media/H3_Lightmap_TestSetHigh.png)

Figure 2 - The original lightmaps run on high.

![Row of shaders on a wall with a singular light to show the differences between them after being re mapped.](./media/H3_Lightmap_TestSetRemap.png)

Figure 3 - A re-lightmapped version (on high) without changing settings.
