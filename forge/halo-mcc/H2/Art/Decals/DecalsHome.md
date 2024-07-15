---
title: Halo 2 Decals Overview #Required; page title is displayed in search results. Include the brand.
description: Decals Overview for Halo 2 Decals in MCC Modding Documentation. #Required; article description that is displayed in search results. 
author: mjordan343 #Required; your GitHub user alias, with correct capitalization.
ms.author: mjordan #Required; microsoft alias of author; optional team alias.
ms.service: halo-mcc #Required; service per approved list. slug assigned by ACOM.
ms.topic: quickstart #Required; leave this attribute/value as-is.
ms.date: 11/10/2022 #Required; mm/dd/yyyy format.
ms.custom: template-quickstart #Required; leave this attribute/value as-is.
---

# H2 Decals Overview

We have 4 kinds of decals in Halo 2. Each was created to solve different problems.

1. wrapped (Halo 1)

1. decorator quad

1. decorator projected

1. overlay geometry.

## Wrapped

- **Description**: Geometry projects over environment and poops directly beneath them and "properly" wrap the adjacent geometry.

- **Implementation**: Placed in Sapien or created from an effect.

- **Render modes**: alpha blends, multiplies, effects: (add, subtract, min, max, color blend)

- **Strengths**: Only decals that wrap. Never fade. Most current render modes.

- **Weaknesses**: More expensive because Sapien ones never fade. Wrap is sometimes not correct looking.

- **Lighting**: We are going to make the alpha blended ones lit by the lightmaps.

- **Used for**: Blast marks, scratches, blood, painted signs big enough you need wrapping or don't want to fade.

## Decorator Quad

- **Description**: A planar quad appears with the bitmap registration point at the location picked on the environment or poop in sapien, aligned to the surface's normal. Fade at distance.

- **Implementation**: Placed in Sapien by clicking a point on the structure or poop.

- **Render modes**: alpha blend (we could add more if needed, but we want to keep the number of shaders down).

- **Strengths**: Cheapest of all decals.

- **Weaknesses**: Need to be small enough to fit on a struture/poop plane because they don't conform to geometry and for you to not notice them fade at distance.

- **Lighting**: We are going to make the alpha blended ones lit by the lightmaps.

- **Used for**: Lots of smallish quads you can put everywhere.

## Decorator Projected

- **Description**: This geometry conforms to the structure or poop by projecting into a box and creating a bunch of sub-structure-triangles. Fade at distance.

- **Implementation**: Geometry is created by a projector box onto geometry in Sapien.

- **Render modes**: alpha blend (we could add more if needed, but we want to keep the number of shaders down)

- **Strengths**: Great for putting detail on complicated geometry.

- **Weaknesses**: Does not wrap, only projects from the box.

- **Lighting**: We are going to make the alpha blended ones lit by the lightmaps.

- **Used for**: Grime in corners or edges, applying to complicated geometry

## Overlay Geometry

- **Description**: Geometry hand crafted, for that beechwood aged flavor.

- **Implementation**: Created in DCC, assigned an overlay shader

- **Render modes**: double multiply (we can easily add more modes that are not alpha blended)

- **Strengths**: Complete control over the geometry created. Never fade.

- **Weaknesses**: Takes a lot of time to create wrapping.

- **Lighting**: These get applied after lighting, lighting never alters it.

- **Used for**: Whatever (non-lightmap-lit) use you want

## DYNAMIC LIGHTS AND DECALS

Dynamic lights will not really affect any of these. We made this tradeoff because of the shader LOD system, and do not have time to do another system where dynamic lights can affect them. You will, however, have a choice by render mode whether a decal gets rendered before or after dynamic lights. Pre-dynamic-light ones will be slightly faded out by the light. Post dynamic light ones will look like they are lit by the dynamic light if they are multiplicative, but alpha-blended ones will not be affected at all by the dynamic light.
