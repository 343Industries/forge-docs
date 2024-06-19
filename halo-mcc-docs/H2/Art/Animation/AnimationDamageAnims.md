---
title: Halo 2 Animation Damage Animations #Required; page title is displayed in search results. Include the brand.
description: Damage Animations for Halo 2 Animations in MCC Modding Documentation. #Required; article description that is displayed in search results. 
author: mjordan343 #Required; your GitHub user alias, with correct capitalization.
ms.author: mjordan #Required; microsoft alias of author; optional team alias.
ms.service: halo-mcc #Required; service per approved list. slug assigned by ACOM.
ms.topic: quickstart #Required; leave this attribute/value as-is.
ms.date: 11/09/2022 #Required; mm/dd/yyyy format.
ms.custom: template-quickstart #Required; leave this attribute/value as-is.
---

# Animations - Damage Animations

Damage animations are identified by **type**, **direction**, and **region**. So, if you made every permutation of damage, region and type you’d have 176 damage animations per character.

## Damage Types

There are four kinds of damage animations.

- **soft_ping** - overlay (jmo) which shows impact from light damage

- **hard_ping** - state animation (jma) which shows the impact of heavy damage (usually a stagger or side-step)

- **soft_kill** - state_animation (jma) which shows death from light damage

- **hard_kill** - state_animation (jma) which shows death from heavy damage

## Damage Directions

- **_animation_damage_direction_front**

- **_animation_damage_direction_left**

- **_animation_damage_direction_right**

- **_animation_damage_direction_back**

## Damage Regions

- **_damage_part_gut,**

- **_damage_part_chest,**

- **_damage_part_head,**

- **_damage_part_l-arm,**

- **_damage_part_l-hand,**

- **_damage_part_l-leg,**

- **_damage_part_l-foot,**

- **_damage_part_r-arm,**

- **_damage_part_r-hand,**

- **_damage_part_r-leg,**

- **_damage_part_r-foot,**

## Damage Animation Inheritence

Since we can’t obviously author that many individual animations, there is an inheritance scheme in place which lets the engine find the closest possible animation to play. It uses a built-in search order to find an animation it can play.

The searching works like this:

Suppose an [h_ping, back, right_shoulder] animation is desired, but one does not exist. The engine will first determine if any h-pings from the back exist. If there are no other h_pings available from the back, the other directions are searched until a set of h_pings is found. The search order is:

|Current Direction | Next Direction to Try|
|---|---|
|_animation_damage_direction_front| _animation_damage_direction_left<br />_animation_damage_direction_back<br />_animation_damage_direction_right|
|_animation_damage_direction_right|_animation_damage_direction_front|

Once a set of hard pings is found, the damage regions are searched to find the closest match. The region order is:

|Current Region|Next Region to Try|
|--|--|
|_damage_part_gut|_damage_part_head|
|_damage_part_chest|_damage_part_gut|
|_damage_part_head|_damage_part_chest|
|_damage_part_l-arm|_damage_part_chest|
|_damage_part_l-hand|_damage_part_l-arm|
|_damage_part_l-leg|_damage_part_gut|
|_damage_part_l-foot|_damage_part_l-leg|
|_damage_part_r-arm|_damage_part_chest|
|_damage_part_r-hand|_damage_part_r-arm|
|_damage_part_r-leg|_damage_part_gut|
|_damage_part_r-foot|_damage_part_r-leg|

## Importing Damage Animations

Currently, to import a damage animation through Tool, it must be named in the format

\**[type][direction][region]** as in:

“h_ping front gut.jma”

For this system to work, at least one gut, chest or head animation must be supplied for each damage type.

For example, you could supply these four animations and have a working system:

```
“s_ping front gut.jma”
“h_ping back chest.jma”
“s_kill front gut.jma”
“h_kill back head.jma”
```

...because these four animations provide at least one head, chest or gut animation for each of the four damage types. The directions used don’t matter in this minimal case.
