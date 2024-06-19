---
title: Halo 2 Decorators Overview #Required; page title is displayed in search results. Include the brand.
description: Decorators Overview for Halo 2 Decorators in MCC Modding Documentation. #Required; article description that is displayed in search results. 
author: mjordan343 #Required; your GitHub user alias, with correct capitalization.
ms.author: mjordan #Required; microsoft alias of author; optional team alias.
ms.service: halo-mcc #Required; service per approved list. slug assigned by ACOM.
ms.topic: quickstart #Required; leave this attribute/value as-is.
ms.date: 11/10/2022 #Required; mm/dd/yyyy format.
ms.custom: template-quickstart #Required; leave this attribute/value as-is.
---

# H2 Decorators Overview

The decorator system is used to create a large number of (relatively) low-cost objects in an environment, such as grass or rock.

Decorators generally fall into three types: **models**, **decals and** **quads**. While models use geometry defined in a 3D application, both decals and quads are **sprites** that use a simple pre-defined geometry to display a bitmap. Decals are placed on the surface of BSP geometry while quads can be placed anywhere in a level.

Decorators use a simplified shader system but also save resources by sharing the same shader between decorators. For this reason **you should always use the minimum number of shaders as possible**. All decorators must use .shader_templates in tags\shaders\shader_templates\decorators\

### SAPIEN NOTE

To reset the placement and lighting of decorators in Sapien, use the console command

```
decorator_rebuild_all
```

## DECORATOR CLASSES

There are six types of decorators: **model, floating decal, projected decal, screen facing quad, axis rotating quad**, and **cross quad**.

### Model

Model is the only class of decorators that you can build geometry for. Objects are created in your 3D application as a bulk file, and exported as a .jmi file. Note that all decorator models are two-sided. No parsed materials.

- Source: .jmi model file (bulk file, can have mutiple elements)

- Import: use tool: import-decorator-set

- Creates .decorator_set

- Shader: use decorator_tex.shader_template only.

- Lighting: lit by lightmaps, not lit by dynamic lights

- LOD: smallify w/distance

> [!NOTE]
> No damage states, does **not** accept decals

### Floating Decal

A floating decal is a sprite that is placed on the surface of BSP geometry in Sapien. Source is from bitmap only - there is no user-defined geometry. The default size of the final sprite in game is 256 pixels per world unit.

- Source: .tif bitmap file (sequenced sprite plate)

- Import: use tool: bitmaps (set .bitmap = sprite, sprite_usage for blend function)

- Creates: .bitmap tag (.decorator_set must be created or edited seperately)

- Shader: use decorator_decal_paint.shader_template (alpha blended), decorator_decal_paint_additive.shader_template for additive or decorator_decal_paint_multiply.shader_template for multiplicative

- Lighting: lit by lightmaps from underlying object (uses ovelay), lit by dynamic lighting from underlying object (uses ovelay)

- LOD: fade w/distance

> [!NOTE]
> Will accept decals

### Projected Decal

A projected decal is a sprite that is projected on to a surface of BSP geometry in Sapien. It has the same attributes as a floating decal, except it is projected (smeared) onto the surface so that it will follow the contours of the underlying geometry. Source is from bitmap only - there is no user-defined geometry. The default size of the final sprite in game is 256 pixels per world unit.

- Source: .tif bitmap file (sequenced sprite plate)

- Import: use tool: bitmaps (set .bitmap = sprite, sprite_usage for blend function)

- Creates: .bitmap tag (.decorator_set must be created or edited seperately)

- Shader: use decorator_decal_paint.shader_template (alpha blended), decorator_decal_paint_additive.shader_template for additive or decorator_decal_paint_multiply.shader_template for multiplicative

- Lighting: lit by lightmaps from underlying object (uses ovelay), lit by dynamic lighting from underlying object (uses ovelay)

- LOD: fade w/distance

> [!NOTE]
> Will accept decals

### Screen Facing Quad

A Screen Facing Quad is a free-standing sprite that always faces the camera.

- Source: .tif bitmap file (sequenced sprite plate)

- Import: use tool: bitmaps (set .bitmap = sprite, sprite_usage for blend function)

- Creates: .bitmap tag (.decorator_set must be created or edited seperately)

- Shader: use decorator_tex.shader_template only.

- Lighting: lit by lightmaps, not lit by dynamic lights

- LOD: smallify w/distance

> [!NOTE]
> No damage states, does not accept decals

