---
title: Halo 3 HowTos Init.txt Scenario Pruning #Required; page title is displayed in search results. Include the brand.
description: HowTos Init.txt Scenario Pruning for Halo 3 Modding Documentation. #Required; article description that is displayed in search results. 
author: mjordan343 #Required; your GitHub user alias, with correct capitalization.
ms.author: mjordan #Required; microsoft alias of author; optional team alias.
ms.service: halo-mcc #Required; service per approved list. slug assigned by ACOM.
ms.topic: quickstart #Required; leave this attribute/value as-is.
ms.date: 02/16/2022 #Required; mm/dd/yyyy format.
ms.custom: template-quickstart #Required; leave this attribute/value as-is.
---

# Init.txt Scenario Pruning

The game has the capacity to prune assets through init.txt. The functionality essentially converts regular scenarios into empty and empty_cinematic scenarios at runtime.

## Commands and Definitions

prune_scenario_force_solo_mode on
- Forces the map to be loaded in solo mode even if it is a multiplayer map. The game will look for a solo map spawn point.

prune_scenario_for_environment_editing_keep_cinematics on
- Same as prune_scenario_for_environment_editing, with the inclusion of cutscene flags and cinematics.

prune_scenario_for_environment_editing
- Removes everything but the environment: Weapons, vehicles, bipeds, equipment, cinematics, AI, etc.

prune_scenario_force_single_bsp_zone_set
- Removes all but the first bsp from the initial zone set. Ensures that the initial zone set will not crash on load due to low memory.

prune_scenario_add_single_bsp_zones:
- Add single bsp zone sets (for each bsp) to the debug menu.

prune_scenario_lightmaps
- Loads the scenario without lightmaps; same as dont_load_lightmaps.

prune_global
- Strips all player information, global materials, grenades and powerups from the globals tag, as well as interface global tags. Same as scenario_load_fast. Don’t use this if you need the game to be playable.

prune_global_material_effects
- Loads the scenario without material effects; same as dont_load_material_effects.

prune_global_dialog_sounds
- Removes all dialog sounds referenced on the globals tag. Same as editor_strip_dialogue_sounds.

prune_global_keep_playable
- Strips player information (keeping one element), global materials, grenades and powerups. Keeps the game playable; same as scenario_load_fast_and_playable.

## Suggested Configurations

The following table provides suggested configurations for different types of users. You may copy these commands directly into your init.txt file.

|**Designer**|**Artist**|**Cinematics**|
|------------|----------|--------------|
|prune_global_keep_playable on|prune_scenario_for_environment_editing on|prune_scenario_for_environment_editing_keep_cinematics on|
|prune_scenario_lightmaps on|prune_scenario_force_single_bsp_zone_set on|prune_scenario_force_single_bsp_zone_set on|
|            |prune_scenario_add_single_bsp_zones on|prune_scenario_add_single_bsp_zones on|
|            |prune_global on|prune_global_keep_playable on|

> [!Note]
> Effects should still use the empty_cinematic scenarios because they contain custom scripts.
