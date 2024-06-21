---
title: Halo 3 Shaders Analytical Anti Shadow Control Properties #Required; page title is displayed in search results. Include the brand.
description: Shaders Analytical Anti Shadow Control Properties for Halo 3 Modding Documentation. #Required; article description that is displayed in search results. 
author: mjordan343 #Required; your GitHub user alias, with correct capitalization.
ms.author: mjordan #Required; microsoft alias of author; optional team alias.
ms.service: halo-mcc #Required; service per approved list. slug assigned by ACOM.
ms.topic: quickstart #Required; leave this attribute/value as-is.
ms.date: 03/17/2022 #Required; mm/dd/yyyy format.
ms.custom: template-quickstart #Required; leave this attribute/value as-is.
---

# Analytical Anti-Shadow Control Properties

This is a way to turn off unwanted analytical specularity in the shadows, which causes shadowy areas to appear brighter than the adjacent lit area.

The valid range is 0-1. 0 is default, meaning specularity is not attenuated at all. 1.0 is pretty aggressive attenuation, so aggressive that it might kill some portion of specularity even in the lit area. You should probably start from 0, and increase the value in small increments to find the sweet spot for your shader. Values in the range of 0.1 to 0.2 generally do the job.

![View of shadows with no blur that look incorrect due to keeping the default setting of zero.](./media/H3_Shaders_AntiShadow0.png)

Figure 1 - analytical_anti_shadow_control: 0 (default).

Notice the shadowy area on the left wall is actually brighter than the lit areas.

![View of shadows blurred slightly due to the shadow control setting being set to zero point one five.](./media/H3_Shaders_AntiShadow015.png)

Figure 2 - analytical_anti_shadow_control: 0.15.

Looks much better.
