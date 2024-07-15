---
title: Halo 2 Animations Inherited Animations #Required; page title is displayed in search results. Include the brand.
description: Inherited Animations for Halo 2 Animations in MCC Modding Documentation. #Required; article description that is displayed in search results. 
author: mjordan343 #Required; your GitHub user alias, with correct capitalization.
ms.author: mjordan #Required; microsoft alias of author; optional team alias.
ms.service: halo-mcc #Required; service per approved list. slug assigned by ACOM.
ms.topic: quickstart #Required; leave this attribute/value as-is.
ms.date: 11/09/2022 #Required; mm/dd/yyyy format.
ms.custom: template-quickstart #Required; leave this attribute/value as-is.
---

# Animations - Inherited Animations

## Changes to the animation tags

Model_animation_graph tags must always contain the same list of nodes as the model tag. This is a requirement so that we can build lookup tables to map inherited graphs to the local nodes without having knowledge of the model. We perform the actual inheritance while post-processing the animation tag, at which point we no longer have knowledge of the model.

On import, we populate the animation graph’s node list with the nodes from the model – not the animation. We no longer compare checksums between model and animation nodes either, since we will allow animations to contain only a subset of model nodes. Instead, we check that all animation nodes appear in the model, and have identical parent nodes. We do all these comparisons as string compares of the node names. If a node can not be found, or it does not have the same parent (with an exception for the root node in the animation), we consider the model and animation incompatible and abort.

Animation data is expanded to contain 4 bit fields (up from 3). The three existing bit fields flag which nodes have animated rotation, translation and scale data. When these bits are not set, data is pulled from the animations ‘default’ data section. To further reduce the tag size, and facilitate animations which contain only a subset of the model nodes, we will add a 4th bit field which signifies whether a non-animated node has a local default orientation, or whether the default orientation should be read from the model itself.

At run-time, we pre-seed the model orientation list with the default orientations from the model. Then, we only need to overwrite the portions of the data for nodes which are present in the animation.

## Inheritance

Each animation graph contains a single link to an inherited tag. At post-process time, we build a run-time list of all inherited graphs by recursively loading each linked tag in the chain. There is a max inheritance list of 8 for the time being. For each inherited tag, we build a lookup table which maps our local node indices to the indices of the inherited graph. Local nodes which do not appear in the inherited graph have an entry of NONE. When computing orientations for a model, we use this table to map model nodes to animation nodes. When the entry is NONE, we can skip the node since we already pre-seeded the orientation list with default model orientations for each node.
