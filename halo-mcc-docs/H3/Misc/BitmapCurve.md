---
title: Halo 3 Misc Bitmap Curve #Required; page title is displayed in search results. Include the brand.
description: Misc Bitmap Curve for Halo 3 Modding Documentation. #Required; article description that is displayed in search results. 
author: mjordan343 #Required; your GitHub user alias, with correct capitalization.
ms.author: mjordan #Required; microsoft alias of author; optional team alias.
ms.service: halo-mcc #Required; service per approved list. slug assigned by ACOM.
ms.topic: quickstart #Required; leave this attribute/value as-is.
ms.date: 03/17/2022 #Required; mm/dd/yyyy format.
ms.custom: template-quickstart #Required; leave this attribute/value as-is.
---

# Bitmap Curve

In each .bitmap tag is a setting which can allow your bitmaps to render up to twice as fast in the game: Bitmap Curve Mode. It's not a freebie though— the fast mode can look worse if the texture is very dark or very smooth. For the most part, however, they will be indistinguishable. The bitmap importer will automatically choose the fast mode if your bitmap is bright and will revert to the slow high-quality mode if the bitmap is dark.

You can manually control the bitmap curve setting within your .bitmap tag (see Figure 1)

- **Choose Best**: The importer chooses for you based on how bright your bitmap is.
- **Choose Fast**: Always uses the fast (but possibly ugly) mode.
- **Choose Pretty**: Always uses the slower, high-quality, mode.

![View of the bitmap file with an arrow pointing towards the curve mode set to choose best.](./media/H3_Misc_CurveMode.png)

Figure 1 - .bitmap tag and the Bitmap Curve Mode setting.

> [!NOTE]
> You need to re-import your bitmap after adjusting this setting for the changes to take effect!
