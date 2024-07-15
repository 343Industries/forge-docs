---
title: Halo 3 Misc Gravity Lifts #Required; page title is displayed in search results. Include the brand.
description: Misc Gravity Lifts for Halo 3 Modding Documentation. #Required; article description that is displayed in search results. 
author: mjordan343 #Required; your GitHub user alias, with correct capitalization.
ms.author: mjordan #Required; microsoft alias of author; optional team alias.
ms.service: halo-mcc #Required; service per approved list. slug assigned by ACOM.
ms.topic: quickstart #Required; leave this attribute/value as-is.
ms.date: 03/17/2022 #Required; mm/dd/yyyy format.
ms.custom: template-quickstart #Required; leave this attribute/value as-is.
---

# Gravity Lifts

To anchor a crate with working renders and physics models or to make the physics capsule push in a direction, you need to create a phantom volume in your physics tag. Do the following:

1. Go to your physics tag and r;Add a phantom volume (3rd field down). In this phantom volume you identify the appropriate marker (which is linked to the model).

1. Set the velocity and acceleration. Look at other lift's physics tags to determine the axis and directional velocity and acceleration to get a good start on appropriate settings.

1. Go to the materials area and link the phantom volume to the respective material.

> [!NOTE]
> You need to have a unique material per phantom volume. Thus, if your lift is composed of three separate phantom volumes, you need three separate materials.
