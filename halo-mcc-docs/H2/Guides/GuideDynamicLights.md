---
title: Halo 2 Guides Dynamic Lights Best Practices #Required; page title is displayed in search results. Include the brand.
description: Dynamic Lights Best Practices for Halo 2 Guides in MCC Modding Documentation. #Required; article description that is displayed in search results. 
author: mjordan343 #Required; your GitHub user alias, with correct capitalization.
ms.author: mjordan #Required; microsoft alias of author; optional team alias.
ms.service: halo-mcc #Required; service per approved list. slug assigned by ACOM.
ms.topic: quickstart #Required; leave this attribute/value as-is.
ms.date: 11/09/2022 #Required; mm/dd/yyyy format.
ms.custom: template-quickstart #Required; leave this attribute/value as-is.
---

# How-To - Dynamic Lights Best Practices

Dynamic lights are fairly expensive in general. You should never have more than 4 reasonably sized lights in view at any given time. A reasonable size is less than 10 world units square at the base of what it’s shining on. The Halo 2 shadowing techniques will not look good for any light larger than this. Because they are so expensive, these are some guidelines to make them cheaper:

- Use the smallest FOV on the light you can. This makes your shadow look better and gives a tighter fitting bounding sphere.

- Tesselate the environment in the area where the light is hitting so that we're not re-rendering the entire floorway of your room for each one. Dynamic lights are in general predominantly fillrate bound.

- Set a closer shadow or illumination fade distance so both systems can deactivate

- Use these flags whenever you can:

    - doesn't shadow environment (if you don't obviously see shadow off of structure, disable them!)

    - doesn't shadow parent (shadows not cast from object you are attached to)

    - ignore parent object (neither shadows nor illumination on/from object you are attached to)

    - no stencil shadow (no shadows at all on this light)

    - doesn't shadow objects (do not cast shadows from objects in the light)

    - no specular (especially on sphere lights, it's a killer there)

    - set the shadow antialiasing taps to 1-tap

- set the shadow quality bias (buffer resolution) negative (turn on rasterizer_shadow_buffer_debug and it will show you the actual resolution currently being used by the shadow buffer)

- pull the cutoff plane in as close to behind what you are shining on as possible so we get the best sphere fit (turn on debug_lights to see the sphere fitting - this sphere is also where we lod and fade the light from)

- don’t set a very far distance between the falloff and cutoff plane. In general we don’t need a huge fade interpolation distance built into lights.

- Be careful placing large lights and be thoughtful of which portals it will be shining through (it may be lighting clusters you don’t realize)

## Use Debug Commands

*debug_lights* - shows you the light geometry, the bounding sphere used for lod’ing, shows you if it is using specular (2 passes means specular, 1 pass is just diffuse). Also you can see all active lights.

*rasterizer_shadow_buffer_debug* - shows you the resolution of the shadow buffer being used (only displays if shadows are active)

*render_layer_enable diffuse or specular* - 0 or 1 to see how much the light’s diffuse or specular are effecting the scene
