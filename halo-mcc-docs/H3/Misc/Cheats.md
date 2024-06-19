---
title: Halo 3 Misc Cheats #Required; page title is displayed in search results. Include the brand.
description: Misc Cheats for Halo 3 Modding Documentation. #Required; article description that is displayed in search results. 
author: mjordan343 #Required; your GitHub user alias, with correct capitalization.
ms.author: mjordan #Required; microsoft alias of author; optional team alias.
ms.service: halo-mcc #Required; service per approved list. slug assigned by ACOM.
ms.topic: quickstart #Required; leave this attribute/value as-is.
ms.date: 03/17/2022 #Required; mm/dd/yyyy format.
ms.custom: template-quickstart #Required; leave this attribute/value as-is.
---

# Cheats.txt

Add the following command to your init.txt file: **cheat_controller 1** (or whichever controller port you use).

Once that line is added to your init.txt, you can use hs-command shortcuts specified in your cheats.txt file.

Each button has a corresponding line, what appears before the r;; becomes the command. If cheat_controller is on, you can hold down the **back** button and hit any other button to activate that button's hs command.

In addition to the obvious things like game_speed 0 or error_geometry_hide_all, this can be useful for things like toggling oft-used commands such as:

```
(set debug_structure_automatic (not debug_structure_automatic)); x-button
```

The order of the lines is intentional and immutable— you can't assign commands to the start or back button.

A Sample Cheats.txt file:

```
; left trigger
; right trigger
; dpad-up
; dpad-down
; dpad-left
; dpad-right
; start (NOT USABLE)
; back (NOT USABLE)
; left-thumb
; right-thumb
game_speed 1; a-button
game_speed 4; b-button
(set debug_structure_automatic (not debug_structure_automatic)); x-button
; y-button
; left bumper
; right bumper
```