### Axis Rotating Quad

An Axis Rotating Quad is a free-standing sprite with one axis always along normal of surface that it is placed on with the other two always facing the camera.

- Source: .tif bitmap file (sequenced sprite plate)

- Import: use tool: bitmaps (set .bitmap = sprite, sprite_usage for blend function)

- Creates: .bitmap tag (.decorator_set must be created or edited seperately)

- Shader: use decorator_tex.shader_template only.

- Lighting: lit by lightmaps, not lit by dynamic lights

- LOD: smallify w/distance

> [!NOTE]
> No damage states, does not accept decals

### Cross Quad

A Cross Quad is a free-standing sprite comprised of two cards perpendicular to each other. They are fixed so do not move with the camera.

- Source: .tif bitmap file (sequenced sprite plate)

- Import: use tool: bitmaps (set .bitmap = sprite, sprite_usage for blend function)

- Creates: .bitmap tag (.decorator_set must be created or edited seperately)

- Shader: use decorator_tex.shader_template only.

- Lighting: lit by lightmaps, not lit by dynamic lights

- LOD: smallify w/distance

> [!NOTE]
> No damage states, does not accept decals

## .decorator_set TAG
 
**.decorator_set** tag is created when importing a decorator model using import-decorator-set, or they can be created in Guerilla by selecting **File - New** and setting Group equal .**decorator_set**.

### SHADERS

Entries for all shaders used in the decorator set.

**shader**: link to .shader tag(s).

**lighting min scale**: range: 0-2 (0 defaults to .4) - range for how 'directional' light is, with 0 = ambient/diffuse and 2 = very directional (sharp shadows).

**lighting max scale**: range: 0-2 (0 defaults to 2).

### CLASSES

Entries for classes used in the decorator set. You can have multiple classes per set.

**name**: name that will be shown in Sapien.

**type**: model, floating decal, projected decal, screen facing quad, axis rotating quad, or cross quad

**scale**: controls size of entire class with one being equal to what is authored.

### PERMUTATIONS

Must have an entry for each permutation.

**name**: name that will be shown in Sapien.

**shader**: pick from shaders defined above.

**flags**: 

- **align to normal**: will align with normal of face decorator is placed on.

- **only on ground**: will only appear on horizontal surfaces but not on vertical.

- **upright**: vertical axis locked.

**fade distance**: N/A.

- **close**: start fade = 53' finish fade = 80'

- **medium**: start fade = 107' finish fade = 160'

- **far**: start fade = 160' finish fade = 240'

**index**: set index for specific decorator to be used in this permutation. For models, this will be the index as listed in the MODELS block (see below). For sprites (quads and decals) this will be the .bitmap tag sprite index.

**distribution weight**: weight for this permutation when put down in a ramdom distribution in Sapien. This number is simply compared with the other entries in the permutation. Zero will NOT appear in random distribution.

**scale**: controls size of this permutation with one being equal to what is set in class scale (see above).

**tint 1**: permutation will be tinted (multiplied) by this color range with white having no effect.

**tint 2**: see above.

**base map tint percentage**: samples base map of decorator placed upon - straight multiply! try this with grayscale only (no color) ? not for decals?

**lightmap tint percentage**: models and sprites ONLY not for decals samples lightmap double-multiply so gray lightmap has no effect with zero equals self-illuminated

**wind scale**: does NOT work.

## **THERE IS NO USER-EDITABLE INFORMATION BELOW THIS POINT**

### **MODELS**

lists the [index number]: [model name] (as named in the origin node in the bulk file)

> [!NOTE]
> That the **index** is what gets referenced in the PERMUTATION, not the **name**

**model name**: as named in the origin node in the bulk file

**index start**: N/A.

**index count**: N/A.

### **RAW VERTICES** 

**position**: N/A.

**normal**: N/A.

**tangent**: N/A.

**binormal**: N/A.

**texcoord**: N/A.

### **INDICES** 

**index**: N/A.

### **CACHED DATA** 

### **BLOCK INFO** 

**block offset**: N/A.

**block size**: N/A.

**section data size**: N/A.

**resource data size**: N/A.

### **RESOURCES** 

**owner tag section offset**: N/A.

Additional information on Decorators can be found in the following pages:

[Floating Decals](../Decorators/DecoratorsFloatingDecals.md)

[Models](../Decorators/DecoratorsModels.md)

[Screen Facing Quads](../Decorators/DecoratorsScreenFacingQuads.md)
