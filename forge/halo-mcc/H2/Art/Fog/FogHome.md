---
title: Halo 2 Fog Home #Required; page title is displayed in search results. Include the brand.
description: Fog Home for Halo 2 Art in MCC Modding Documentation. #Required; article description that is displayed in search results. 
author: mjordan343 #Required; your GitHub user alias, with correct capitalization.
ms.author: mjordan #Required; microsoft alias of author; optional team alias.
ms.service: halo-mcc #Required; service per approved list. slug assigned by ACOM.
ms.topic: quickstart #Required; leave this attribute/value as-is.
ms.date: 12/09/2022 #Required; mm/dd/yyyy format.
ms.custom: template-quickstart #Required; leave this attribute/value as-is.
---

# Halo 2 Fog Home

There are three different types of fog in the game: **sky fog**, **atmospheric fog** and **planar fog**. This page describes how they work, how to use them and how to debug problems when they occur.

At runtime, the atmospheric fog overrides everything. Then it checks if the cluster can “see” a sky, and if that sky has fog. The planar fog is considered separately.
