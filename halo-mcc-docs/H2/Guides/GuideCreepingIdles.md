---
title: Halo 2 Guides Fix Creeping Idle Animations #Required; page title is displayed in search results. Include the brand.
description: Fix Creeoping Idle Animations for Halo 2 Guides in MCC Modding Documentation. #Required; article description that is displayed in search results. 
author: mjordan343 #Required; your GitHub user alias, with correct capitalization.
ms.author: mjordan #Required; microsoft alias of author; optional team alias.
ms.service: halo-mcc #Required; service per approved list. slug assigned by ACOM.
ms.topic: quickstart #Required; leave this attribute/value as-is.
ms.date: 11/09/2022 #Required; mm/dd/yyyy format.
ms.custom: template-quickstart #Required; leave this attribute/value as-is.
---

# How-To - Fix "Creeping" Idle Animations

If your custom character has an incorrectly set up idle animation, they may slowly "slide" or "creep" from their starting locations.

The most likely source of this error is where idle animations are .JMA files that contain pelvic-animation.

All .JMA files have their pelvis motions translated into dx,dy data which is used by the physics system to move the actual unit per frame. This movement is not exact, and will cause the character to creep across the map in looping animations like the idle.

To prevent this, all Idle animations should be .JMM files, just like enter and exit animations. This will prevent the physics stuff from happening and keep your character locked in place while animating. This not only fixes the creeping problem, but also helps to lock the feet to the ground much better.

> [!NOTE]
> This should not occur often, as Tool treat all JMAs with the word ‘idle’ in them as if they were JMM files. 
