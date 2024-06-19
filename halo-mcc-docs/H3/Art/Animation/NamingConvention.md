---
title: Halo 3 Animation Naming Conventions #Required; page title is displayed in search results. Include the brand.
description: Animation Naming Conventions for Halo 3 Modding Documentation. #Required; article description that is displayed in search results. 
author: mjordan343 #Required; your GitHub user alias, with correct capitalization.
ms.author: mjordan #Required; microsoft alias of author; optional team alias.
ms.service: halo-mcc #Required; service per approved list. slug assigned by ACOM.
ms.topic: quickstart #Required; leave this attribute/value as-is.
ms.date: 03/16/2022 #Required; mm/dd/yyyy format.
ms.custom: template-quickstart #Required; leave this attribute/value as-is.
---

# Naming Conventions

This article discusses the current name conventions for animation files.

- Animation Prefix: Every animation name begins with a mode, weapon class, and weapon type

    - Mode - combat, patrol, etc.

    - Weapon Class - rifle, pistol, etc.

    - Weapon Types are abbreviated versions of the weapon name

        - Examples: ar (assault rifle), ne (needler), pp (plasma pistol), etc.

    - Format: \<mode> \<weapon class> \<weapon type>

    - Note: The word 'any' can be used to replace a weapon class and/or weapon type, indicating the animation can be used for any weapon class and/or weapon type

        - Example: combat pistol any or combat any any

- After the prefix, the animation name contains either a State, Death and Damage, or a State and Transition

    - State - idle, move-left, move-front, etc.

        - Format: \<mode> \<weapon class> \<weapon type> \<state>

        - Example: combat rifle ar idle

    - Death and Damage is comprised of damage type, direction, and region

        - Damage Type - h_ping, s_ping, h_kill, s_kill

            - s (soft): refers to damage done by something like a pistol

            - h (heavy): refers to damage done by something like a rocket launcher

            - ping: refers to being hit

            - kill: refers to being killed

        - Direction refers to the direction from which the damage is being inflicted

            - left, right, front, back

        - Region refers to the region on the character that is being damaged

            - gut, chest, head, l_arm, l_hand, l_leg, l_foot, r_arm, r_hand, r_leg, r_foot

        - Format: \<mode> \<weapon class> \<weapon type> \<damage type> \<direction> \<region>

        - Example: combat rifle ar s_ping front gut

    - Transitions refer to animations in which the character is changing modes or states and is denoted by placing a '2' in the name, followed by the new mode and state.

        - Format: \<mode> \<weapon class> \<weapon type> \<state> 2 \<mode> \<state>

        - Example: combat rifle ar idle 2 combat patrol

- NOTE: With regards to files that contian 'any', some files may have omitted the word and left the space blank (eg. combat rifle idle). In such cases, 'any' is implied. Check with your lead for how they prefer to handle this scenario.

- File Extensions

    - .jma – extracts root motion in the XY plane, and zeros out any vertical motion. No orientation

    - .jmm- extracts no movement

    - .jmt – extracts root motion in the XY plane and yaw orientation (used for turns, for example)

    - .jmo – no movement (these are overlays)

    - .jmr – no movement (replacement animation in object space)

    - .jmrx – no movement (replacement animation in local space)

    - .jmz – extracts FULL XYZ motion and yaw orientation (could not find examples of this)

    - .jmw – animation in world space (used for large objects that cross large areas of a level)
