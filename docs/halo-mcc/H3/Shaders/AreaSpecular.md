---
title: Halo 3 Shaders Area Specular Contribution #Required; page title is displayed in search results. Include the brand.
description: Shaders Area Specular Contribution for Halo 3 Modding Documentation. #Required; article description that is displayed in search results. 
author: mjordan343 #Required; your GitHub user alias, with correct capitalization.
ms.author: mjordan #Required; microsoft alias of author; optional team alias.
ms.service: halo-mcc #Required; service per approved list. slug assigned by ACOM.
ms.topic: quickstart #Required; leave this attribute/value as-is.
ms.date: 03/17/2022 #Required; mm/dd/yyyy format.
ms.custom: template-quickstart #Required; leave this attribute/value as-is.
---

# Area Specular Contribution

Ambient lighting. Controls the amount of light cast onto the surface from all light sources in the area. Looks at all of the light probes in the area and calculates the amount and color of light that would be cast on the surface from each. Gives a very accurate representation of area lighting on the suface.

Defined by a value from 0-1, but higher numbers can be entered for special effects. A value of zero will result in no area specular at all. Low numbers work best.

![Object showing the Area Specular set to zero point one.](./media/H3_Shaders_AreaSpec01.png)

Figure 1 -  area_specular_contribution: 0.1.

![Object showing the Area Specular set to zero point five.](./media/H3_Shaders_AreaSpec05.png)

Figure 2 -  area_specular_contribution: 0.5.

![Object showing the Area Specular set to one .](./media/H3_Shaders_AreaSpec1.png)

Figure 3 -  area_specular_contribution: 1.

![Object showing the Area Specular set to two.](./media/H3_Shaders_AreaSpec2.png)

Figure 4 -  area_specular_contribution: 2.

![Object showing the Area Specular set to five.](./media/H3_Shaders_AreaSpec5.png)

Figure 5 -  area_specular_contribution: 5.
