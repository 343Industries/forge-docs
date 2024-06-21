---
title: Halo 2 Device Machines #Required; page title is displayed in search results. Include the brand.
description: Device Machines for Halo 2 Devices in MCC Modding Documentation. #Required; article description that is displayed in search results. 
author: mjordan343 #Required; your GitHub user alias, with correct capitalization.
ms.author: mjordan #Required; microsoft alias of author; optional team alias.
ms.service: halo-mcc #Required; service per approved list. slug assigned by ACOM.
ms.topic: quickstart #Required; leave this attribute/value as-is.
ms.date: 11/10/2022 #Required; mm/dd/yyyy format.
ms.custom: template-quickstart #Required; leave this attribute/value as-is.
---

# Device Machines

**Device Machines** are motorized, animated, objects placed in the game that either react to the player, or that the player can interact with. Below, you can find detailed information on all of the properties of device machines, as well as step by step setup instructions to get you going quickly.

## THE BASICS

- The animation file for your device machine needs to be exported as a **.jmo**. None of the other animation formats will work.
- When creating the animation for your device machine, do not leave any static frames at the beginning or end! This causes problems later when adding sound effects.
- If you want the object's bounding sphere to move with it when it animates in game (and thus retain physics and collision), you need to animate the root node for the object (not any of the lower frame nodes).
- When you export your animation, it needs to be named **device position.jmo**. If the file is not named this way, it will not function!
For position animations (which are what most device machine animations will be), our engine animates frame #0, but drops the last frame of the animation. For overlay animations, our engine doesn't play frame #0.

## STEP-BY-STEP SETUP

1. Create and import the geometry and animation files for your device machine. You will need render, collision, physics, and animations. Also, make sure you name the animation file "**device position.jmo.**" If you don't, the animation will not play.
    - When creating the animation for your device machine, do not leave groups of static frames at the beginning or end! This causes problems later when adding sound effects.
1. Create any .shader tags for the materials you assigned to your model in the 3D Program of your choice. Re-import.
1. Create a new .model tag. Link all of the other tags for your object to your new .model tag. Make sure you set the material types in your .model tag as well. Save it.
1. In the *Model* tag block of the .model tag, click the Browse (...) button next to the **Animation** text box and link the .model_animation_graph tag for your device machine to your .model tag.
1. Create a new .device_machine tag. Save it to a location of your choosing.
1. Link your .device_machine tag to the .model tag for your object. This field is in the topmost section of your .device_machine tag (labeled *Model*) - simply click on the ... button and browse to the .model tag for your object.
1. Scroll down to the bottom of the .device_machine tag to a block labeled *Device*. There are many different properties to check depending on the type of device machine you're trying to build (see below for detail on each property). To get your device machine up and running, the most important field to enter a number in is **Position Transition Time**. This is the amount of time it will take your device machine to go from closed to open (or off to on). Enter a number (in seconds) here now.
1. Next, find the **Automatic Activation Radius** field. This is the distance (in world units) the player needs to be from the object for it to activate automatically. Think of this in the context of an automatic door - when the player gets close, it opens. Enter a number here now. If you don't want your device to activate automatically, but want to set up a button press or other event which will activate it, check out the [Device Controls](../Devices/DeviceControls.md) article. Also, if your device is a "door," and you don't want it to activate automatically, you'll need to check the "Does not operate automatically" flag in Sapien (See below for more info).
1. Now move down to the *Machines* tag block. For **Type**, select *Gear*. Even if you want to make a door, gear is the most useful for initial debugging of your machine because the *gear* type is always on - so you'll instantly know if your object is working. You can go back and reset the type to *door* at any time once you know the device itself (and particularly its animation) works.
1. Open your scenario in Sapien.
1. Add your new device machine to the Palette, and then place one (by right-clicking on the game window) in the scenario.
1. Select the device you just placed (by clicking on its name in the Hierarchy View) and then select the type for it in the Properties Palette. You can find more information on properties set in Sapien in the Properties Set in Sapien section below.
1. That should be everything you need to set up your basic device machine. Save. If you already had your map running, you will need to reset the map before the device machine will begin to function. See below for more details on individual properties or flags you can set for your device.

