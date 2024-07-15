---
title: Halo 3 Objects Setting Model Variants Regions Permutations and States #Required; page title is displayed in search results. Include the brand.
description: Objects Setting Model Variants Regions Permutations and States for Halo 3 Modding Documentation. #Required; article description that is displayed in search results. 
author: mjordan343 #Required; your GitHub user alias, with correct capitalization.
ms.author: mjordan #Required; microsoft alias of author; optional team alias.
ms.service: halo-mcc #Required; service per approved list. slug assigned by ACOM.
ms.topic: quickstart #Required; leave this attribute/value as-is.
ms.date: 03/17/2022 #Required; mm/dd/yyyy format.
ms.custom: template-quickstart #Required; leave this attribute/value as-is.
---

# Setting Model Variants, Regions, Permutations, and States

The following are step-by-step setup instructions for configuring a Variant, Region, Permutation, and State for a model.

> [!IMPORTANT]
> This section is built from the original documentation and is tailored for use in 3ds Max, but the important principles can be used in any 3d program.

1. Go to the *Variants* tag block (the first block in the tag below the initial information) and add a Variant (click the Add button).

1. Enter a unique name for the variant. If you use the name Default, this will automatically be set as the default variant for the model— meaning that every time you drop one (or one is spawned) in the game, you will get this variant (unless you specify a different variant in Sapien).

1. Under the *Regions* tag block, add a new region (click the Add button). The *Regions* tag block is a sub-block of *Variants* and is located directly below it.

1. For *Region Name*, enter the name of one of the regions you specified for the model in 3ds Max (if you haven't done so, go back and do it, then re-export and import it).

1. For **Parent Variant**, you can select NONE or the name of any variant you have set up. The Region will inherit the properties of whatever variant you select as its parent.

1. Add a new permutation in the *Permutations* tag block (click the Add button). *Permutations* is a sub-block of *Regions* and is located directly below it.

1. For **Permutation Name**, enter any name you would like to call this particular permutation of the model. In many cases, this can simply be default. It has nothing to do with the permutations you already set up in 3ds Max (those are used in the damage states section). The only time you would want to use multiple permutations is if you were going to have different versions of the same object, which could be spawned based on the probability setting in the same tag block (such as the different kinds of marines, for example).

1. If you want every permutation you set up to share the states of the current one, you can check the *Copy states to all permutations box*. Otherwise, leave it empty.

1. Add a new state in the *States* tag block (click the Add button). The *States* block is a sub-block of *Permutations*, which means it's located directly below it.

1. For **Permutation Name**, enter the name of a permutation for the particular region you are working with. You should have specified the permutations for the region in 3ds Max. If you haven't done so, you'll have to go do that, then re-export/import.

1. If you'd like this state to be blurry (perhaps if you're using it in conjunction with some type of smoke effect, for example), check one of the blur checkboxes. Otherwise, you can leave them blank.

1. For **State** select one of the states from the drop-down list. This can be connected later to a damage section/response. You will need to set up a state for each permutation you created for this particular region in 3ds Max.

1. If you'd like this state of this permutation of this Region of this variant of the model to be connected to some type of effect (smoking, sparking, burning, etc.), you can add one under **Looping Effect**. Click the browse button to find the effects tag you want.

1. If you've selected a looping effect tag, you need to choose a marker on the object to play it from. You need to set these markers up in 3ds Max. Once you've done that (and re-exported/imported), enter the name of the marker in the **Looping Effect Marker Name** text box.

1. Open Sapien. Add your model to the palette, and place one of your objects in the scenario. The default variant will automatically be placed. If you'd like to specify another variant, you can do so by entering the name of the variant in the **Variant** text box of the properties palette.
