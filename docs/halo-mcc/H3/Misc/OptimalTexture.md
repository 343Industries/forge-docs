---
title: Halo 3 Misc Optimal Texture Size Reference #Required; page title is displayed in search results. Include the brand.
description: Misc Optimal Texture Size Reference for Halo 3 Modding Documentation. #Required; article description that is displayed in search results. 
author: mjordan343 #Required; your GitHub user alias, with correct capitalization.
ms.author: mjordan #Required; microsoft alias of author; optional team alias.
ms.service: halo-mcc #Required; service per approved list. slug assigned by ACOM.
ms.topic: quickstart #Required; leave this attribute/value as-is.
ms.date: 03/17/2022 #Required; mm/dd/yyyy format.
ms.custom: template-quickstart #Required; leave this attribute/value as-is.
---

# Optimal Texture Size Reference

The following is intended as a reference for use while creating .bitmap tags.

## **Compressed Textures**

- **Supported Sizes**: Any multiples of 4

- **Optimal Sizes**: Multiples of 128 (128, 256, 384, 512, 640, 768, 896, 1024, ...)

> [!WARNING]
> As soon as you go over a multiple of 128, you use the same memory as the next higher multiple of 128!

So, a 132x260 texture uses the same amount of memory as a 256x384 texture. Also, the small mip map levels waste memory so, if possible, use a few higher-rez textures instead of many low-rez textures.

Again, it is much better to use a single large texture than to use multiple small ones that add up to the same size. For example, four compressed textures that are 128x128 use twice as much memory as a single 256x256 compressed texture. Refer to the memory efficiency chart below for details:

**Memory Efficiency for Compressed Textures**

|**Bitmap Sizes**|**Memory Efficiency**|
|----|----|
|16|(2.08%)|
|32|(4.17%)|
|64|(11.11%)|
|128|(33.33%)|
|256|(66.66%)|
|384|(70.59%)|
|512|(88.89%)|
|640|(68.03%)|
|768|(79.99%)|
|896|(89.50%)|
|1024|(96.97%)|

## **Uncompressed Textures**

- **Supported Sizes**: Any

- **Optimal Sizes**: multiples of 32 (32, 64, 96, 128, 160, 192, 224, 256, 288, ...)

> [!WARNING]
> As soon as you go over a multiple of 32, you use the same memory as the next higher multiple of 32!

Also, for 32x32 and smaller mip levels, 2-channel and 1-channel textures use the same memory as 4-channel textures. So, at low resolutions, you don't gain anything by using fewer channels.
