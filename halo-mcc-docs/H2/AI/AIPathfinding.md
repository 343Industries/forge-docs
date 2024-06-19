---
title: Halo 2 AI Pathfinding #Required; page title is displayed in search results. Include the brand.
description: Pathfinding for Halo 2 AI in MCC Modding Documentation. #Required; article description that is displayed in search results. 
author: mjordan343 #Required; your GitHub user alias, with correct capitalization.
ms.author: mjordan #Required; microsoft alias of author; optional team alias.
ms.service: halo-mcc #Required; service per approved list. slug assigned by ACOM.
ms.topic: quickstart #Required; leave this attribute/value as-is.
ms.date: 11/09/2022 #Required; mm/dd/yyyy format.
ms.custom: template-quickstart #Required; leave this attribute/value as-is.
---

# AI Pathfinding

## ORGANIZATION

### Sectors

In contrast to Halo 1, where path-finding took place directly on the collision BSP surfaces, for Halo 2, we will be grouping surfaces into sectors. These sectors will be convex pathfindable areas within which completely reactive navigation will suffice to get the actors from any point in the sector to any other point in the sector. Sectors will likely be larger than bsp surfaces, and will be able to contain uneven terrain (i.e. normals need not be near-equal) – as long as the terrain is not SO uneven that it can’t be traversed in all directions. Note also that while sectors will be created, for example, for climbable (non-walkable) surfaces, no sectors can COMBINE walkable and non-walkable surfaces (for the same reason as above, that an actor that cannot climb will not be able to traverse the sector-space freely). Similarly, breakable and non-breakable surfaces cannot be combined.

Initially, in most cases, sectors will be groupings of existing BSP surfaces – i.e. each collision surface will belong to exactly one sector. This restriction might be eased later on if it is deemed necessary in some cases to split individual surfaces in order to make the overall sector partitioning cleaner. ALSO, note that the environmental collision BSP will NOT be the only source of sectors – certain environment objects will also be able to be walked on – sectors on these objects will be created with similar rules.

## Links

Sectors will be connected via links (the equivalent of edges in the BSP surface rep). Again, most links will simply be references to some underlying collision BSP edge (since in the base case the sector-reps will be groupings of collision surfaces).

Most of these links will simply represent the need for an actor to walk from one sector to another (around a wall, for example). However, in some cases, special-purpose information might be encoded in the link to indicate that the two sectors are connected in a special way – for example, the actor needs to climb a ladder to get from one sector to another, or the actor needs to jump.

See section below on “[special-purpose sector-links](#special-purpose-sector-links)” for more details.

## ALGORITHMS

Initially the algorithms for path-planning will remain unchanged, with the exception of the new terrain-preprocessing step.

## A*

The fundamental path-planning algorithm remains A*.

### Terrain pre-processing

The fundamental new algorithm, the terrain pre-processing step requires us to generate a list of sectors based in large part on the collision bsp model. The difference, again, is sectors don’t require surfaces of nearly-equal normals – they can incorporate fairly uneven surfaces, as long as the surface is still pathfindable in all directions.

We will use the standard greedy algorithm done in Halo1 for the collision BSP and in the Tozour article. We will repeatedly iterate over the collision surfaces, attempting to coallesce them into larger convex sectors (on subsequent iterations, sectors will be coallesced and so on, until no more sectors can be merged). Depending on what the results of this process produces, we may well also perform something like the 3→ 2 merging process described in the Tozour article (unfortunately, this would create edges and vertices in the path-finding graph that do NOT exist in the collision BSP – resulting in larger storage requirements for those edges and vertices).

### Surface → Sector Mapping
The process of discovering the sector at a certain point is critical to allowing AIs to pathfind about their environment. Since AIs always have a current surface, we can use a surface à sector mapping. We do this by laying down 2-d bsps on the collision surfaces at sector-creation time. These bsps can then be queried with a surface point to find the sector.

## SPECIAL-PURPOSE SECTOR-LINKS

### Link types

Beyond simply walking from one sector to another, sometimes a more specific behavior is required. What type of behavior depends on information that will be stored in the link (quite a bit of it is placed by hand by a designer or environment artist in the form of environmental “hints”). Envisioned link-types include:

- **Elevators**

- **Ladders**

- **Jump points**

- **Climb points**

- **Vault points**

- **Crawl points**

- **…**

### Behavior-system integration

In order to incorporate a behavioral component into individual path-links, the command-list notion of an “AI atom” will be recycled. The “atom-evaluator”, the piece of codes which transforms atoms into specific orders for the actor to execute, will be pulled out of the action_obey code, and be made a general module that can be used by any ai system (e.g. individual actions could conceivably express their effects in terms of atoms). Links in the pathfinding graph can contain one or a number of these AI atoms, which together specify the type of behavior required to traverse a link. For example, an “elevator” link, might contain the following atoms:

- **Navigate to point \<x,y,z>**

- **Orient to direction \<x,y,z>**

- **play animation “push button”**

- **Wait until elevator arrives (until event detection)**

- **navigate to \<x,y,z>**

- **Wait until elevator arrives at destination**

- **navigate to point \<x,y,z>**

Even a “normal” link – the kind whereby one can simply walk from one sector to another – could be considered to contain a single atom of “Navigate to \<x,y,z>” where the point specified is a point on the edge between the two sectors (though it’s unlikely that it will actually be implemented this way).

## DYNAMIC SURFACES

A number of the path-findable surfaces will be attached to dynamic environment objects (and vehicles and so on) which means that many of the links they have to static sectors will be temporary. For example, a warthog being driven through a scene might have a small sector (probably a single point) where enemies may jump onto its hood to attack the driver. As the jeep drives from sector to sector, an enemy must know which sector it has to navigate to to jump onto the jeep.

This might be accompished as follows: a “jump hint” on the hood of the warthog would need to be placed by the artist or designer of the vehicle. This jump hint would contain information both on where on the hood the enemy would land but also a small number of locations on the ground (in warthog-relative space) that the enemy could jump from. As the warthog drives around, these points follow it. These points can also be traced to a specific sector. Thus, if an enemy wish to jump onto the warthog, it has to navigate first to the sector from which it can begin its jump.

The link encoding the ability to jump onto the warthog hood must obviously be invalidated if the warthog is overturned.
