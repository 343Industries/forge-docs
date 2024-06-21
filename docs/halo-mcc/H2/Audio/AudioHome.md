---
title: Halo 2 Audio Home #Required; page title is displayed in search results. Include the brand.
description: Audio Home for Halo 2 Audio in MCC Modding Documentation. #Required; article description that is displayed in search results. 
author: mjordan343 #Required; your GitHub user alias, with correct capitalization.
ms.author: mjordan #Required; microsoft alias of author; optional team alias.
ms.service: halo-mcc #Required; service per approved list. slug assigned by ACOM.
ms.topic: quickstart #Required; leave this attribute/value as-is.
ms.date: 11/09/2022 #Required; mm/dd/yyyy format.
ms.custom: template-quickstart #Required; leave this attribute/value as-is.
---

# Audio

## Overview

- Music is used to set the mood, to provide a dramatic component to game mechanics like combat and exploration, and to reward the Player for successes.

- Dialog is used unfold the story, provide characterization and draw the Player into the experience.

## DEFINITIONS

The following details all of the various types of sound assets in the game and their function.  There are occasional references to implementation for the purpose of describing audio types.

### Linear Audio

Any sound used in scripted or pre-rendered scenes that have a set, pre-determined duration is considered linear.

### Interruptive Cinematics

Linear sound effects, music and dialog will be mixed to picture in post-production and delivered in the final format, stereo or surround.

### Linear Music

Music that is traditionally produced, recorded and mixed to a specific length will usually be used to post score an interruptive cinematic, event, or used as a stand alone piece that might play during a splash screen or for marketing purposes. Think “Soundtrack CD”.

### Linear Dialog

A traditional script with characters and storyboard that is recorded and then used as an element in any interruptive cinematic. These are scenes that have a set duration that will not change during game play (or after the final mix).

## Dynamic Sound Effects

Any sound that responds to a game play condition or event is considered to be Dynamic.

Dynamic sounds can be occluded by geometry, they are spatially located, they are effected by physics (reverb, Doppler shift), they have weighted permutations, they must be assigned a priority and may be effected by special characteristics (i.e. an engine sound will change with the rpm’s, or gear shifting, the volume of the sound of a bouncing shell casing will change with the velocity of impact etc.)

### Impulse Sounds

Impulse Sounds are triggered sounds that always play all the way through without interruption and usually include many variations.

Footsteps, gunshots, explosions and bullet impacts are examples of Impulse Sounds.

Impulse sounds may have two or more permutations which can be weighted.

#### Animation Key Frame Sounds

Sounds that are played when an animation hits a key frame.

#### Impact Sounds

Sounds that are played whenever something impacts a surface.  The volume of impact sounds should scale with velocity and distance

Impact Sounds that reflect the material type of the impacted surface are called Sweeteners.

### Looping Sounds

Looping Sounds are multi-sectioned sounds that play for an unspecified length of time, usually determined by the Player’s actions or by Global Functions.

Looping Sounds are constructed in three sections; the **Intro** which is played only once as the sound starts, the **Loop** which consists of multiple and randomly chosen sections that seamlessly connect to each other and is played for the duration of the sound, and the **Outro** which can either be a smooth transition from the **Loop** or interruptive depending on game conditions and is played when the sound ends.

The **Loop** may have two or more permutations which can be weighted.  It may also have several tracks which can be turned on and off independently but are automatically synchronized.

#### Environmental Sounds

Ambient Sounds are Looping Sounds that are associated with a gameplay area such as a room or outdoor location instead of specific objects, so they are not spatially located. 

#### Ambient Sounds

Ambient Sounds are pre-mixed, pre-spatialized sounds that do not change during game play (i.e. the background sound of an interior room, cavern or forest.)

Ambient Sounds will usually be stereo or surround.

#### Detail Sounds

Detail Sounds are discreet in nature, like Impulse Sounds, but are considered looped because they are played again after some random time has passed (i.e. bird sounds in the forest, telemetry sounds in a computer).

Detail Sounds are randomly spatialized according to variable parameters.

#### Attached Sounds

Audio can be attached to specific points in the environment.  Audio can also be attached to projectiles, effects, animations, devices, and particles.

### Game Mechanics

Health sounds, low time sounds, power-ups, game timers, etc.

### Scripted Events

These are what are currently being referred to as Non-Interruptive Run-Time cinematics

### Cascading Sounds

Cascading Sounds are a special group of sounds that will be used to simulate events that are impossible to produce without special considerations (i.e. breaking glass, falling gravel, hundreds of mousetraps being sprung by ping pong balls.)  Rather than attempting to create a cacophony of sound by multiplying single sound events, we step up from simple to more complex sound files based on the number of game events that are being called. In the example of breaking glass we will step up from the sounds of small_glass_crash to medium_glass_crash to huge_piles_o_glass (in stereo) as more glass is broken simultaneously. This technique will produce the desired overwhelming effect and still give the illusion of synchronization.

