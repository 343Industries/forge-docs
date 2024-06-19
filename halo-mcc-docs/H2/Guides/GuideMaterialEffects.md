---
title: Halo 2 Guides Information on material_effects #Required; page title is displayed in search results. Include the brand.
description: Information on material_effects for Halo 2 Guides in MCC Modding Documentation. #Required; article description that is displayed in search results. 
author: mjordan343 #Required; your GitHub user alias, with correct capitalization.
ms.author: mjordan #Required; microsoft alias of author; optional team alias.
ms.service: halo-mcc #Required; service per approved list. slug assigned by ACOM.
ms.topic: quickstart #Required; leave this attribute/value as-is.
ms.date: 11/09/2022 #Required; mm/dd/yyyy format.
ms.custom: template-quickstart #Required; leave this attribute/value as-is.
---

# How-To - Information on material_effects

General guidelines for setting up material effects in objects and the divisions between the art and sound pipelines.

## OVERVIEW

There are many types of objects which have a material_effects slot in them (crates, vehicles, bipeds, etc.). Generally, you should leave this slot empty and allow the surface types of the various objects to generate art effects and sound fx as it is laid out in globals.globals.

There are several instances where we you will hook up a material_effects tag to that slot in a specific object:

- art or sound wants to treat the object as a single entity instead of the collection of various pieces (think warthog).
here are two objects of the same surface type where the sound or art just does not fit for both... we would then special case one of them and let the other one be taken care of by globals

- all bipeds will have material_effects tags assigned to them for footsteps. However as long as the only events in these tags are footstep events all other aspects of havok interaction (collisions, grinding, rolling) will be taken care of by globals according to surface type.

- As a general rule, avoid using material_effects tags hooked up at the object level. It adds complexity to an already complex hierarchy. However given that art and sound may want to special case something at the object level we need to follow


### A SIMPLE RULE

If, for instance, an audio guy decides to special case sound fx for an object they make a new material_effects tag and hook it up at the object level. This tag should not have any ART elements present in the ART tag block area. So if perchance that audio guy started with another material_effects tag and did a “save as” to a new tag that very same audio guy should delete all of the art references in the art tag block area. This will allow sound to override at the object level, but art effects to proceed to globals and resolve surface type effects there. And vice versa.

In a nutshell if anyone hooks up a material_effects tag at the object level it should only have references in it for their own discipline.

The following are template material_effects tags which can be used as a starting point and will have all references from the “other side” already removed.

```
effects/materials/sound_template.material_effects

effects/materials/effects_template.material_effects
```

Also as a reminder ALL material_effects tags should live somewhere in the directory structure under tags\effects\materials...
