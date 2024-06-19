---
title: Halo 3 Instance Objects Home #Required; page title is displayed in search results. Include the brand.
description: Instance Objects Home for Halo 3 Modding Documentation. #Required; article description that is displayed in search results. 
author: mjordan343 #Required; your GitHub user alias, with correct capitalization.
ms.author: mjordan #Required; microsoft alias of author; optional team alias.
ms.service: halo-mcc #Required; service per approved list. slug assigned by ACOM.
ms.topic: quickstart #Required; leave this attribute/value as-is.
ms.date: 03/17/2022 #Required; mm/dd/yyyy format.
ms.custom: template-quickstart #Required; leave this attribute/value as-is.
---

# Instance Objects

Instancing is a way of making cheap copies of an object. The math used to render the original can be used again to create the instances. Instance objects are one of the reasons that we switched to the .ASS file format.

> [!IMPORTANT]
> This section is built from the original documentation and is tailored for use in 3ds Max, but the important principles can be used in any 3d program.

The following sections cover these topics:

## [*Light Map Resolution*](LightMapResolution.md)

## [*Damage Sections and States Tag Info*](DamageSections.md)

## [*Functions*](Functions.md)

## [*Collision*](Collision.md)

## [*Pathfinding Policy*](PathfindingPolicy.md)

### **Instance Objects in 3ds Max**

In order to make poops, a number of criteria must be true of instance objects:

- Be instances in 3ds Max

- Be named with % at the beginning

- Cannot have different modifiers or materials

- Be exported as an ASS file — you cannot copy, reference, add modifiers, or reference different materials in 3ds Max — use instance objects ONLY

And here are some facts worth noting:

- Instances can have uniform scaling — it does not break the instance.

- Non-uniform scaling is simply chucked out at export (when you create the ASS file from within 3ds Max)— it uses the X-axis values for all three axes.

- You can have unique instances in the game— poops that do not share instance definitions with any other objects— they just don’t save anything.

### **Draw Distances on Poops**

Putting @30-20 into the suffix of the name of an instance now sets that as its fade pixel sizes (otherwise controlled in the scenario tag for that bsp). It will start fading when its bounding sphere is 30 pixels on screen and not draw at all when less than 20 pixels on screen.

> [!NOTE]
> Add letter or character text (like an underscore) after the immediately after the pixel fade numbers in the suffix so extra numbers aren't added by 3ds Max during an auto increment . For example:

%-?name01@10-5_01

The _01 at the end is merely a buffer, making sure the pixel fade distances don't get added to by 3ds Max. Otherwise, instance stencil pixel culling is controlled per-bsp by default instance fading values. In the scenario tag in the structure bsps block at the top. If you leave these at 0 it uses the hard-coded values of 36, 30.

### **Errors**

Instances with open edges will not be collidable.

### **Markers**

You can attach lights and leaf widgets to structure markers. Use debug_structure_markers to see them in-game.

### **Regions and Permutations**

Object Instances can belong to regions and permutations. Naming should be %(permutation region)instance00, just like in the 3ds Max Material Name Field.

This will override the permutation and region set in the 3ds Max material name field.

### **XRef'ing Instance Objects**

Xrefs of instanced objects should now work but nested XRefs (xrefing an object from a file, which itself is an xref from a third file) are not supported well. If you XRef multiple instances, we will write a single object definition but the name of that object may be taken from any one of the instances— not necessarily the ’r;root’ object.

We export the name of the xref’ed object in the object definition, not the local object name.

### **Lighting Nomenclature on Poop Prefixes**

Quality of lighting-wise, all three lighting schemes are doing the same per-pixel calculations, so you can get the same look from all three— the only difference is where and how often the lighting is stored.

|Summary| -     |
|-------|-------|
|%|single-probe when your instance is less than 8 world units, and per-pixel when it is greater than 8 world units|
|%?|per vertex|
|%!|per-pixel (in the same bitmap as the structure)|

### **Single Probe**

Cheap but effective lighting. Footprint memory cost is negligible.

Simply leave the poop without any specific lighting prefix. If your poop has a diameter smaller than 8 world units it will automatically become single probe. Over this size it becomes per-pixel.

```
Example: %probe_01
```

Also, you can force a poop to be single probe. Use the symbol > for this.

```
Example: %>probe_01
```

Single probe poops have prt and are lit like our objects in the world.

Single probe can be effective for cleaning light map errors on single poops (particularly those partially bisecting something else).  If your poop has little light transition over the breadth of it— this is a good naming convention to use.

Conversely, single probe poops behave very poorly if the lighting is changing much across the poop. For example, in a lighting gradient, two poops side by side look very bad because there is a harsh lighting line where they meet.

> [!NOTE]
> Single probe and per-vertex are lit at the vertex level and can show tessellation artifacts (that is, show the underlying tessellation of the object with lighting variation).

### **Per Pixel**

Per pixel is good to get fidelity and to show lighting variation but it sucks up resolution along with everything else in the lightmap— this is a costly method depending on naming convention used and complexity of poop and shadow contrast thereon.

A prefixing exclamation mark,’!’, is used to denote per pixel. 

```
Example: %!probe_01
```

This can be augmented with a suffixing number in parentheses. The greater the number the more resolution from the lightmap the object gets.

```
Example: %!probe_01(4)
```

> [!NOTE]
> Per-pixel instances do steal resolution from your structure (bsp).

### **Per Vertex**

Uses a separate and additional per-vertex lightmap budget. Cost is dependent purely on complexity/vert count of poop.

A question mark is used to denote per vertex.

```
Example: %?probe_01
```

Per-vertex lightmaps cost us 20 bytes per vertex (this is already compressed). 20 bytes * 1 million verts = 20M. So, a 10 k vert poop would cost 0.2 mbs in per vertex lightmaps (this is in addition to per pixel light maps). Per pixel is good for getting light variation across an object in a specific and cheap fashion (you can cut in where the shadows will fall to eradicate errors/light better).
