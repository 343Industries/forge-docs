---
title: Halo 3 Animation Facial Animation #Required; page title is displayed in search results. Include the brand.
description: Animation Facial Animation for Halo 3 Modding Documentation. #Required; article description that is displayed in search results. 
author: mjordan343 #Required; your GitHub user alias, with correct capitalization.
ms.author: mjordan #Required; microsoft alias of author; optional team alias.
ms.service: halo-mcc #Required; service per approved list. slug assigned by ACOM.
ms.topic: quickstart #Required; leave this attribute/value as-is.
ms.date: 03/16/2022 #Required; mm/dd/yyyy format.
ms.custom: template-quickstart #Required; leave this attribute/value as-is.
---

# Facial Animation

You can have eight emotional states which may seem limiting, but they can be blended to create more than 64 individual emotional states. For example, the canonical 7 emotions identified by FACS can be blended to create 47 emotions.

> [!IMPORTANT]
> This section is built from the original documentation and is tailored for use in Maya, but the important principles can be used in any 3d program.

## **Generating the Animation**

Each character that wishes to speak or show emotion must contain two animations in its graph:

- *facial_animation_base.jmr*

- *facial_animation_overlay.jmo*

These animations are made from the same Maya file, exported twice. Once as a replacement animation to create *facial_animation_base.jmr* and once as an overlay to generate *facial_animation_overlay.jmo*.

> [!NOTE]
> Different frame counts are exported for each animation. The total frame set to author is shown below:

- Base Pose— Matching models default pose

- Base Pose Copy— Must match the base pose!

- Base Pose Blink— Must match the base pose, except for eye blink

## **Neutral Face**

- Neutral: Silent— Mouth closed.
- Neutral: Eat
- Neutral: Earth
- Neutral: If
- Neutral: Ox
- Neutral: Oat
- Neutral: Wet
- Neutral: Size
- Neutral: Church
- Neutral: Fave
- Neutral: Though
- Neutral: Told
- Neutral: Bump
- Neutral: New
- Neutral: Roar
- Neutral: Cage
- Neutral: unused
- Neutral: Eyebrow Raise— Must match r;silent pose, except for eyebrows
- Neutral: Eyebrow Lower— Must match r;silent pose, except for eyebrows
- Neutral: Blink— Must match r;silent pose, except for blink

## **Happy Face**

- Happy: Silent— Mouth closed.
- Happy: Eat
- Happy: Earth
- Happy: If
- Happy: Ox
- Happy: Oat
- Happy: Wet
- Happy: Size
- Happy: Church
- Happy: Fave
- Happy: Though
- Happy: Told
- Happy: Bump
- Happy: New
- Happy: Roar
- Happy: Cage
- Happy: unused
- Happy: Eyebrow Raise— Must match silent pose, except for eyebrows
- Happy: Eyebrow Lower— Must match silent pose, except for eyebrows
- Happy: Blink— Must match silent pose, except for blink

Sad Face— Frames 43–62, repeat the phoneme set for a Sad character

Angry Face— Frames 63–82, repeat the phoneme set for an Angry character

Disgusted Face— Frames 83–102, repeat the phoneme set for a Disgusted character

Scared Face— Frames 103–122, repeat the phoneme set for a Scared character

Surprised Face— Frames 123–142, repeat the phoneme set for a Surprised character

Pain Face— Frames 143–162, repeat the phoneme set for a character in Pain

163–165— Unused (should match base pose of frame #0)

166— Orientation Head Pitch Pos  

167— Orientation Head Pitch Neg

168— Orientation Head Roll Pos  

169— Orientation Head Roll Neg

170— Orientation Head Yaw Pos  

171— Orientation Head Yaw Neg

172— Gaze Eye Pitch Pos

173— Gaze Eye Pitch Neg

174— Gaze Eye Yaw Pos

175— Gaze Eye Yaw Neg

176— Eyebrow Raise Left

177— Eyebrow Lower Left

178— Eyebrow Raise Right

179— Eyebrow Lower Right

## **Animation Graphs**

1. First, export the entire 180 frame animations as **facial_animation_overlay.jmo**.

1. Next, export only the first 162 frames (all the emotions and phonemes) as **facial_animation_base.jmr**.

1. Reimport the character’s animation graph so that the new animations are included.

1. Make sure compression is disabled for both (Best Accuracy) and save the graph.

## **Scripted Emotions**

There are two ways to instruct a unit to show emotion: scripting and lipsync.

In scripts, we provide the command: 

```
unit_set_emotion_by_name \<unit> \<emotion> \<weight> \<seconds>*
```

This command tells \<unit> to become \<emotion> over the next \<seconds> seconds. The amount in which they display the emotion is indicated by \<weight>. For example, *unit_set_emotion_by_name johnson happy 0.5 3* instructs the character **Johnson** to display his happy face at 50% strength. If Johnson is not already showing his happy face at 50%, he can use the next 3 seconds to interpolate to it.

Emotions can be combined to create new emotions or cross-fade between two or more emotions. If you had already used the happy example above, and then added unit_set_emotion_by_name johnson angry 0.5 3 the r;johnson character would interpolate to show both the happy and angry faces at the same time, each with the corresponding weight. To shut off an emotional face, simply give it a weight of zero to interpolate to: unit_set_emotion_by_name johnson angry 0 1

In this example, the angry face would shut off over 1 second. Specifying a time value of zero will make the change instant.

## **Embedded Emotions**

We can also embed emotional changes directly into the lipsync animations. You can do this by either hand-editing an animation and exporting an fxx file, or adding emotional commands to the text file associated with your audio.

For example, imagine we had a sound file (angry_marine.aif) and a text file (angry_marine.txt) containing the dialog:

*Enemies spotted, kill them!*

We could embed emotional response into the text file, and have it affect the animation produced.

["r;shock" 50%] Enemies spotted, [/shock] ["r;anger" 100%] kill them! [/anger]

This would instruct the system to add the shocked emotional state to the two three words of the dialog at 50% strength, and 100% of anger for the final two words.

> [!NOTE]
> The actual parameters used are more complicated than the ones shown in this example and provide full control over the weighting curve generated.

## **Further Notes**

During a cinematic the animators have full control over the face until one of the following happens:

- a script command sets an emotion

- dialog begins

When one of these happens the face nodes moved by the facial_animation_base animation will transition to engine control. Even if the animator has moved these nodes, they will be trumped by the runtime system. Once the dialog ends, or the script clears the emotion, those nodes revert back to animator control.

Nodes which are not moved by facial_animation_base (usually the head & eyes) will always remain under the animator’s control.

There is no way to turn phoneme animation on or off, it turns itself on when dialog audio is running and shuts down when it isn’t.
