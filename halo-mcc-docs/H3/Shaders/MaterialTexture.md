---
title: Halo 3 Shaders Material Texture Properties #Required; page title is displayed in search results. Include the brand.
description: Shaders Material Texture Properties for Halo 3 Modding Documentation. #Required; article description that is displayed in search results. 
author: mjordan343 #Required; your GitHub user alias, with correct capitalization.
ms.author: mjordan #Required; microsoft alias of author; optional team alias.
ms.service: halo-mcc #Required; service per approved list. slug assigned by ACOM.
ms.topic: quickstart #Required; leave this attribute/value as-is.
ms.date: 03/17/2022 #Required; mm/dd/yyyy format.
ms.custom: template-quickstart #Required; leave this attribute/value as-is.
---

# Material Texture Properties

Available only in the cook_torrance material_model. Allows you to control specular coefficient, albedo blend, environment specular contribution and roughness on a per-pixel basis using the RGB and Alpha channels of the material texture bitmap.

You must check the use_material_texture box to activate the use of the material_texture bitmap. Checking this box disables some of the numeric value inputs.

> [!TIP]
> If you decide to use a material texture, you should remove the old specular alpha mask from your diffuse map— this will save you some texture memory.

## Red

Specular Coefficient (does not override the number value input).

You can think of this as the same thing as a specular mask, which is why you should remove it from the diffuse map.

![An object with the specular map using the diffuse map.](./media/H3_Shaders_MatTextureRed.png)

Figure 1 - Diffuse map copied into the red channel.

- Black = no specular

- White = max specular as defined by the specular_coefficient and related parameters (area and analytical, but not environment_map, contributions).

## Green

Albedo Blend (overrides the number value input).

![An object with the specular map using a half black and half white map to show how the tint color impacts the specular.](./media/H3_Shaders_MatTextureGreen.png)

Figure 2 - Half black and half white.

- Black = specular uses tint color

- White = specular uses albedo color (tinted by the tint color)  

## Blue

Environment Specular Contribution (overrides the number value input).

![An object with the specular map using a half black and half white map to show how the environment impacts the specular.](./media/H3_Shaders_MatTextureBlue.png)

Figure 3 - Half black and half white.

- Black = no environment.

- White = max environment.

## Alpha

Roughness (overrides the number value input).

- Black = sharp.

- White = wide.

![An object with the specular map using a uniform flat grey map.](./media/H3_Shaders_MatTextureAlphaGrey.png)

Figure 4 - Uniform flat grey (medium roughness).

![An object with the specular map using a checkerboard map.](./media/H3_Shaders_MatTextureAlphaChecker.png)

Figure 5 - Checker Map.

![An Alpha Map consisting of a black and white checker board pattern with a 50 percent grey square in the center.](./media/H3_Shaders_MatTextureAlphaMap.png)

Figure 6 - Alpha Map used in figure 5.

> [!TIP]
> A good place to start is to copy and invert the specular (red) channel. This gives you tight highlights in the areas with the strongest spec values, which is how spec usually works.

![An object with the specular map using an inverted roughness map.](./media/H3_Shaders_MatTextureRoughness.png)

Figure 7 - Spec map with inverted roughness map.