## DEVICE TAG BLOCK

- **Flags**
    - Position Loops: This flag allows the device to change its position to any value at will, but it will always choose the shortest circular path. When the position goes below zero or above one, it wraps around. For example, if you were at position 0.2 and wanted to to to 0.9, the shortest circular distance is to run backwards (.2, .1, 0, .9). This is different from the Gear machine type in that the Gear type always loops continuously in the direction of the animation you set up (it never goes backwards).
    - Allow Interpolation: Allows the device machine to interpolate animations (they don't do this automatically). Using this flag, you can set a series of positions (without animating them in the 3d Program of your choice) and the game engine will animate the device's movements. However, this will cause the animation to lag behind the device's actual position. For an example, think of the Scarab in Halo 2 (which didn't have animations, but was interpolated by the game engine). You should not use this for for things like doors or elevators.
- **Power Transition Time** - When a power group is set up for the device (with other devices, or with a device control), this controls the amount of time it takes for the device to go from its off state to its on state.
- **Power Acceleration Time** - The amount of time it takes for the speed of the power transition to accelerate from 0 to 1 - or decelerate to 0 - when powering up.
- **Position Transition Time** - The amount of time (in seconds) it takes for the device machine to go from a completely closed (off) to a completely open (on) state.
- **Position Acceleration Time** - The amount of time (in seconds) it takes for the device machine to reach it's top speed (or slow down to zero if it is in 'closing' mode).
- **Depowered Position Transition Time** - The time it takes for the device to enter its depowered state (from a powered state). This only matters when the device is part of a power group (set up in Sapien) with other devices or device controls.
- **Depowered Position Acceleration Time** - The amount of time it takes for the device to accelerate from stopped to top speed on its way into the depowered state. This only matters when the device is part of a power group (set up in Sapien) with other devices or device controls.
- **Lightmap Flags**
    - Don't use in Lightmap: When this flag is checked, the device will not be considered when lightmaps are run. So, for example, if the device is covering an area (or blocking light), the lightmapper will run as if the device did not exist and the area will be lit by lights that might otherwise be blocked.
    - Don't use in Lightprobe: When this flag is checked, the lightprobes will not consider the way a device machine is affecting lighting in the area and, therefore, how the player is lit when standing on/around/near the device.
- **Open (up)** - The effect that is played while the device is opening (or moving up in the case of a lift).
- **Close (down)** - The effect that is played while the device is closing (or moving down in the case of a lift).
- **Opened** - The effect that plays while the device is opened/on.
- **Closed** - The effect that plays while the device is closed/off.
- **Depowered** - The effect that plays when power to the device is shut off.
- **Repowered** - The effect that plays when power to the device is turned on.
- **Delay Time** - The time (in seconds) between when the device is activated and when it actually begins to move.
- **Delay Effect** - The effect that plays during the time between when the device has been activated and when it actually begins to move.
- **Automatic Activation Radius** - The size of the radius (in world units) within which the player needs to stand to activate the device.

## MACHINE TAG BLOCK

- **Type** - Select the type of device machine you want to create from the drop down list:
    - Door: The device will behave as a door - opening and closing depending on the settings you choose. Doors are set to open automatically when the player comes within their activation radius unless they are part of a position group with a device control(and you set the "Does Not Operate Automatically" flag in Sapien).
    - Platform: A platform behaves the same as a door device except that it will not activate automatically. For platforms to function, they need to be part of a position group with a device control (a button, for example).
    - Gear: The device will work like a gear - constantly performing it's animations in a single direction - never going backwards and only having the ability (via setup in the tag) to speed up or slow down. In this state, the player doesn't need to turn it on or off, or activate it in any way.
