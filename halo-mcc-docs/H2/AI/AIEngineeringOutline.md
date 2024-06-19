---
title: Halo 2 AI Engineering Outline #Required; page title is displayed in search results. Include the brand.
description: Engineering Outline for Halo 2 AI in MCC Modding Documentation. #Required; article description that is displayed in search results. 
author: mjordan343 #Required; your GitHub user alias, with correct capitalization.
ms.author: mjordan #Required; microsoft alias of author; optional team alias.
ms.service: halo-mcc #Required; service per approved list. slug assigned by ACOM.
ms.topic: quickstart #Required; leave this attribute/value as-is.
ms.date: 11/09/2022 #Required; mm/dd/yyyy format.
ms.custom: template-quickstart #Required; leave this attribute/value as-is.
---

# AI Engineering Outline

## Spatial Encoding

### Zones

Replacing Encounters will be a “Zone” system. Like encounters, Zones will contain groups of firing points, which actors will use to control their movement. Unlike encounters, Zones are not team-specific, so the spatial information they encode can be used by any actor.

### Areas

Zones will contain Areas, groups of firing points that cover individual regions within a single zone. These areas will be used for the purposes of scripting and order-specification (see [below](#orders)). Potentially, these firing points could be jittered, to allow some variation in position selection (and to avoid the problem where two actors conflict over the same position).

While defined as a set of points, areas also have an associated “margin of error”, which denotes a radius around each point within which all space is still considered to be part of the area. In other words, an actor within a margin distance X of one of the firing points of an area is still considered to be within that area. Areas can be used to define an “allowable region” within which an actor can operate (this would be done with the actors orders, e.g. “defend this region and under no circumstances can you leave it”).

### Firing Point Generation

In addition to the statically laid firing points provided by Areas, actors will be able to generate new firing points for consideration on the fly. These will almost always be task-specific. Thus, if an actor is looking for cover, it will generate firing points around nearby obstacles. These generated points might also be filtered by the agent’s allowable region. Thus an actor might be allowed to take cover behind an obstacle as long as it is within his allowable region.

Firing points will not be generated around static obstacles, since designers can place them when creating the levels. However, generating them around dynamic obstacles will allow the actor to take cover behind vehicles, “blocks” (dynamic obstacles that can be meleed to create cover) and each other. There might even be some rudimentary planning possible in this respect – an object offering some cover points but “only if you melee me first”. These dynamic firing points could also be used in establishing attack formations and setting up positions for coordinated actions.

### Zone-level Activation Control

Actor activation will be controlled on a zone-by-zone basis. Based on what clusters are potentially visible to the viewer, all the zones that are not visible (do not impinge on the PVS) will be deactivated. Consequently all squads in the zone will be deactivated until the player returns to the zone.

Some allowance might be made for squad positions – a squad on their way to an active zone, but not there yet, for example, might be allowed to remain active.

## Squads

Since Encounters are being deprecated, squads will move out of the Encounter structure and become a Scenario-level representation. Actors will generally go into leaf-node Squads, while these leaves will be held together in a larger structure by Squad-Groups.

The main difference with the new representation will be that squads will be put into a hierarchical structure, rather than just a list. This will allow orders, for example, to be given to a potentially large number of actors, while still being able to give smaller groups more specific instructions.

### Squad_groups

The military hierarchy will be encoded in a hierarchical structure, however, only leaf-nodes in this tree will be allowed to actually contain actors. To avoid confusion, intermediate (branch) nodes will be called *squad_groups* (represented in code by a squad_group struct). Squad_groups, like squads, will maintain statistics (current membership, initial membership, etc.) encompassing all their children.

## Orders

Some of the burden of scripting complex battle sequences will be taken over by the new Order system. Orders are atomic instructions to the actors of a squad – instructions on the order of “defend this position”, “secure this area”, and so on. Orders are simple associations of a location and a style. Possible styles include “idle”, “defend” and “attack” (more styles to come). When an order is given to a group of actors (through their *Squad* grouping, see below) the actors will do their best to comply with it.

Orders have an ending condition, indicating when the order has been successfully completed. Possible ending conditions include:

- **If [greater than / less than] X actors alive in squad**

- **If squad at X strength**

- **If enemy sighted**

- **If unopposable enemy within X distance**

- **After X ticks**

- **If alerted by squad X**

- **Arbitrary condition**: specified by script.

Any combination of these conditions can be used to trigger the end of an order. A set of ending conditions also contains a reference to a next order, to which the squad will switch when an order is completed. An order can contain multiple sets of ending conditions (and hence can be followed by multiple orders) reflecting the different possible outcomes of a battle.

These orders, linked together as they are through their ending conditions form an *order tree*. Scripting commands will be available to impose a change of orders (and perhaps a change of order-trees).

There is special interaction between the order system and the squad-tree. When an order is given to a top-level node in the squad-tree, the order filters down to all its children. The exception: an order may be “locked”, such that no parent-level orders can override it. When the ending-conditions of a locked order are met, the next-order is activated (with its lock-status used). If no next-action is provided, the squads will default to the nearest ancestor’s order.

Order options include

- **Locking**: an order cannot be overriden (by an order to a parent of the squad in question, see below). The only ways for a locked order to be changed is by satisfying a set of ending conditions or by an explicit script call.

- **Always active**: A squad executing the command should be be always be kept active.

- **Debug**: Causes additional debugging information to be output when the order is started/stopped.

## Hints

Information is also available through special designer-provided hints. These hints provide information that would be too expensive (or impossible) to derive at run-time, such as good locations to snipe from, or what direction to retreat in (dependant on the subtle ebb and flow of the battle). They might also include information such as “this is a good place to jump up and shoot at the enemy” or “this is something that you could jump over”.

Hints can be associated both with either an order or an entire zone. The former is for team-specific hints (e.g. “flee in that direction”) while the zone-hints are generally available knowledge (e.g. “that is a good position to snipe from”).

Possible hint-types include:

- **Firing position**

- **Cover position**

- **Concealment position**

- **Search position**

- **Sniping position**

- **Climbable**

- **Hang down and shoot from me**

- **Interesting-look**

- **Interesting-touch**

- **Interesting-destroy**

- **No-stopping zone**

- **No-travel zone**

- **Vaulting/jumping**

Like orders, hints express themselves in terms of *Areas* (see [above](#areas)), i.e. in terms of one or a set of firing points (possible with some designer-provided margin in the area-definition).

Hints can also be attached to specific objects (especially if that object is moveable) and object-types (so that the designer need not place a copy of the same hint on every tree, for example). Thus the pinball machine, for example, will tell the actor “I can help you with your entertainment drive”.

## Player-Modeling

It would interesting to try to map a brief history of the player’s recent behavior to a discrete style. Thus, the player might be perceived to be in “sniper-mode”, “aggressive mode”, and so on. The game could react to this mode through specific vocalizations, specialized battle set-ups, and appropriate team (and enemy) behavior. The player mode would be available through script as well as being a possible ending-condition for orders.
