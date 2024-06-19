---
title: Halo 3 Shaders Alpha Test Properties #Required; page title is displayed in search results. Include the brand.
description: Shaders Alpha Test Properties for Halo 3 Modding Documentation. #Required; article description that is displayed in search results. 
author: mjordan343 #Required; your GitHub user alias, with correct capitalization.
ms.author: mjordan #Required; microsoft alias of author; optional team alias.
ms.service: halo-mcc #Required; service per approved list. slug assigned by ACOM.
ms.topic: quickstart #Required; leave this attribute/value as-is.
ms.date: 03/17/2022 #Required; mm/dd/yyyy format.
ms.custom: template-quickstart #Required; leave this attribute/value as-is.
---

# Alpha Test Properties

Alpha Testing defines whether a pixel should be rendered or ignored.

> [!NOTE]
> This is different than alpha blending. With alpha test, the unused (not rendered) pixels are discarded, whereas they are still used in alpha-blend— thus making alpha test the cheaper solution.

![Three images. One black and white noise map. The second image is a black and white checker pattern. The third image is an object withteh two maps applied.](./media/H3_Shaders_AlphaExample.png)

Figure 1 - Two maps combined (left and middle) to affect an object (right).

There are two options for alpha test parameters: None and simple.

## **None**

[no parameters] — No alpha testing. This is the default setting.

## **Simple**

alpha_test_map [bitmap] — Modulates all other maps in the shader based on the color value of the alpha channel. Any pixel with a value less than 128 (50% gray) will not be rendered. Pixels with a value greater than 128 (50% gray) will be rendered on the screen. White in the alpha channel will render, Black will be transparent.

The alpha channels in both the base_map and the alpha_test_map are combined to determine which pixels get drawn and which do not. Grayscale values over 50% are drawn, under 50% are not. The RGB channels of the alpha_test_map are not used.
