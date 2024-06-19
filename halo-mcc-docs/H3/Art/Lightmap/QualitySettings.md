---
title: Halo 3 Lightmap Quality Settings #Required; page title is displayed in search results. Include the brand.
description: Lightmap Quality Settings for Halo 3 Modding Documentation. #Required; article description that is displayed in search results. 
author: mjordan343 #Required; your GitHub user alias, with correct capitalization.
ms.author: mjordan #Required; microsoft alias of author; optional team alias.
ms.service: halo-mcc #Required; service per approved list. slug assigned by ACOM.
ms.topic: quickstart #Required; leave this attribute/value as-is.
ms.date: 03/17/2022 #Required; mm/dd/yyyy format.
ms.custom: template-quickstart #Required; leave this attribute/value as-is.
---

# Lightmap Quality Settings

This information is for the quality setting when running lightmaps using the tool command

## **Quality Settings**

- **Draft** — Does direct only (first bounce) illumination, no bounced light. What makes it different from direct_only is that it casts fewer rays per light. This makes the lighting really harsh. The sun, for example, is done with 64 rays in direct only so you get nice soft shadows from in (in draft there's only one ray). It's supposed to be the "I don't care about anything except how much light is hitting this floor" setting.

- **Direct Only** — A slightly slower first bounce version. The direct lighting will appear the same that it will in the low quality setting, so your shadow edges should be fairly smooth.

- **Low** — Direct only, but we also cast photons, perform the radiance estimate, compute exit illumination, and do final gather to get bounced lighting. The final gather uses an iterative algorithm that keeps casting rays until the variance (splotchiness in the lighting) is below some threshold. For low, that threshold is pretty high to make it finish quicker, but the bounced lighting gets splotchy as a result.

- **Medium** — The main difference from low is that we subdivide each lightmap pixel and do a 2x2 multisample. This means each pixel takes at least four times as long as on medium, but the benefit is that hard shadow edges get even smoother and bounced lighting blends better. The threshold for final gather is a little lower as well.

- **High** — In this setting we subdivide each pixel into a 3x3 multisample, so about 2.5x longer than medium for each pixel. Also, the threshold for final gather is lower. This is fairly representative of what the final lightmaps will look like.

- **Super** —  When closing out maps we run on super — it does 3x3 multisample like high, but has a lower threshold for final gather. The jobs take forever to finish, but they end up as splotch-free as we can reasonably hope.