## Dynamic Music

Dynamic music consists of Looping Sounds of variable length that will be affected by game play.

Dynamic Music consists of an **Intro**, a **Loop** and an **Outro**, but it also has the capability to respond to dynamically changing game conditions.

### Atmospheric Music

Similar to ambient sounds in construction but consisting of more musical or non-reality based sound content. Atmospheric music can evoke specific moods or emotions without using what would be considered traditional elements of music. Still dynamic but with less emphasis on interactivity

### Thematic Music

This music will be more traditional in nature.  Containing recognizable themes and rhythmic elements Thematic Music will immediately alert the player that there is music playing.  Unique themes could be associated with characters, locations, and events.

## Dynamic Dialog

Pre-recorded lines of dialog that can be triggered during game play.

### Scripted Dialog

These are lines designed to play only once during the game. They are tied to a specific game event or scene that may or may not occur depending upon the importance to advancing the story. They can be attached to a specific character or character class i.e. Master Chief talking to Captain Keyes or a Elite talking to a Grunt.

### Conditional Dialog

These are lines designed to play numerous times during the game. They can be triggered by several different conditions such as events, locations, or game state. They might be interruptible or even play simultaneously with other character’s lines. It’s important to record several appropriate permutations that carry the same meaning while keeping the sense of randomness and variation. They can be attached to a specific character or character class i.e. taunts, hurt sounds etc, ally getting killed, killing friends, etc. It’s vitally important during casting and recording to keep track of when and where the actors are performing which kind of dialog. Scripted dialog performed by one actor might be followed by generic dialog performed by a different actor but emanating from the same character. Anticipating the number of repetitions of any piece of generic dialog heard during a player’s experience of a game is also of vital importance.

## Implementation / audio engine tools

What follows is the specific layout of how audio will be implemented into the game. We essentially have three layers: **Soundfiles**, **Soundtags**, and **Looping Sounds**. 

### Soundfiles

This is the raw data, and is irrelevant to anyone other than the audio team beyond the fact that the next layer refers to them.  These files will be 16-bit, 22050 kHz or higher, and can be either mono, stereo, or 5.1.

### Soundtags

Any time a Soundtag is called, a single permutation of that Soundtag is played. 

Sound Designer will be able to assign many Soundfiles to each sound, and weight each permutations probability of being selected.

Soundfiles assigned to each Soundtag can be either mono or stereo but not both.

The following are the controls we need to have at this layer:

### Permutation selection method

Random – Randomly chosen from a weighted list. **This is the Default Choice**

Random, No Repeats – Randomly chosen from a weighted list, but plays all the permutations before repeating

### Maximum Number

If enabled, we can set the maximum number of times a Soundtag can be called in a given period of time.  However, if the Soundtag is being used as part of a Looping Sound this value will be ignored.

### Pitch

Assignable pitch level at which the Soundtag will play.

Assignable pitch range can be assigned for each individual permutation

### Volume

Assignable volume level at which the Soundtag will play

Assignable volume range can be assigned for each individual permutation.

### Occlusion Cap

Occlusion can be capped to a level below which occlusion will stop.  This will prevent audio from being completely cut off due to excessive layers of occluding material between the player and the audio location.

### Priority

Priority can be assigned here in four levels:  Game Essential, Dangerous, Relevant, Atmospheric

### Cascading Sound Controls

There will be mutiple levels to a Cascading Sound.  If the Soundtag (example is glass breaking in a three level cascade) is triggered more than a given number of times in a given period (adjustable) then the next time it is triggered it will trigger the level two Soundfile.  If the Soundtag continues to be triggered (now playing level two Soundfile) more than a given number of times in a given period (adjustable) then the next time the Soundtag is triggered it will trigger the level three Soundfile up to a given number of repetitions.  This should look something like:

| - | - | - |
|---|---|---|
|Soundfile one   |        Number of repetitions|         Time period|
|Soundfile two   |        Number of repetitions|         Time period|
|Soundfile three |        Number of repetitions|                    |

###  DSP

We will be able to send all of the audio from a Looping Sound to DSP.

Defaults will be no buses assigned and 50% mix amount.

#### Buses

We can route and re-route audio through as many effects as we want, we should have some way to select what effect(s) we want to be applied.

#### Mix Amount

We will be able to determine what amount of each effect is mixed in with the original sound.

### Auditioning

We need to have the ability to audition the Soundfiles as we import them, and the Soundtag itself playing back with the parameters we have set.

### Importing groups of Audio

If when importing audio into a  Soundtag we select a folder that contains a number of audio files, all files in the folder will be imported as permutations into the Soundtag.

