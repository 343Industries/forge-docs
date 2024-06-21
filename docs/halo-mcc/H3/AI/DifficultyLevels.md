---
title: Halo 3 AI Difficulty Levels #Required; page title is displayed in search results. Include the brand.
description: AI Difficulty Levels for Halo 3 Modding Documentation. #Required; article description that is displayed in search results. 
author: mjordan343 #Required; your GitHub user alias, with correct capitalization.
ms.author: mjordan #Required; microsoft alias of author; optional team alias.
ms.service: halo-mcc #Required; service per approved list. slug assigned by ACOM.
ms.topic: quickstart #Required; leave this attribute/value as-is.
ms.date: 03/14/2022 #Required; mm/dd/yyyy format.
ms.custom: template-quickstart #Required; leave this attribute/value as-is.
---

# Difficulty Levels

## **AI Parameters Modified by Difficulty**

There are a number of attributes in the game varied by difficulty. Most of these are related to AI, and happily most of them are also accessible in various tags. Here follows a list of the most common game variables modified by difficulty.

## **Character (*.character tag)**

### **Vitality**

AI characters may have varying levels of health and/or shield based on difficulty level.

### **Accuracy**

The most important thing about AI accuracy is how the firing parameters blend from inaccurate to accurate at different rates depending on difficulty level.

### **Upgrade chance**

Actors can upgrade to different variants, such as "major." The major characters have a different appearance (difference armor, mostly), and may have different behavior properties (more likely to charge, etc).

## **Scenario (*.scenario tag)**

### **Upgrade chance**

As above, but the default value can be overridden on a per squad basis.

### **Squad placement numbers**

Different numbers or placement of actors can happen depending on the difficulty level.

### **Task flags**

Tasks can be enabled and disabled depending on the difficulty level, meaning squads will occupy different areas, be more aggressive, timid, etc.

## **Projectiles (*.projectile tag)**

### **AI projectile velocity**

Velocity of projectiles fired by AI can be modified based on difficulty level.

## **Globals (globals.globals tag)**

There are a load of global modifiers, some of which aren't actually linked up in code, but here is an exhaustive list. There exist different (or sometimes the same) values for each of the following attributes, for each difficulty level.

### **Health**

- *enemy damage*— Enemy damage multiplier
- *enemy vitality*— Enemy maximum body vitality scale
- *enemy shield*— Enemy maximum shield vitality scale
- *enemy recharge*— Enemy shield recharge scale
- *friend damage*— Friend damage multiplier
- *friend vitality*— Friend maximum body vitality scale
- *friend shield*— Friend maximum shield vitality scale
- *friend recharge*— Friend shield recharge scale
- *infection forms*— Toughness of infection forms (may be negative)

### **Ranged Fire**

A lot of these values are the same across difficulty levels because the firing parameters moved from here into the character tag, as discussed above.

- *rate of fire*— Enemy rate of fire scale
- *projectile error*— Enemy projectile error scale, as a fraction of their base firing error
- *burst error*— Enemy burst error scale, reduces intra-burst shot distance
- *new target delay*— Enemy new-target delay scale factor
- *burst separation*— Delay time between bursts scale factor for enemies
- *target tracking*— Additional target tracking fraction for enemies
- *target leading*— Additional target leading fraction for enemies
- *overcharge chance*— Overcharge chance scale factor for enemies
- *special fire delay*— Delay between special-fire shots (overcharge, banshee bombs) scale factor for enemies
- *guidance vs. player*— Guidance velocity scale factor for all projectiles targeted on a player
- *melee delay base*— Delay period added to all melee attacks, even when berserk
- *melee delay scale*— Multiplier for all existing non-berserk melee delay times

### **Grenades**

grenade chance scale— Scale factor affecting the decisions to throw a grenade
grenade timer scale— Scale factor affecting the delay period between grenades thrown from the same encounter (lower is more often)

### **Placement**

major upgrade (normal)— Fraction of actors upgraded to their major variant
major upgrade (few)— Fraction of actors upgraded to their major variant when mix = normal
major upgrade (many)— Fraction of actors upgraded to their major variant when mix = many

### **Vehicles**

player vehicle ram chance— Chance of deciding to ram the player in a vehicle
