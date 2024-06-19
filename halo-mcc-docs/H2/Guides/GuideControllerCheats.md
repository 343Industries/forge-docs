---
title: Halo 2 Guides Controller Cheats #Required; page title is displayed in search results. Include the brand.
description: Controller Cheats for Halo 2 Guides in MCC Modding Documentation. #Required; article description that is displayed in search results. 
author: mjordan343 #Required; your GitHub user alias, with correct capitalization.
ms.author: mjordan #Required; microsoft alias of author; optional team alias.
ms.service: halo-mcc #Required; service per approved list. slug assigned by ACOM.
ms.topic: quickstart #Required; leave this attribute/value as-is.
ms.date: 11/09/2022 #Required; mm/dd/yyyy format.
ms.custom: template-quickstart #Required; leave this attribute/value as-is.
---

# How-To - Set Up Controller Cheats

Any console command can be set in your **init.txt** file. Similarly you can set up a **cheats.txt** file that allows you to invoke console commands from the game controller.

> [!NOTE]
> Create cheats.txt in your H2EK root directory.

In your **init.txt**, add a line of text that says **cheat_controller on**

To activate your new commands, press the BACK button and then the corresponding button to the command you wish to activate.

> [!NOTE]
> THIS WILL ONLY WORK WHILE YOU ARE IN CONTROL OF THE CHARACTER. you won't be able to invoke commands while in the flying camera mode.

## FORMAT

### Format for boolean commands (ones that accept true,false or on,off or 1,0) is:

```
set [command] (not [command])
```

- example: set debug_objects (not debug_objects)

### Format for cheat commands is simply:

```
[command]
```

- example: cheat_teleport_to_camera

### Format for integer commands is a bit trickier. These are commands that require a numerical value (like pad3):

```
set [command] (- 1 [command])
```

- example: set pad3 (- 1 pad3)

### Format for unmapped keys:

```
empty (empty)
```

## ORDER OF COMMANDS

The order of commands is assumed - ie, the first line is always mapped to the "A" button, the second line to the "B," etc.

The order of commands is:

- ine 01 = A button

- line 02 = B button

- line 03 = X button

- line 04 = Y button

- line 05 = Black button

- line 06 = White button

- line 07 = Left Trigger

- line 08 = Right Trigger

- line 09 = D-Pad Up

- line 10 = D-Pad Down

- line 11 = D-Pad Left

- line 12 = D-Pad Right

## ADDING COMMENTS

You can add comments to any line by seperating it with a semicolon.

example: set debug_objects (not debug_objects); A button

The words "A button" don't actually do anything - the code stops reading the line at the semicolon (;). It's just a good way to show someone looking at the file what this line of code is doing.

## SAMPLE CHEATS.TXT FILE

- set debug_objects (not debug_objects); A button

- set ssc_shadow (not ssc_shadow); B button

- set render_model_markers (not render_model_markers); X button

- set render_model_vertex_counts (not render_model_vertex_counts); Y button

- set debug_render_freeze (not debug_render_freeze); Black button

- cheat_teleport_to_camera; White button

- set ssc_bump_mode_debug (not ssc_bump_mode_debug); Left Trigger

- set rasterizer_bump_mapping (not rasterizer_bump_mapping); Right Trigger

- empty (empty); D-Pad Up

- empty (empty); D-Pad Down

- empty (empty); D-Pad Left

- empty (empty); D-Pad Right
