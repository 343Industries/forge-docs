---
title: Halo 2 AI Behavior List #Required; page title is displayed in search results. Include the brand.
description: Behavior List for Halo 2 AI in MCC Modding Documentation. #Required; article description that is displayed in search results. 
author: mjordan343 #Required; your GitHub user alias, with correct capitalization.
ms.author: mjordan #Required; microsoft alias of author; optional team alias.
ms.service: halo-mcc #Required; service per approved list. slug assigned by ACOM.
ms.topic: quickstart #Required; leave this attribute/value as-is.
ms.date: 11/09/2022 #Required; mm/dd/yyyy format.
ms.custom: template-quickstart #Required; leave this attribute/value as-is.
---

# AI Behavior List

> [!NOTE]
> Behavior in italics are IMPULSES, which means they simply trigger another behavior to run, or run a specialized piece of code – however, they themselves have no duration. As such you will never seem them in the behavior stack of a character.

> [!NOTE]
> “Danger” has a very specific technical meaning in Halo 2. You can see the amount of danger an AI thinks he’s in by turning on “ai_render_emotions 1” at the console and selecting a character.

> [!NOTE]
> Most of the parameters controlling behavior (timing, probabilities, etc.) are located in the .character tag for the character.

## GENERAL
- **Root**: Root of behavior tree (always on)

- **Null**: literally, do nothing

- **Obey**: running a command script

- **Guard**: stand on a firing position

- **Ready**: Run upon first transition into a combat state

## ENGAGE

Runnable when enemies present

- **Engage**: root of engage subtree

- **Fight**: Stand and shoot. Also handles maneuvering when targets moves outside of ideal combat ranges (based on weapon properties of character tag)

- **Melee charge**: run towards the target and melee

- **Surprise**: When target’s back is turned, sneak up behind to close distance (often followed by melee-charge)

- **Grenade impulse**: Consider throwing grenades (probabilisic, and subject to timing constraints. See character tag)

- **Anti-vehicle-grenade**: Throw grenades at vehicles when on foot

- **Stalk**: When given “suppress combat” orders (a flag in the order structure), AI stalks instead of fighting visible target (i.e. get close to them, but don’t open fire)

## BERSERK

Berserking is a state where the AI behaves extremely aggressively, often throwing down all but melee weapons, and then hard-charging their target.

- **Last man berserk**: when all allies of my type have died in my area, berserk.

- **Stuck-with-plasma-grenade-berserk**: when stuck with a plasma grenade, berserk.

## PRESEARCH

When we first lose sight of a target, we consider our “presearch” options.

- **Presearch**: Root of presearch subtree

- **Presearch uncover**: Run the uncover behavior (see SEARCH)

- **Destroy cover**: If target is hiding behind a destroyable object, shoot the object

- **Suppressing fire**: Failing any of the above, stand and shoot at the last place you saw target. If the target moves, this behavior will finish quickly. If not, it will last a longish time, giving the illusion of pinning the target down.

- **Grenade uncover**: throw a grenade to flush the target from behind cover (only after we’ve just lost sight of them)

- **Leap-on-cover**: if the player is hiding behind an object that has mount or hoist hints on it, jump on top of it.

## SEARCH

The target has been gone for some time, or we’re just coming out of cover.

- **Search**: root of search subtree

- **Uncover**: pick a firing point from where I expect to be able to see the target that is currently hidden.

- **Investigate**: Go to the point I currently think the target is at.

- **Pursuit-sunc**: If I’m searching with other people, wait for them to investigate their current search point.

- **Pursuit**: Not having found the target where I though it would be, pick another point (current hidden from me) to search at.

- **Postsearch**: We have given up on the target. Pick a point in the open near where we first lost sight of the target.

- **Coverme_investigate**: I’m searching with a friend. Have him cover me (stay put) while I investigate my current search point.

## SELF-PRESERVATION

Self-preservation is a set of controlled cover-seeking/defensive behaviors. This is opposed to RETREAT, which is a full-on panic.

- **Self-preservation**: Root of the self-preservation subtree

- **Cover**: Find a point that is hidden from my target (the guy I’m hiding from) and go there, possibly playing a cool lean-up-against-the-wall animation when I get there.

- **Cover-peek**: After I’ve been in cover a while, if I am leaning against a wall or bunkering, lean out from behind wall an fire on enemy is they are then visible. Duck back behind cover immediately if I’m hit by enemy fire.

- **Avoid**: If a danger zone is coming my way (grenade, or mortar, or danger enemy vehicle) move to a point that is safe from that danger zone.

- **Evasion impulse**: Hop to the side to avoid enemy fire.

- **Dive impulse**: If I’m in immediate danger from a vehicle or grenade or suck, dive away from it.

- **Danger cover impulse**: If I’m in a certain amount of danger (and my shields are below a certain level, etc.), run self-preserve. (Considered when running ENGAGE).

- **Danger crouch impulse**: When I’m in a certain amount of danger, crouch down.

- **Proximity melee**: If I’m trying to self-preserve, but my target gets too close to me, melee charge him instead of running away.

- **Proximity-self-preserve**: If my target gets too close to me, self preserve (considered when running ENGAGE)

- **Unreachable-enemy-cover**: If I’m being sniped by an enemy from beyond my maximum combat range, take cover.

- **Scary-target-cover**: If my target is facing me and aware of me, and is very scary (e.g. he’s a flood juggernaut, or he’s holding a scary weapon like a rocket launcher and I’m not), self-preserve (considered when running ENGAGE).

- **Group-emerge**: If I’m finished covering and there are other guys near me who are also covering, wait for them so that we can all emerge from cover together.

