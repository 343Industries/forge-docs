---
title: Halo 3 Shaders Specular Mask #Required; page title is displayed in search results. Include the brand.
description: Shaders Specular Mask for Halo 3 Modding Documentation. #Required; article description that is displayed in search results. 
author: mjordan343 #Required; your GitHub user alias, with correct capitalization.
ms.author: mjordan #Required; microsoft alias of author; optional team alias.
ms.service: halo-mcc #Required; service per approved list. slug assigned by ACOM.
ms.topic: quickstart #Required; leave this attribute/value as-is.
ms.date: 03/17/2022 #Required; mm/dd/yyyy format.
ms.custom: template-quickstart #Required; leave this attribute/value as-is.
---

# Specular Mask

Specular Mask defines how specular properties are controlled on a per-pixel basis.

> [!NOTE]
> The specular properties (if any) are defined in the Material Model, this option simply defines where to find the mask. Regarding the grayscale values in the alpha channel (if used), white is maximum specularity as defined in the material_model properties, black is zero specularity.

There are three options for specular mask parameters:

## no_specular_mask

- **[no parameters]** — No per-pixel control of specular properties. This is the default setting. This will give you a constant specular highlight across the mesh, resulting in a very plastic look.

![An object that is note using a specular mask resulting in a general highlight across the mesh.](./media/H3_Shaders_SpecMaskNone.png)

Figure 1 - no_specular_mask

## specular_mask_from_diffuse

- **[no parameters]** — Uses the alpha channel of the base_map in the albedo properties for per-pixel control of specular properties.  This option (and the one below) let you break up the specular highlight for a more realistic look.

![An object that is using a specular mask based on the albedo of the texture.](./media/H3_Shaders_SpecMaskDiffuse.png)

Figure 2 - specular_mask_from_diffuse

## specular_mask_from_texture

- **specular_mask_texture** [bitmap] — Uses the red channel of the material_texture as defined in the cook_torrance material_model.
