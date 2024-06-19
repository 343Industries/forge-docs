---
title: Halo 3 Shaders Albedo Blend Properties #Required; page title is displayed in search results. Include the brand.
description: Shaders Albedo Blend Properties for Halo 3 Modding Documentation. #Required; article description that is displayed in search results. 
author: mjordan343 #Required; your GitHub user alias, with correct capitalization.
ms.author: mjordan #Required; microsoft alias of author; optional team alias.
ms.service: halo-mcc #Required; service per approved list. slug assigned by ACOM.
ms.topic: quickstart #Required; leave this attribute/value as-is.
ms.date: 03/17/2022 #Required; mm/dd/yyyy format.
ms.custom: template-quickstart #Required; leave this attribute/value as-is.
---

# Albedo Blend Properties

Blends between albedo base_map color and the specular tint and fresnel colors defined in the shader.

- 0 = more specular tint (see Figure1).

- 1 = more albedo/less specular tint (see Figure 2).

> [!NOTE]
> This can be used as a cheap alternative to a real specular mask.

![Object with albedo blend set to 0.](./media/H3_Shaders_Albedo0.png)

Figure 1 - Albedo 0.

![Object with albedo blend set to 1.](./media/H3_Shaders_Albedo1.png)

Figure 2 - Albedo 1.
