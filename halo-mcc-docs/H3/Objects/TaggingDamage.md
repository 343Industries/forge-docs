---
title: Halo 3 Objects Tagging Damage Sections and States #Required; page title is displayed in search results. Include the brand.
description: Objects Tagging Damage Sections and States for Halo 3 Modding Documentation. #Required; article description that is displayed in search results. 
author: mjordan343 #Required; your GitHub user alias, with correct capitalization.
ms.author: mjordan #Required; microsoft alias of author; optional team alias.
ms.service: halo-mcc #Required; service per approved list. slug assigned by ACOM.
ms.topic: quickstart #Required; leave this attribute/value as-is.
ms.date: 03/17/2022 #Required; mm/dd/yyyy format.
ms.custom: template-quickstart #Required; leave this attribute/value as-is.
---

# Tagging Damage Sections and States

This article covers tags for an object with damage sections and states.

## **New Damage Info Tag Block**

You need to have an instance of the global_damage_info_block activated before you can access any of the damage options for your model. It is also important to note that any damage you set up is global to the model. You can't set up a specific damage model for one variant and not have it apply to other variants (for example, all marines share the same damage sections, health, etc).

- **Global indirect material name**: The material type (one of the materials for this specific model - found above in the Materials block) that takes all indirect damage done to the model.

- **Indirect damage section**: The damage section (selected from a drop-down list) that will absorb indirect damage (melee, explosion, etc) for the model.

- **Collision damage reporting type**: For special cases such as the warthog, where the object can do damage that we want attributed to something else. So, when the warthog runs someone over, this is how we attribute the kill to the driver (instead of the hog).

- **Response damage reporting type**: For special cases where the instant response of an object kills a person. For example, when the ghost explodes, or a fusion coil explodes, and kills someone - this property specifies where the damage came from.

- **Body**

    - maximum vitality - The total health (vitality) of the model. For an object like the masterchief, this value would be relatively low (45), because he has low health, but higher shields (maximum shield vitality).

    - minimum stun damage - The minimum amount of damage it takes to stun the object's health. This amount of damage prevents the health from recharging.

    - stun time - The amount of time that the object's health stays stunned before recharging. When this amount of time has expired, the object's health will begin to recharge (unless the minimum stun damage amount is exceeded during that time - at which point the stun timer is reset).

    - recharge time - The amount of time it takes the object to restore itself to full health.

    - recharge fraction - The maximum amount of health that the object will be allowed to recharge. The values go from 0 - 1, so entering .5 would only allow the object to recharge to half of its maximum health.

- **Shield**

    - Shield damaged first person shader - The shader that will be displayed when damage is taken to the shield in first person.

    - Shield damaged shader - The shader that will be displayed when damage is taken to the shield in third person.

    - maximum shield vitality - The total health/strength of the object's shield. For the Master Chief, this number is set to 70.

    - global shield material name - The material type for the shield (right-click on the words "global shield material name" to select the material type).

    - minimum stun damage - The minimum amount of damage that is required to stun the shield's health (and prevent it from recharging).

    - stun time - The amount of time that will elapse before the shield will begin to recharge after being damaged or stunned.

    - recharge time - The total amount of time it takes for the shield to recharge.

    - shield damaged threshold - The amount of damage it takes to do damage to the shield.

    - shield damaged effect - The effect that will play when the shield is damaged.

    - shield depleted effect - The effect that will play when the shield is completely depleted (destroyed).

    - shield recharging effect - The effect that will play when the shield is in the process of recharging.

## **Damage Sections**

Any area of your model that you wish to show damage needs a damage section set up for it.

- **name**: A unique name given to each damage section

- **flags**: Options you can set for the selected damage section

- **vitality percentage**: This damage section's percentage of the overall health/vitality of the object.

## **Instant Response Tag Block**

The *Instant Response* section of the .model tag configures the response that will take place for each damage section.

- **response type**: A drop-down list with three options: receives all damage, receives area effect damage, and receives local damage . If receives local damage is selected, the selected damage section will not receive area of effect or indirect (melee, grenade, etc) damage.

- **constraint damage type**: A constraint is a piece of the model that holds two pieces together (think of a hinge on a door). If you set up a constraint group (by naming it below under Constraint Group Name, you can use this field to set the type of damage that is done to the constraint - either loosening or destroying. Loosening damage activates a constraint, while destroying damage sets the pieces free (separates them).

- **flags**: Set any of these for special ways the damage section will respond to damage.

- **damage threshold**: The point the damage section's health needs to be at before the instant response will fire. 1 is the object at full health, 0 is the object destroyed.

- **transition effect**: The effect that plays while the object is transitioning from one state to another.

- **transition damage effect**: The effect that plays while the object is transitioning from an undamaged to a damaged state.

- **region**: The region of the object that displays the instant response (the region where the damage section is to be attached). This is a named region that should have been set up in 3DS Max and then defined earlier in the tag. For information on how to set up variants, regions, permutations, and states, check out the article here.

- **new state**: A drop-down list of new states for the region of the object to enter when the instant response fires. This should coincide with a state you have set up for the Region you entered under Region. For information on how to set up variants, regions, permutations, and states, check out the article here.

- **effect marker name**: This is the name of a marker you should have specified in 3DS Max when creating the model. The marker is the area where the transition effect will render on the model.

- **damage effect marker name**: This is the name of a marker you should have specified in 3DS Max when creating the model. The marker is the area where the damage effect will render on the model.

- **Response Delay**

    - response delay - The number of seconds until the "instant" response fires.

    - delay effect - The effect that will play during the delay time before the instant response fires.

    - delay effect marker name - The marker (set up in 3DS Max) which specifies where you want the delay effect to render on the model.

- **Constraint Destruction**

    - constraint/group name - The name of a constraint group that you want this particular instant response/ damage section to belong to. See the entry on Constraint Damage Type above for more info.

- **seat ejection**

    - ejecting seat label - If the damage section is the seat of a vehicle or turret, you can have the player ejected from it when it is destroyed. Enter the name of the seat that you want to eject the player from here. For example, if you're setting up the damage section for the driver's side of the warthog, you would enter "warthog_d."

- **skip fraction**

    - skip fraction - If you want this response to fire sometimes, but not always, you can enter a percentage of the time you'd like it to fire.
Destroyed Child object marker name

    - Destroyed child object marker name - When the response fires, any child objects created at the supplied marker name (set up in 3DS Max) will be destroyed.

- **total damage threshold**

    - total damage threshold - The threshold at which damage will be done to the damage section. It defaults to 0, which means any damage done will affect the overall health (vitality) of the damge section.
