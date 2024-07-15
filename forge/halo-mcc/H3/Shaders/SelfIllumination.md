---
title: Halo 3 Shaders Self Illumination Properties #Required; page title is displayed in search results. Include the brand.
description: Shaders Self Illumination Properties for Halo 3 Modding Documentation. #Required; article description that is displayed in search results. 
author: mjordan343 #Required; your GitHub user alias, with correct capitalization.
ms.author: mjordan #Required; microsoft alias of author; optional team alias.
ms.service: halo-mcc #Required; service per approved list. slug assigned by ACOM.
ms.topic: quickstart #Required; leave this attribute/value as-is.
ms.date: 03/17/2022 #Required; mm/dd/yyyy format.
ms.custom: template-quickstart #Required; leave this attribute/value as-is.
---

# Self-Illumination Properties

Self-Illumination defines which pixels override object lighting.

There are six properties:

- off
- simple
- 3_channel_self_illum
- plasma
- from_diffuse
- illum_detail

## off

- **[no parameters]**— No self-illumination. This is the default setting.

## simple

- **self_illum_map** [bitmap] — Alpha channel of the selected bitmap controls which pixels are self-illuminated. The higher the color value in the alpha channel (of the self_illum_map), the more object lighting is overridden (255 = 100%, 0 = 0%).

- **self_illum_color** [color value] — Multiplied with the RGB channels of the self_illum_map to determine the color of light the object illuminates itself with.

- **self_illum_intensity** [numerical value] — the intensity of the light the object illuminates itself with. 

## 3_channel_self_illum

- **sel_illum_map** [bitmap]— Alpha channel of the selected bitmap controls which pixels are self-illuminated. RGB channels of the selected bitmap are used to modulate between channels A, B, and C. The higher the color value in the alpha channel of the self_illum_map, the more object lighting is overridden (255 = 100%, 0 = 0%).

- **channel_a** [color] — The color of self-illuminated pixels from the Red channel of the self_illum_map.

- **channel_a_alpha** [value] — Governs the intensity of the self-illuminated pixels in the Red channel of the self_illum_map.

- **channel_b** [color] — The color of self-illuminated pixels from the Green channel of the self_illum_map.

- **channel_b_alpha** [value] — Governs the intensity of the self-illuminated pixels in the Green channel of the self_illum_map.

- **channel_c** [color] — The color of self-illuminated pixels from the Blue channel of the self_illum_map.

- **channel_c_alpha** [value] — Governs the intensity of the self-illuminated pixels in the Blue channel of the self_illum_map.

- **self_illum_intensity** [numerical value]— The intensity of the light the object illuminates itself with.

## plasma

Plasma shaders take two bitmaps (noise maps) and compare them. Where values are the same (or close) between the two bitmaps, self-illumination is increased. Where values are different between the two bitmaps, self-illumination is decreased. For each area of similarity, three lines are created: sharp, medium, and wide— based on how similar the values are.

> [!NOTE]
> Only the values placed in the Red channel of the bitmaps (noise_maps) are used for comparison.

- **noise_map_a** [bitmap]— Pixels which are of similar value to those of noise_map_b will be self-illuminated.

- **noise_map_b** [bitmap]— Pixels which are of similar value to those of noise_map_a will be self-illuminated.

- **color_medium** [color]— The color of the medium sized line. Color_medium is a blend between the sharp and wide lines.

- **color_medium_alpha** [value]— Governs the intensity of the self-illumination for the medium sized line.

- **color_wide** [color]— The color of the wide line. Used where the difference in value between the pixels in the noise maps is greatest.

- **color_wide_alpha** [value]— Governs the intensity of the self-illumination for the wide (or large) line.

- **color_sharp** [color]— The color of the sharp line. Drawn where the difference in pixel value between the noise maps is the smallest.

- **color_sharp_alpha** [value]— Governs the intensity of the self-illumination for the sharp (or small) line.

- **self_illum_intensity** [numerical value]— The overall intensity of the light the object illuminates itself with.

- **alpha_mask_map** [bitmap]— Uses the alpha channel of the specified bitmap for per-pixel control of the plasma illumination. 255 (white) does nothing, any value less than 255 will decrease the plasma illumination.

- **thinness_medium** [value] — Governs the thinness of the color_medium area. A higher number will cause the color_medium line/area to become smaller (thinner). A low number will spread out the color_medium area of the shader.

- **thinness_wide** [value] — Governs the thinness of the color_wide area. A higher number will cause the color_wide line/area to become smaller (thinner). A low number will spread out the color_wide area of the shader.

- **thinness_sharp** [value] — Governs the thinness of the color_sharp area. A higher number will cause the color_sharp line/area to become smaller (thinner). A low number will spread out the color_sharp area of the shader.

## from_diffuse

Self-illumination of pixels is governed by the values of the RGB channels of the base_map from the albedo properties of the shader. 0 = no self-illumination. 255 = full self-illumination. 

- **self_illum_color** [color]— The color of self-illuminated pixels.

- **self_illum_intensity** [numerical value]— The intensity of the light the object illuminates itself with.

## illum_detail

- **self_illum_map** [bitmap]— The alpha channel of the selected bitmap is multiplied with the alpha channel of the self_illum_detail_map to control which pixels are self-illuminated. The higher the color value of each pixel in the alpha channel (of the self_illum_map), the more object lighting is overridden (255 = 100%, 0 = 0%).

- **self_illum_detail_map** [bitmap]— The RGB channel of the selected bitmap is double-multiplied with the self_illum_intensity setting. 50% gray does nothing, darker than 50% gray decreases the intensity. The alpha channel of the self_illum_detail_map is multiplied with the alpha channel of the the self_illum_map to control which pixels are self-illuminated.

- **self_illum_color** [color]— Multiplied with the RGB channels of the self_illum_map to determine the color of the light the object illuminates itself with.

- **self_illum_intensity** [value]— The intensity of the light the object illuminates itself with.