- **Flags**
    - Pathfinding Obstacle: Checking this flag prevents AI from pathing onto the device - they will consider it an obstacle and path around it.
    - ... But not when Open: Checking this flag in conjunction with Pathfinding Obstacle will allow AI to path onto or through the device (or space created by the device) when it is open (on) but not when it is closed (off).
    - Elevator: Allows the device to stop and start at multiple points along the way from completely closed to completely open. For example, the silo elevator in 04b_floodlab (Halo 2). The stopping and starting can be accomplished using scripting (see Tyson or Rob for more info on how to do this). For the elevator to work, you also need to enter an Elevator Node below (in the Machine properties).
- **Door Open Time** - The amount of time (in seconds) a door will remain open before closing (unless it has an automatic activation radius which the player is standing within, or if the door is controlled by a device control - in either of those cases, this property is ignored).
- **Door Occlusion Bounds** - This flag activates and de-activates visibility portals within the distance of the door that you specify (in world units). This is used so that things don't render when the door is closed (or render if we need them to so that they don't "pop" in when the door is opened by the player).
- **Collision Response** - How the device responds when it collides with another object.
    - Pause Until Crushed: The device will continue to its normal open or closed position, crushing anything in its path.
    - Reverse Directions: The device will stop and reverse directions when it collides with an object.
- **Elevator Node** - Used in combination with the Elevator flag (see above) to create device machines which can stop at various points between their fully open or fully closed states. NOTE: Greg says this option appears to be disabled in code (so elevators may not work at the moment).
- **Pathfinding Policy** - Sets the way AI will path on, through, or around the device.
    - Discs: pathfinding for this device will be generated using a disc-type style.
    - Sectors: pathfinding for this device will be generated using sectors.
    - Cut_Out: pathfinding for this device will be generated using cut outs.
    - None: no set pathfinding policy. The engine will decide.

## PROPERTIES SET IN SAPIEN

The special properties for Device Machines in Sapien are found in the Properties Palette (after you've placed your device machine in the game window).

![View of the Device Machine Properties in Sapien.](./media/H2_Devices_DeviceMachineProperties.jpg)

Fig 1 - Device Machine properties set in Sapien

- **Power Group** - Power groups are set up to link device machines and device controls together when the machine has a depowered and powered state.
- **Position Group** - Position groups are links between device controls and device machines. This group controls the animation/movement of the machine. If you want to set up any device machine which is controlled by a button (or any other device control), you must group it in a position group with a device control.
- **Flags**
    - Initially Open (1,0): The device will appear in it's open/on state when the game/level starts.
    - Initially Off (0,0): The device will be in it's depowered/deactivated state when the game/level starts.
    - Can Change Only Once: allows the device machine to change position (open or close, for example) only one time. Once it has moved, it cannot be moved again.
    - Position Reversed: Reverses the position values for the device. So, a door that would normally start out in its open state would start out in its closed position when this flag is checked.
    - Not usable from any side: prevents the player from being able to use the device.
- **Flags**
    - Does Not Operate Automatically: the device will not operate automatically. If this flag is set, the "automatic activation radius" property in Guerilla will be ignored, and you will need to set up a position group with a device control in order to operate the machine.
    - One-Sided: the device will only operate from one side. The side can be set as the positive x-axis of a marker named "one_way" or the x-axis of the door (or other device) itself if no marker exists.
    - Never Appears Locked: For door objects. The device will never report itself as locked to object function callers. In other words, it will never appear locked to the player (appearance-wise).
    - Opened By Melee Attack: when this flag is set, the player will need to melee the device machine for it to enter its opened state.
    - One-sided For Player: The device will only be accesible to the player from one side. AI can access it from either side. See "One-Sided" flag description for more information.
    - Does Not Close Automatically: prevents a device machine from closing automatically. You will need to set up a position group with a device control (such as a button) to get the device to close.
