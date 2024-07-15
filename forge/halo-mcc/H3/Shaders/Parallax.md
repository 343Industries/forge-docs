---
title: Halo 3 Shaders Parallax Properties #Required; page title is displayed in search results. Include the brand.
description: Shaders Parallax Properties for Halo 3 Modding Documentation. #Required; article description that is displayed in search results. 
author: mjordan343 #Required; your GitHub user alias, with correct capitalization.
ms.author: mjordan #Required; microsoft alias of author; optional team alias.
ms.service: halo-mcc #Required; service per approved list. slug assigned by ACOM.
ms.topic: quickstart #Required; leave this attribute/value as-is.
ms.date: 03/17/2022 #Required; mm/dd/yyyy format.
ms.custom: template-quickstart #Required; leave this attribute/value as-is.
---

# Parallax Properties

Parallax defines a special kind of bump mapping where pixels may occlude other pixels in the same map.

> [!NOTE]
> This is an expensive option and should be used sparingly.

Parallax Mapping uses a specially formatted .bitmap tag called a **height map**. When you import a bitmap to use as a height map, either name it with a _height at the end, or make sure and select *Height Map* in the bitmap tag (and then re-import). The .bitmap parameter bump_height has nothing to do with the height of the parallax mapping. The height of the parallax is based solely on the green channel of the height_map.

> [!IMPORTANT]
> Parallax mapping is a very subtle technique. If you set the scale too high, or have too much contrast in your bitmap when you import it, the parallax mapping will look ugly on your surface.

## There are three options for Parallax

### **off**

- **[no parameters]** — No parallax mapping. This is the default setting.

### **simple**

- **height_map** [bitmap] — Differences in pixel values are used to determine placement and occlusion of pixels on the surface. Based on the differences in Value (lightness/brightness) between pixels in the green channel of the bitmap.

- **height_scale** [value]— The amount of displacement/occlusion applied to the affected pixels.

### **interpolated**

The interpolated parallax map makes two corrections to the location of light and displacement of pixels across the surface and then averages between the two. This is more expensive than the standard parallax mapping option.

- **height_map** [bitmap] — Differences in pixel values are used to determine placement and occlusion of pixels on the surface. Based on the differences in value (lightness/brightness) between pixels in the green channel of the bitmap.

- **height_scale** [value] — The amount of displacement/occlusion applied to the affected pixels.
