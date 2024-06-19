---
title: Halo 2 Guides Effective Bitmaps #Required; page title is displayed in search results. Include the brand.
description: Effective Bitmaps for Halo 2 Guides in MCC Modding Documentation. #Required; article description that is displayed in search results. 
author: mjordan343 #Required; your GitHub user alias, with correct capitalization.
ms.author: mjordan #Required; microsoft alias of author; optional team alias.
ms.service: halo-mcc #Required; service per approved list. slug assigned by ACOM.
ms.topic: quickstart #Required; leave this attribute/value as-is.
ms.date: 11/09/2022 #Required; mm/dd/yyyy format.
ms.custom: template-quickstart #Required; leave this attribute/value as-is.
---

# How-To - Create Effective Bitmaps

Everyone understands that compression affects the quality of bitmaps but it’s important to also understand that there are ways to make the most of the bits we have.

## Bitmap Values

The most important thing is to use the full value range whenever possible. There is a maximum of 256 values in any bitmap - no matter what the compression scheme. Authoring bitmaps that use a limited value range will create posterized bitmaps.

| Use This | Not This|
|----------|---------|
|![Bitmap using a full range as an example of the correct type of bitmap to use](./media/H2_Guides_EffectiveBitmapCorrect.jpg)|![Bitmap using one value as an example of the incorrect type of bitmap to use](./media/H2_Guides_EffectiveBitmapIncorrect.jpg)|

It’s possible to “turn down” a bitmaps value range in the game. For example in the specular (which uses the alpha channel of the base_map) you can use a darker color for the specular_color, which will allow you to use a wider value range that gives you better control over the effect you are trying to achieve.

Here’s an example with a cloud map. The left half of this image uses a full value range bitmap (0-255) that is scaled in the tag while the right half uses a bitmap with a value range of 0-63:

![View of a bitmap separated into two sections, the left half showing the full value range of 0 - 255 and the right half using a value range of 0 - 63.](./media/H2_Guides_BitmapExample01.jpg)

Fig 1. Difference between full range of 0-255 on the left and a range of 0-63 on the right.

This actually makes a bigger improvement than increasing the bit-depth. In this final example, the left half of this image uses a monochrome compression setting (8 bits/pixel) while the right half used DXT1 (4 bits/pixel). The left half (monochrome) uses twice as much memory as the right.

![View of a bitmap separated into two sections, the left half showing a monochrome compression and the right half showing a DXT1 compression.](./media/H2_Guides_BitmapExample02.jpg)

Fig 1. Difference between monochrome and DXT1 compressions.