If we select a folder with a series of nested folders containing varying numbers of audio files, when we import each nested folder will be imported into a separate Soundtag with the files therein as permutations.

### Looping Sounds

This is a layer where the designer can utilize various audio elements for use in Dynamic Music and all flavors of Dynamic Sound Effects.

The designer will attach Soundtag in the various areas detailed below, i.e. we will never be assigning Soundfiles directly to the Looping Sounds area.  Looping Sounds refer  to Soundtags, which in turn refer to the Soundfiles. 

The following are the controls we need to have at this layer:

### Tracks

A Soundtag will be associated with each track as follows:

#### Intro

This is a Soundtag that begins the Looping Sound.

#### Looping Tracks

Ideally we will have several of these to do multi-track mixing “on the fly” in relation to gamestate.  The Looping Track will play directly after the Intro is completed.  If there is no Intro the Looping Sound would begin with the Looping Track(s)

#### Outro

This is a Sound that ends the Looping Sound.  Ideally we could have multiple Outros selectable by gamestate.

#### Detail

The Soundtag attached in this area would consist of multiple permutations (such as computer telemetry audio).  Detail controls will be:

#### Time Range

The range of time during which another detail sound will be triggered.

#### Panning/Positioning

The designer sets the range inside which yaw, pitch, and distance are randomly selected.

### Interrupt On Stop

This will be a checkbox that allows the overall Looping Sound to be interrupted wherever it is currently playing (and jump to Outro or just stop if no Outro).  If this box is unchecked the Looping Sound will finish playing the current loop and then proceed to the Outro.  This should default to unchecked (non-interrupt).

### Looping Sound Transition

In relation to gamestate we will be able to move from one piece of music (Looping Sound) to another.  For instance a piece of music is playing in the Looping Track area above.  As a gamestate parameter changes (player has low health) we could change to a new piece of music in one of two ways:

1. If Interrupt on stop is checked, the music would immediately switch to the Intro of the new Looping Sound.

1. If Interrupt on Stop is not checked, at the end of loop that is currently playing the code would switch to the Intro of the new Looping Sound.

### Auditioning

We need to have the ability to audition the Soundtags as we import them, and the Looping Sound itself playing back with the parameters we have set.

## Implementation / environment / geometry

Both Soundtags and Looping Sounds can be attached to the following areas:

### Geometry

Rooms, hallways, canyons etc will be able to have a Looping Sound attached to them.  We also need to be able to subdivide the given Geometry.  For example if a tunnel opens up into a large cavern and the combination of the two is considered one piece of geometry we would like to be able to divide the current geometry between the tunnel and cavern so we can attach different audio to those two distinct areas. 

### Environment

We need to be able to have the ability to place Looping Sounds spatially (with x,y,z coords).  On these Soundpoints we need to be able to have alterable shapes (spheres, cones, cylinders, etc.) in which the sound will play at its maximum level, and an additional distance assigned beyond that shape between which the volume will fade to zero.

### Particles

When a given particle is present, we will be able to assign a Soundtag to play when the particle impacts (i.e. shrapnel or shell casings).

### Projectiles

When a given projectile is present, we will be able to assign a Looping Sound to play while the projectile exists. 

### Effects

When a given effect is present, we will be able to assign either a Soundtag or Looping Sound to play while the effect is present.  Soundtags would be used in cases such as explosions and Looping Sounds would be used for persistant sounds (such as the fire created from an explosion).

### Impacts

Audio will be triggered for various impacts based on the material that is moving and the surface material being impacted.  This audio will respond to velocity data and can be made up of two distinct Soundtags: a material type Soundtag and a surface type Soundtag (i.e. rifle falling on grass triggers rifle_fall and med_grass_impact).

### Animations

Audio can be added to animations via frame number.  There will be a way to audition animations and the associated audio files

### Vehicles

When a vehicle is at rest (not moving), it will play an idle Looping Sound.

When the vehicle is moving there will be multiple Looping Sounds utilized that respond to conditions such as RPM, acceleration, and deceleration. 

### Scripted Events

We will able to assign Soundtags or Looping Sounds along with scripted events and pass along volumes, fade times, and other parameters to control audio during scripted events.

## Sound Features

### Global Fade

An automatic fade of all audio at the end of level or a scripted event, and a partial fade under menu or interface screens.

### Sound Debug Mode

In the Sound Debug Mode all the sounds being played are printed on-screen along with attributes (configurable).  All audio in use and all attributes can also be dumped to a tab-delimited text file. 

## Occlusion

Occlusion should not be considered when the audio is passing from non-playable space into playable space.  For example, an audio source placed inside environmental geometry that looks like an air conditioner should not be occluded by the geometry that makes up the air conditioner. 

## Test Map

A Test Map specially made for testing audio on materials, weapons, characters, environments etc. should be created.
