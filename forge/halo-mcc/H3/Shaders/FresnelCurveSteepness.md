---
title: Halo 3 Shaders Fresnel Curve Steepness #Required; page title is displayed in search results. Include the brand.
description: Shaders Fresnel Curve Steepness for Halo 3 Modding Documentation. #Required; article description that is displayed in search results. 
author: mjordan343 #Required; your GitHub user alias, with correct capitalization.
ms.author: mjordan #Required; microsoft alias of author; optional team alias.
ms.service: halo-mcc #Required; service per approved list. slug assigned by ACOM.
ms.topic: quickstart #Required; leave this attribute/value as-is.
ms.date: 03/17/2022 #Required; mm/dd/yyyy format.
ms.custom: template-quickstart #Required; leave this attribute/value as-is.
---

# Fresnel Curve Steepness

Controls how far the environment map wraps around from the edges of the model. A value of zero gives you uniform reflection across the model, the same as a non-glass shader. Higher value cause less reflection on the front of the mesh and keep it limited to the sides of the mesh (faces with their normals at 90 degrees to the camera).

![An object with the fresnel curve steepness set to one.](./media/H3_Shaders_FresCurve1.png)

Figure 1 - fresnel_curve_steepness: 1.

![An object with the fresnel curve steepness set to two point five.](./media/H3_Shaders_FresCurve25.png)

Figure 2 - fresnel_curve_steepness: 2.5.

![An object with the fresnel curve steepness set to five.](./media/H3_Shaders_FresCurve5.png)

Figure 3 - fresnel_curve_steepness: 5 (default).

![An object with the fresnel curve steepness set to ten.](./media/H3_Shaders_FresCurve10.png)

Figure 4 - fresnel_curve_steepness: 10.
