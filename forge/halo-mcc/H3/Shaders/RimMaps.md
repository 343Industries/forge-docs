---
title: Halo 3 Shaders Rim Maps Transition Ratio #Required; page title is displayed in search results. Include the brand.
description: Shaders Rim Maps Transition Ratio for Halo 3 Modding Documentation. #Required; article description that is displayed in search results. 
author: mjordan343 #Required; your GitHub user alias, with correct capitalization.
ms.author: mjordan #Required; microsoft alias of author; optional team alias.
ms.service: halo-mcc #Required; service per approved list. slug assigned by ACOM.
ms.topic: quickstart #Required; leave this attribute/value as-is.
ms.date: 03/17/2022 #Required; mm/dd/yyyy format.
ms.custom: template-quickstart #Required; leave this attribute/value as-is.
---

# Rim Maps Transition Ratio

Controls how much the rim specular is affected by the specular or diffuse maps.

- 1.0 = rim color from specular map

- -1.0 = rim color from diffuse

- 0 = rim color from rim parameters only.

![An object with the rim maps transition ratio set to a value of one.](./media/H3_Shaders_RimMaps1.png)

Figure 1 - rim_maps_transition_ratio: 1

![An object with the rim maps transition ratio set to a value of zero.](./media/H3_Shaders_RimMaps0.png)

Figure 2 - rim_maps_transition_ratio: 0

![An object with the rim maps transition ratio set to a value of negative one.](./media/H3_Shaders_RimMapsNeg1.png)

Figure 3 - rim_maps_transition_ratio: -1

![A red and green noise map used for the specular texture in figures 1 through 3.](./media/H3_Shaders_RimMapsMap.png)

Figure 4 - Specular map used in figures 1 - 3
