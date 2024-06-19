---
title: Halo 2 AI Overview #Required; page title is displayed in search results. Include the brand.
description: Overview page for Halo 2 AI in MCC Modding Documentation. #Required; article description that is displayed in search results. 
author: mjordan343 #Required; your GitHub user alias, with correct capitalization.
ms.author: mjordan #Required; microsoft alias of author; optional team alias.
ms.service: halo-mcc #Required; service per approved list. slug assigned by ACOM.
ms.topic: quickstart #Required; leave this attribute/value as-is.
ms.date: 11/09/2022 #Required; mm/dd/yyyy format.
ms.custom: template-quickstart #Required; leave this attribute/value as-is.
---

# AI Overview

## BEHAVIORS

- **Formations**: Any homogenous collection of characters can group itself into a formation. However, there are currently no rules dictating when this should be done, since it is largely assumed that most formations will be scripted. This is an appropriate way, for example, to do AI insertions. (e.g. player enters a clearing just in time to see a jackal phalanx march around the corner). A formation behavior could, for example, be initiated by the level designer in an HS command script that aborts when the AIs become aware of an enemy. Thus the formation holds until the player opens fire, and then everyone scatters.

## MOVEMENT

### Environmental Pathfinding Hints

- **Jump hints**: Jumping connections can be designated between unconnected pieces of geometry. The AIs will then be able to pathfind through these hints. Note that jump-hints take the form of two parallel rails, where a point on the departure rail takes the AI to the corresponding point on the arrival rail. (this is as opposed to a single point-to-point connection).

- **Climb hints**: Climbing hints can be placed on certain configurations of geometry. This requires two levels of floor connected through a perfectly vertical wall. Unlike the jump hints, climb hints are point-to-point, like a ladder.

- **Pathfinding on moveable objects**: There are two types of objects that can be set to be pathfindable, i.e. that AI will be able to navigate on: scenery and machinery. While scenery is static (and therefore look, to pathfinding, like just another piece of the environment) machinery can animate in arbitrary ways. Examples of this include elevators, and Marcus’s magic floating platforms. Firing positions can be placed on these machines, and the AI will behave and move just as they would on the ground. In order to connect these machines to the rest of the environment, **jump hints** must be placed between suitable entry/exit points.

    In the future, moveable pieces of bsp will also be navigatable in this way.

### Object Hints

In addition to hints that are explicitly placed in the environment by the level-designer, special hint-markers can be added to object render_model definitions which will create hints automatically for every placed instance of that object.

- **Jump hints**: The markers must be names hint_jump_Xa, hint_jump_Xb, hint_jump_Xc and hint_jump_Xd, where X is the number of the hint, in two-digit format starting from 01 (i.e. 01, 02, 03, … 10, 11, 12 …) Each set of four markers defines, as in the explicitly-placed environment hints, a set of two rails, with a and b defining the departure rail and c and d defining the destination rail. 

> [!NOTE]
> that the geometric configuration of the hint markers must be the same as the environmental ones, with a and c being on the same side and b and d being on the same (stated another way, if you took a vector a→b and another vector c→d, both vectors would be pointing in roughly the same direction).

- **Climb hints**: Only two markers are required, name in the format hint_climb_Xa and hint_climb_Xb. Like their explicitly-placed counterparts, the order must be from the lower surface (a) to the upper surface (b).

## POSTURES

- **Wall leaning**: In certain circumstances, AIs will assume special covering postures near a corner providing cover (e.g., marines leaning their back against the wall). In order for this to happen there are two requirements: (a) a firing position needs to be placed near the corner (within about 0.4 wus). (b) the geometry must consist of floor connected directly with vertical wall (such that, for example, there can be no bevel at the base of the wall). The wall must also be of sufficient height (about 0.6 wus) and breadth to hide a human-sized character.

## OBJECTS

### Pathfinding with Obstacles

Usually AIs just pathfinding around objects as part of the process of obstacle-avoidance. In certain circumstances, however, certain types of obstacles can be “dealt with” in special ways. There are three  types of such obstacles (or strategies for by-passing the obstacle): low mid and high threshold. Low-threshold obstacles are ones that are ignored completely at pathfinding time and then dealt with as needed (e.g. smashing and vaulting). This means that even if the object is easily avoided, it will be dealt with regardless. A hunter for example, will not even attempt to avoid the space crate that is in his way. High-threshold obstacles, by contrast, are dealt with only as a last resort. So for example, an elite will destroy a destroyable obstacle in his path only if there is no other convenient way to get to where he wants to go.

#### Low threshold

- **Trample**: Ignore the obstacle altogether, possibly dealing it damage as you step on it.

- **Smash**: Havok objects that are appropriately annotated (in their object-definition) can be knocked aside by certain types of characters (e.g. hunters smashing aside convenant space crates).

- **Vault**: Objects with appropriate markers can be vaulted over by certain AI characters (e.g. elite vaulting over overturned covenant space crate).

- **Leap**: Obstacle can be leaped over entirely

#### High threshold

- **Destroyable**: When the destroy_obstacle behavior is enabled, characters can destroy destroyable obstacles if they are uniquely blocking the path to their goal (and there is no convenient way to get around it).

- **Knock**: Some obstacles can be knocked aside, or knocked over, in order to get past them (involves far more effort than merely smashing obstacles).

- **Mount**: Can jump on top of object to get past it.

- **Hoist**: AIs can hoist themselves onto the top of the object to get past it.

### Object-Behaviors

- **Destroy cover**: If a target has taken cover behind an object that is destroyable, an AI might respond by attempting to destroy the object.

- **Mount cover**: If a target has taken cover behind a havok object, the AI might decide, if it can, to leap onto the top of the object to expose its target.

- **Hoist to uncover**: A target is uncovered by hoisting onto the cover obstacle.

- **Knock to uncover**

- **Knock to create cover**

- **Knock to deal damage**: a nearby object can be knocked onto the target in order to damage it

## AMBIENT LIFE

### Flocks

A flock of a certain kind of unit can be placed down for flavor in a certain area. The units making up the flock will be pretty stupid, and so not very fun to interact with. The best way to use them is for flocks of birds in the distance, or flocks of spaceships flying overhead.

A flock is placed through a block in the scenario definition. This block contains all the parameters that control the flock (which can be tweaked to make it look like anything from a loose flock of birds to a tight school of fish). You can also control the number of members in the flock and the noise parameters that can add a small amount of random movement to each flock-member’s heading.

Due to run-time considerations, flocks cannot directly perceive the environment or any of the objects in it. Instead the flock’s allowable space is defined by a simple geometric shape which is placed by a level designer. Currently the only supported shape is a squashed-sphere shape, which is defined by a center, a radius (xy) and a height (z). The flock will wander about within this shape by turn around when it reaches its edges.