## RETREAT

A paniced, mindless retreat from a target

- **Retreat**: Root of retreat subtree

- **Retreat-grenade**: Throw a grenade at my target before taking off.

- **Flee**: Run away to a hiding point, playing my crazy fleeing animations as I go.

- **Cower**: Crouch down at my hiding place, fearing for my life.

- **Low-shield-retreat**: Considered when running ENGAGE

- **Scary target retreat**: Considered when running ENGAGE

- **Leader dead retreat**: GRUNTS ONLY. An elite died, and there are no more elites around me. Flee!

- **Peer dead retreat**: Probabilistically retreat is one my friends just died.

- **Danger retreat**: Above a certain danger level, possibly retreat.

- **Proximity retreat**: If my target gets too close to me, retreat.

- **Charge when cornered**: If I have nowhere else to go, turn around and run melee-charge.

- **Surprise retreat**: If I’m surprised by a target, possibly retreat.

- **Overheated weapon retreat**: If my weapon overheated, retreat!

## AMBUSH

After a retreat target has cowered for enough time, he begins to try to ambush his target (i.e. emerge at an opportune time)

- **Ambush**: Root of ambush subtree

- **Coordinated ambush**: If there are others trying to ambush, hook up with them, and ambush together.

- **Proximity ambush**: If my target appears very near to me, start fighting again.

- **Vulernable enemy ambush**: My target is vulnerable, e.g. nearby and facing away from me. Ambush.

- **Nowhere to run ambush**: I have nowhere else to run, start fighting again.

## VEHICLE

This section covers behaviors for getting in/out of vehicles, and things to do when you’re in a vehicle.

- **Vehicle**: Get in a vehicle.

- **Enter friendly vehicle**: If the player is in a nearby vehicle, get in with him.

- **Re-enter flipped vehicle**: A vehicle that I was recently flipped out of is upright again, so get back into it.

- **Vehicle entry engage impulse**: I’m fighting an enemy, and there's a vehicle available nearby. Get in it.

- **Vehicle board**: Jump on my enemy’s vehicle and board him.

- **Vehicle fight**: Drift around my target and fight.

- **Vehicle charge**: Strafe my target

- **Vehicle ram**: Ram my target.

- **Vehicle cover**: Pick a point far away from my target (but preferably still visible) and go there.

- **Damage vehicle cover**: Run vehicle cover if my vehicle has taken a certain amount of damage recently.

- **Exposed rear cover**: Someone is shooting me from behind. Run vehicle-cover.

- **Vehicle avoid**: Danger is coming my way. Strafe to the side to avoid it.

- **Vehicle pickup**: I need a gunner. Go find someone to be my gunner.

- **No driver exit vehicle impulse**: I’m in a vehicle without a driver. If I’m a passenger get out immediately.

- **Danger vehicle exit impulse**: I’m in a vehicle without a driver, and danger is heading my way. Get out.

- **Vehicle flip**: A vehicle that I want to get into is flipped nearby. Either flip it myself (if it’s ghost-sized) or get two buddies to help me flip it (if it’s warthog-sized).

- **Vehicle turtle**: (Wraiths) “Crouch” down if I’ve taken a certain amount of damage.

## POSTCOMBAT

What we do after combat is finished and there are no more enemies.

- **Postcombat**: root of postcombat subtree

- **Post-postcombat**: root of postpostcombat subtree

- **Check friend**: Kneel down beside the body of a friend and say something touching.

- **Shoot corpse**: Shoot the dead body of an enemy corpse.

- **Postcombat approach**: In postpostcombat, regroup with my friends, if we’re scattered.

## ALERT

When we THINK there are enemies in the area, but we don’t know where they are (either because we were fighting them and they got away or because the designers has told us we should be alert).

- **Alert**: Root of alert subtree

## IDLE

There are no enemies around.

- **Idle**: root of idle subtree

- **Wander**: We have a small area to available to us. Wander from one firing point to another.

- **Flight wander**: Wander for flying creatures

- **Patrol**: Walk around, picking a firing position in each area in my orders.

- **Fall-asleep**: If nothing is going on, go to sleep.

## SWARMS/FLOOD

Swarm- and flood-specific behaviors. Swarms have their own tree entirely separate from any other type of character.

- **Swarm root**

- **Swarm attack**: Run toward a target and jump at it.

- **Support attack**: If a flood combat form is fighting the target, hang back.

- **Infect**: Run up to a dead flood body on the ground and resurrect it.

- **Scatter**: If a certain percentage of a swarm has died recently, run away.

- **Eject parasite**: If a flood combat form loses both its arms, it releases an infection form and collapses.

- **Flood self-preservation**: All flood retreat at the same time.

- **Juggernaut flurry**: After receiving a certain amount of damage, the juggernaut runs a “flurry” melee animation (undirected area melee damage)

## SENTINELS

- **Enforcer weapon control**: Enforcer changes the weapon it uses depending on target range, suppressing fire etc.

- **Grapple**: If target is in a vehicle, boost over the vehicle.

## SPECIAL

- **Formation**: Jackals can form a number of formations and march forward together.

- **Grunt scare by elite**: A grunt walks up to an elite, the elite turns around and plays his “berserk” animation. The grunt then flees from him.

- **Stunned**: Get stunned by a nearby grenade explosion. Stumble around, clutching your ears.

- **Cure isolation**: I’m standing on a nonwalkable sector, or an isolated walkable sector. Try a bunch of tricks to get back to a walkable surface.

- **Deploy turret**: If I’m carrying a deployable turret, run to a specially-marked script point and deploy it there
