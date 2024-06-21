---
title: Halo 3 Weapon Home #Required; page title is displayed in search results. Include the brand.
description: Weapon Home for Halo 3 Modding Documentation. #Required; article description that is displayed in search results. 
author: mjordan343 #Required; your GitHub user alias, with correct capitalization.
ms.author: mjordan #Required; microsoft alias of author; optional team alias.
ms.service: halo-mcc #Required; service per approved list. slug assigned by ACOM.
ms.topic: quickstart #Required; leave this attribute/value as-is.
ms.date: 03/21/2022 #Required; mm/dd/yyyy format.
ms.custom: template-quickstart #Required; leave this attribute/value as-is.
---

# **Weapons**

## **Magazine Properties**

This article contains information about the properties of the magazines for each weapon.

- **Weapon** — Name of the weapon
- **Rounds Total Initial** — The initial amount of ammunition the player receives when the weapon is picked up
- **Rounds Total Maximum** — The total amount of ammunition of this type that a player can hold at one time (in addition to the rounds loaded in the weapon)
- **Rounds Loaded Maximum** — The total number of rounds that can be loaded into the weapon at one time
- **Rounds Reloaded** — The number of rounds placed in the weapon each time the player reloads

### **Weapon Properties**

|**Weapon**   |**Rounds Total Initial**   |**Rounds Total Maximum**| **Rounds Loaded Maximum**|**Rounds Reloaded**|
|----------|-----------|------------|------------|------------|
|**Excavator**          |10       |25        |5        |5        |
|**Magnum**             |32       |48        |8        |8        |
|**Needler**            |75       |105       |15       |15       |
|**Assault Rifle**      |96       |192       |32       |32       |
|**Battle Rifle**       |108      |144       |36       |36       |
|**Covenant Carbine**   |36       |90        |18       |24       |
|**Shotgun**            |18       |36        |6        |1        |
|**SMG**                |180      |240       |60       |60       |
|**Sniper Rifle**       |12       |24        |4        |4        |
|**Spike Rifle**        |180      |240       |60       |60       |
|**Flak Cannon**        |20       |30        |5        |5        |
|**Missile Launcher**   |2        |4         |1        |1        |
|**Rocket Launcher**    |4        |8         |2        |2        |
|**Spartan Laser**      |2        |2         |1        |1        |
|**Brute Shot**         |18       |24        |6        |6        |
|**Flamethrower**       |600      |1200      |100      |100      |

### **Power Magazine Properties**

|**Weapon**   |**Powerup Name**   |**Rounds**|
|----------|-----------|------------|
|**Excavator**          |NA                     |NA        |
|**Magnum**             |pistol_ammo            |24        |
|**Needler**            |needler_ammo           |60        |
|**Assault Rifle**      |NA                     |NA        |
|**Battle Rifle**       |br_ammo                |72        |
|**Covenant Carbine**   |NA                     |NA        |
|**Shotgun**            |shotgun_ammo           |18        |
|**SMG**                |smg_ammo               |120       |
|**Sniper Rifle**       |sniper_rifle_ammo      |12        |
|**Spike Rifle**        |smg_ammo               |120       |
|**Flak Cannon**        |NA                     |NA        |
|**Missile Launcher**   |rocket_launcher_ammo   |1         |
|**Rocket Launcher**    |rocket_launcher_ammo   |2         |
|**Spartan Laser**      |NA                     |NA        |
|**Brute Shot**         |NA                     |NA        |
|**Flamethrower**       |flamethrower_ammo      |100       |

## **Scaling**

Weapons are scaled in-game to accommodate both character size and game situation, so a weapon on the ground in multiplayer is scaled differently than when held in the hands of a Grunt.

This causes problems when authoring animation (both in-game and cinematic) as weapon size, weapon location, and hand placement are different in Maya than they will actually occur in-game. Some Maya files are currently being animated with arbitrary scaling on the weapon.

The solution to this problem is to add a scale factor to the next version of the weapons rig. This will automatically read the tag data and scale the weapon appropriately for the character. This will not adversely affect any existing animations, whether they have an arbitrary scaling to the weapons or not; however, there will be clean-up involved once weapons are their proper scale.

Weapon scaling info is held in **.weapon.item_scale_setting**

- single player ground
- multiplayer ground
- small unit armed
- small unit stowed
- medium unit armed
- medium unit stowed
- player unit armed
- player unit stowed
- large unit armed
- large unit stowed

Biped size info is held in **.biped.unit.item.item_owner_size**

- small, medium, player, or large biped

## **Additional Information**

- Scaling affects the render model only, so the physics model must be scaled large enough to accommodate all of the different scales
- Atlas uses a smaller player character than Halo3: changes in weapons scale will need to happen in tags
- Omaha will be using a smaller player character than Halo3
