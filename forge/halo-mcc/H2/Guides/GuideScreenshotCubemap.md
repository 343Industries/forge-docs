---
title: Halo 2 Guides screenshot_cubemap Command #Required; page title is displayed in search results. Include the brand.
description: screenshot_cubemap Command for Halo 2 Guides in MCC Modding Documentation. #Required; article description that is displayed in search results. 
author: mjordan343 #Required; your GitHub user alias, with correct capitalization.
ms.author: mjordan #Required; microsoft alias of author; optional team alias.
ms.service: halo-mcc #Required; service per approved list. slug assigned by ACOM.
ms.topic: quickstart #Required; leave this attribute/value as-is.
ms.date: 11/09/2022 #Required; mm/dd/yyyy format.
ms.custom: template-quickstart #Required; leave this attribute/value as-is.
---

# How-To - Using screenshot_cubemap Command

There is a console command called

```
screenshot_cubemap
```

...that renders a cube map of an environment from the viewpoint of the camera.

## **How to Use**

Position the camera at the point where you want to render the cubemap. It doesn't matter which way the camera is pointing - the cube map is always rendered in the correct XYZ orientation.

> [!NOTE]
> that you must be in the flying camera, otherwise you will render the HUD into the cube map.

Open the console (by pressing the ~ key) and type in:

```
screenshot_cubemap [name]
```

This will create a TIF file called name.tif in your Halo 2 directory. You can then convert it into a bitmap tag for use in the game as an environment map.

| Screenshot Location | Generated Cubemap |
|---------------------|-------------------|
|![View of the area in the level where the cubemap screenshot will be generated from.](./media/H2_Guides_CubemapCommandScreenshot.jpg)|![View of the cubemap that is generated from the console command based on the screenshot taken.](./media/H2_Guides_CubemapCommandCubemap.jpg)|
