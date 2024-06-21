---
title: Halo 3 Debug Profile Settings Commands #Required; page title is displayed in search results. Include the brand.
description: Debug Profile Settings Commands for Halo 3 Modding Documentation. #Required; article description that is displayed in search results. 
author: mjordan343 #Required; your GitHub user alias, with correct capitalization.
ms.author: mjordan #Required; microsoft alias of author; optional team alias.
ms.service: halo-mcc #Required; service per approved list. slug assigned by ACOM.
ms.topic: quickstart #Required; leave this attribute/value as-is.
ms.date: 03/16/2022 #Required; mm/dd/yyyy format.
ms.custom: template-quickstart #Required; leave this attribute/value as-is.
---

# Profile Settings Commands

The following debug commands can be used to modify player profile settings in all but the shipping build of the game and they will also save profile as they are made. You can use these commands to change your settings but they won't be saved to your profile (and you'll then have to enter these commands every time you launch the game).

These commands will no longer work from your init.txt file because there is a delay between the time init.txt is read and when the signed-in users are detected by the game.

- **controller_set_look_inverted** [controller] [true|false]— Sets look inversion for specified controller, where controller is one of [controller1, controller2, controller3, controller4]

- **controller_set_vibration_enabled** [controller] [true|false]— Sets vibration for specified controller, where controller is one of [controller1, controller2, controller3, controller4]

- **controller_set_flight_stick_aircraft_controls** [controller] [true|false]— Sets airrcraft flight stick controls for specified controller, where controller is one of [controller1, controller2, controller3, controller4]

- **controller_set_auto_center_look** [controller] [true|false]— Sets auto center look for specified controller, where controller is one of [controller1, controller2, controller3, controller4]

- **controller_set_button_preset** [controller] [preset]— Sets button preset for specified controller, where controller is one of [controller1, controller2, controller3, controller4] and preset is one of [standard south_paw boxer green_thumb]

- **controller_set_joystick_preset** [controller] [preset]— Sets joystick preset for specified controller, where controller is one of [controller1, controller2, controller3, controller4] and preset is one of [standard south_paw legacy legacy_south_paw]

- **controller_set_look_sensitivity** [controller] [value]— Sets look sensitivity for specified controller, where controller is one of [controller1, controller2, controller3, controller4] and value is some number in the range of [0,9] inclusive

- **controller_unlock_single_player_levels** [controller]— Unlocks all single player levels for specified controller, where controller is one of [controller1, controller2, controller3, controller4]

- **controller_set_primary_change_color** [controller] [color]— Sets primary change color for specified controller, where controller is one of [controller1, controller2, controller3, controller4] and color is one of [white steel red orange gold olive green sage cyan teal cobalt blue violet purple pink crimson brown tan]

- **controller_set_secondary_change_color** [controller] [color]— Sets secondary change color for specified controller, where controller is one of [controller1, controller2, controller3, controller4] and color is one of [white steel red orange gold olive green sage cyan teal cobalt blue violet purple pink crimson brown tan]

- **controller_set_tertiary_change_color** [controller] [color]— Sets tertiary color for specified controller, where controller is one of [controller1, controller2, controller3, controller4] and color is one of [white steel red orange gold olive green sage cyan teal cobalt blue violet purple pink crimson brown tan]

- **controller_set_quaternary_change_color** [controller] [color]— Sets quaternary change color for specified controller, where controller is one of [controller1, controller2, controller3, controller4] and color is one of [white steel red orange gold olive green sage cyan teal cobalt blue violet purple pink crimson brown tan]

- **controller_set_player_character_type** [controller] [character]— Sets player character type for specified controller, where controller is one of [controller1, controller2, controller3, controller4] and character is one of [mp_masterchief mp_elite]

- **controller_set_emblem_info** [controller] [foreground_emblem] [background_emblem]— sets emblem for specified controller, where controller is one of [controller1, controller2, controller3, controller4] and foreground_emblem is some number in the range of [0, 31] inclusive and background_emblem is some number in the range of [0, 31] inclusive

- **controller_set_voice_output_setting** [controller] [setting]— Sets voice output setting for specified controller, where controller is one of [controller1, controller2, controller3, controller4] and setting is one of [default speakers headset none]

- **controller_set_voice_mask** [controller] [voice_mask]— Sets voice mask for specified controller, where controller is one of [controller1, controller2, controller3, controller4] and voice_mask is one of [none anonymous]

- **controller_set_subtitle_setting** [controller] [setting]— Sets subtitle setting for specified controller, where controller is one of [controller1, controller2, controller3, controller4] and setting is one of [automatic enabled disabled] 
