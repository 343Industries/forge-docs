---
title: Halo 3 PRT Notes #Required; page title is displayed in search results. Include the brand.
description: PRT Notes for Halo 3 Modding Documentation. #Required; article description that is displayed in search results. 
author: mjordan343 #Required; your GitHub user alias, with correct capitalization.
ms.author: mjordan #Required; microsoft alias of author; optional team alias.
ms.service: halo-mcc #Required; service per approved list. slug assigned by ACOM.
ms.topic: quickstart #Required; leave this attribute/value as-is.
ms.date: 03/21/2022 #Required; mm/dd/yyyy format.
ms.custom: template-quickstart #Required; leave this attribute/value as-is.
---

# Notes

PRT stands for Pre-Computed Radiance Transfer and is a way of storing multiple per-vertex lighting solutions. At runtime, these possible solutions are compared to light probe information to light the object on a per-vertex basis.

- **Console Command**: render_disable_prt

## **PRT Regions and Permutations**

Assume you have an object with three regions: Region zero has four permutations, region one has three permutations and region two has four permutations.

Only the initial permutation will cast and receive shadows— all other permutations can only receive shadows.

And note:

- Regions can shadow themselves.

- A region will never cast shadows on permutations of the same region.

![Chart showing the breakdown of permutations based on casts received in each region.](./media/H3_PRT_PermutationExample.png)

Figure 1 - Permutation Example

For example: Permutation zero of region one (R1P0) will cast shadows on: R0P0, R0P1, R0P2, R0P3, R2P0, R2P1, R2P2 and R2P3 — but not on R1P1 and R1P2 (see Figure 2).

![Chart showing the breakdown of permutations based on casts received in each region with red arrows showing which regions would have shadows casted on them for permutation zero of region one.](./media/H3_PRT_CastingShadows.png)

Figure 2 - Casting Shadows

Permutation zero of region one (R1P0) will receive shadows from R0P0 and R2P0 only (and itself, of course). See Figure 3.

![Chart showing the breakdown of permutations based on casts received and which regions permutation zero of region one would receive shadows from.](./media/H3_PRT_ReceiveShadows.png)

Figure 3 - Receiving Shadows

## **Setting Default Shadow-Casting Permutation**

![View of the default shadow cast settings in guerilla with fields for region and shadow cast permutation.](./media/H3_PRT_DefaultShadow.png)
