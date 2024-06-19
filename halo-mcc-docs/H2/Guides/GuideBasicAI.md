---
title: Halo 2 Guides Character Basic AI #Required; page title is displayed in search results. Include the brand.
description: Character Basic AI for Halo 2 Guides in MCC Modding Documentation. #Required; article description that is displayed in search results. 
author: mjordan343 #Required; your GitHub user alias, with correct capitalization.
ms.author: mjordan #Required; microsoft alias of author; optional team alias.
ms.service: halo-mcc #Required; service per approved list. slug assigned by ACOM.
ms.topic: quickstart #Required; leave this attribute/value as-is.
ms.date: 11/09/2022 #Required; mm/dd/yyyy format.
ms.custom: template-quickstart #Required; leave this attribute/value as-is.
---

# How-To - Setting Up A Character With Basic AI

## BASIC SETUP

character tag must be set up first

object\character\\[character]\ai
designers should set this up

## OPEN SAPIEN

- add character

- add weapon

- add tags\ai\style (usually: guarding)

- Go -> Everything\Mission\AI\Zone
    
    - \# zone = collection of firing positions

- New Instance     # creates new zone

    - expand new zone

- Go -> Firing positions

    - drop several (~6) firing positions by r-click on scenario in Game window    # firing positions must belong to area

- Go -> Area

- new instance     # creates new area

    - assign firing points to new area

- Go -> Firing positions

    - select firing points     # in Game window or Hierarchy view

    - in Properties palette

        - area: assign to area  # ignore NO sign next to FPs in Hierarchy view

        - can select Firing points and Ctrl-N creates new area and assigns FP to new area

- Go -> Squad

    - new instance     # creates new squad

    - in Properties palette

        - set name     # this will be what is called from console

        - set normal diff count = same as insane diff count count (~2) # of characters to spawn

        - set actor defaults

            - \# ignore vehicle

            - character type     # to be spawned

            - initial zone

            - initial weapon

            - (optional: grenade type)

            - \# ignore initial order

- Go -> Squad

    - expand specific squad

- Go -> Starting points

    - place starting points     # [normal diff count] will spawn for each

## IN CONSOLE

console: ai_place \[squad_name]
