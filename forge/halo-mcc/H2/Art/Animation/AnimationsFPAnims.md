---
title: Halo 2 Animation First Person Animations #Required; page title is displayed in search results. Include the brand.
description: First Person Animations for Halo 2 Animations in MCC Modding Documentation. #Required; article description that is displayed in search results. 
author: mjordan343 #Required; your GitHub user alias, with correct capitalization.
ms.author: mjordan #Required; microsoft alias of author; optional team alias.
ms.service: halo-mcc #Required; service per approved list. slug assigned by ACOM.
ms.topic: quickstart #Required; leave this attribute/value as-is.
ms.date: 11/09/2022 #Required; mm/dd/yyyy format.
ms.custom: template-quickstart #Required; leave this attribute/value as-is.
---

# Animations - First Person Animations

Below is an outline of the files that comprise the Halo 2 first person animation system.

## BASIC ANIMATIONS

The following files is the base file list you need for a standard first person weapon animation set. They should reside in the weapon’s “fp” animation folder.

For instance you would find the SMG first person animations here:  *\data\objects\weapons\rifle\smg\fp_smg\animations*

We recommend creating a “working” directory in the “animations” folder where you can store your DCC files and reference.

- **first-person firing.jmo**

- **first-person idle.jmm**

- **first-person melee-1sthit.jmm**

- **first-person melee-1sthit2i.jmm**

- **first-person melee-2ndhit.jmm**

- **first-person melee-2ndhit2i.jmm**

- **first-person melee-3rdhit.jmm**

- **first-person moving.jmo**

- **first-person overlays.jmo**

- **first-person posing.jmm**

- **first-person put-away.jmm**

- **first-person ready.jmm**

- **first-person reload-full.jmm**

- **first-person reload-empty.jmm**

- **first-person throw-grenade.jmm**

- **rename.txt**

### FIRST PERSON ANIMATION BREAKDOWN

*The following text describe the purpose for each animation file needed for a basic first person animation graph.*

**first-person firing.jmo**

- firing animation overlay

- shares timing with the 3rd person firing animation for that weapon

**first-person idle.jmm**

- basic breath idle

- should have at least one other variation

**first-person melee-1sthit.jmm**

- melee attack

- 1st hit of melee combo

- roughly timed the same as hit #2

- animated from idle pose to end position of attack #1

- hold in end position

**first-person melee-1sthit2i.jmm**

- return to idle from melee attack #1

- quick return to idle

- used if combo is interrupted or discontinued

**first-person melee-2ndhit.jmm**

- melee attack

- 2nd hit of melee combo

- roughly timed the same as hit #1

- animated from end position of attack #1 to end position of attack #2

- hold in end position

**first-person melee-2ndhit2i.jmm**

- return to idle from melee attack #2

- quick return to idle

- used if combo is interrupted or discontinued

**first-person melee-3rdhit.jmm**

- melee attack

- 3rd hit of melee combo

- biggest attack of the combo

- animated from end position of attack #2 to idle

- returns to idle

**first-person moving.jmo**

- simulates the character’s upper body movement

- gun and arms sway from side to side to simulate footsteps being taken

**first-person overlays.jmo**

- overlays used to simulate delay/overlapping action

- eg: a character strafes left and the gun/arms delay then move left with the character

- 0-9 [10 frames]

|Frame|Name|Pose Reference|
|--|--|--|
|0|All-Base|- base pose holding gun|
|1|Arms-Back|- arms move back|
|2|Arms-Front|- arms move forward|
|3|Arms-Left|- arms move left|
|4|Arms-Right|- arms move right|
|5|All-Base|- base pose holding gun|
|6|Gun-Left|- gun pitches left|
|7|Gun-Right|- gun pitches right|
|8|Gun-Up|- gun pitches up|
|9|Gun-Down|- gun pitches down (helpful to slide the rig back a little on this one)|

**first-person posing.jmm**

- flavour animation / flavour idle

- used when character is idle for a longer period of time

- eg: character fidgeting with gun

- animated from idle pose to idle pose

**first-person put-away.jmm**

- used to stow weapon

- weapon completely leaves screen

- animated from idle pose to off screen

**first-person ready.jmm**

- used to bring weapon to idle pose

- weapon comes from off of screen

- animated from off of screen to idle pose

**first-person reload-full.jmm**

- reload weapon

- changing magazines/clips/etc

- different for each weapon [eg: shotgun]

**first-person reload-empty.jmm**

- reload weapon

- reused from “first-person reload-full” animation in the rename.txt

**first-person throw-grenade.jmm**

- throw grenade

- left handed throw

- do not export with a grenade in the scene

**rename.txt**

- a text file

- intended to list reused animations

### HELPFUL HINTS
> [!NOTE]
> export is basically the same method, with the graph living under the weapons’ tag directory

> [!NOTE]
> start with a static animation as an idle to get the pose down on screen before moving on to creating the rest of the moveset

> [!NOTE]
> you can reuse a lot by referring to existing animations as a base to start from

> [!NOTE]
>the slightest movement can make or break a first person animation, so be aware of what you are doing and refer to the animations in the engine for the final look
