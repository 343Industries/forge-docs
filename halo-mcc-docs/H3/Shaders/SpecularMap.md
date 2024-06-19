---
title: Halo 3 Shaders Specular Map #Required; page title is displayed in search results. Include the brand.
description: Shaders Specular Map for Halo 3 Modding Documentation. #Required; article description that is displayed in search results. 
author: mjordan343 #Required; your GitHub user alias, with correct capitalization.
ms.author: mjordan #Required; microsoft alias of author; optional team alias.
ms.service: halo-mcc #Required; service per approved list. slug assigned by ACOM.
ms.topic: quickstart #Required; leave this attribute/value as-is.
ms.date: 03/17/2022 #Required; mm/dd/yyyy format.
ms.custom: template-quickstart #Required; leave this attribute/value as-is.
---

# Specular Map

Gives you per-pixel control over both specular strength and color. If the map is greyscale, it only affects strength, not color. Use and RGBA map to control color (and in this case, the alpha channel would control strength).

![An object that has a red and green specular map applied that includes an alpha mask.](./media/H3_Shaders_SpecMapWith.png)

Figure 1 - with specular_map

![A red and green noise texture used for the specular map.](./media/H3_Shaders_SpecMapMap.png)

Figure 2 - specular_map

![A black and white noise texture used for the alpha of the specular map.](./media/H3_Shaders_SpecMapAlpha.png)

Figure 3 - specular_map alpha

![An object with a specular map assigned.](./media/H3_Shaders_SpecMapWithout.png)

Figure 4 - without specular_map
