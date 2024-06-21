---
title: Halo 3 Objects Halo Script Damage Object #Required; page title is displayed in search results. Include the brand.
description: Objects Halo Script Damage Object for Halo 3 Modding Documentation. #Required; article description that is displayed in search results. 
author: mjordan343 #Required; your GitHub user alias, with correct capitalization.
ms.author: mjordan #Required; microsoft alias of author; optional team alias.
ms.service: halo-mcc #Required; service per approved list. slug assigned by ACOM.
ms.topic: quickstart #Required; leave this attribute/value as-is.
ms.date: 03/17/2022 #Required; mm/dd/yyyy format.
ms.custom: template-quickstart #Required; leave this attribute/value as-is.
---

# Halo Script Damage_Object

damage_object is a Halo Script command that allows you to apply specific amount of damage to a named object in a scenario.

## **Use**

damage_object is executed from a command line:

damage_object \<object name> \<material name> \<damage amount>

- object name— Named object in scene

- material name— Collision material of named object

- damage amount— Deducted from object's vitality

## **Example**

- damage_object hog hull 100

This command will do 100 damage to the material hull on the warthog named hog on the active map.

## **Tag Info**

There is a hs_damage.damage_effect tag that is linked to the globals.global (see Figure 1).

![View of the falling damage tag with the h s damage section highlighted by a box.](./media/H3_Objects_DamageTag.png)

Figure 1 - hs damage tag.
