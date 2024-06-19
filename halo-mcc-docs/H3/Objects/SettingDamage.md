---
title: Halo 3 Objects Setting Damage Sections and States #Required; page title is displayed in search results. Include the brand.
description: Objects Setting Damage Sections and States for Halo 3 Modding Documentation. #Required; article description that is displayed in search results. 
author: mjordan343 #Required; your GitHub user alias, with correct capitalization.
ms.author: mjordan #Required; microsoft alias of author; optional team alias.
ms.service: halo-mcc #Required; service per approved list. slug assigned by ACOM.
ms.topic: quickstart #Required; leave this attribute/value as-is.
ms.date: 03/17/2022 #Required; mm/dd/yyyy format.
ms.custom: template-quickstart #Required; leave this attribute/value as-is.
---

# Setting Damage Sections and States

To set up working damage sections and states, there are a number of things that need to be configured within the .model tag. They are:

1. In Guerilla, open up the .model tag for your object/model and add an instance of the **New Damage Info** block.

1. Select both a **collision damage reporting type** and a **response damage reporting type** from the drop-down lists (these are within the *New Damage Info* tag block).

1. Define the Vitality/Health properties of the model by Filling in the **body** section of the *New Damage Info* tag block (the shield section is optional— if you want the model to be shielded, fill it in).

1. Add one or more **Damage Sections** to the model (click the Add button in the *Damage Sections* tag block). For the object to be set up correctly, you need to add one damage section per region of the object. The *Damage Sections* tag block is a sub-block of *New Damage Info*.

1. For each Damage Section you add, give it a **Name** and set the **vitality percentage** (this is the sections percentage of the overall vitality of the model/object).

1. Add an **Instant Response** for each damage section you created. The *Instant Response* tag block is a sub-block of *Damage Sections* and won't be available until you've added a damage section.

1. Enter a **Region** of the model where you'd like the response to occur (this is a region you have already pre-defined in 3DS Max).

1. From the drop-down list, select the **state** you'd like the damage section to enter when the instant response fires. In order for the response to play on the object, you must have already set up states for the region of the model you entered in the last step. For more information on setting up Variants, Regions, Permutations, and States, see the article here.

1. Now go back up near the top of the *New Damage Info* block. Select the name of one of your damage sections in the **Indirect damage section** drop down list.

1. Directly above the *New Damage Info* block is the *Materials* block. For each material (one for each collision/physics sub-material you set up in Max), you need to assign a **Damage Section**. Simply pick one of the damage sections you created from the drop down list.

1. Also in the *Materials* tag block, you need to specify a global material name for each material. You can easily select a global material type by right-clicking global material name and then navigating through the sub-menus until you find the material you want.

1. Save
