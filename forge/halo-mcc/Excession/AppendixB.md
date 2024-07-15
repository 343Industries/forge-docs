---
title: Excession Tool Appendix B #Required; page title is displayed in search results. Include the brand.
description: Excession Tool Apendix B for MCC Modding Documentation. #Required; article description that is displayed in search results. 
author: mjordan343 #Required; your GitHub user alias, with correct capitalization.
ms.author: mjordan #Required; microsoft alias of author; optional team alias.
ms.service: halo-mcc #Required; service per approved list. slug assigned by ACOM.
ms.topic: quickstart #Required; leave this attribute/value as-is.
ms.date: 10/31/2022 #Required; mm/dd/yyyy format.
ms.custom: template-quickstart #Required; leave this attribute/value as-is.
---

# Appendix B: How to generate the "multiplayer_object_types.bin" file?

The **multiplayer_object_types.bin** file allows the system to define the game variants (e.g. Slayer, Oddball, CTF, King Of Hill, Infection, and so on) that will be playable on the particular multiplayer map.

> [!NOTE]
> **NOTE #1**: You are able to import data from the **multiplayer_object_types.bin** file to a multiplayer map when defining its properties in Excession, using the **IMPORT MULTIPLAYER OBJECT TYPES** button – see [Multiplayer Map properties](../Excession/CreatingModPackage/SpecifyingProperties.md#multiplayer-map-properties) for details.

> [!NOTE]
> **NOTE #2**: If the **multiplayer_object_types.bin** file is empty or undefined for the map different behavior will occur depending on the title.<br /> <br />For Reach, only the Infection game variant will be available for the multiplayer map. <br />For Halo 2 Anniversary, maps will **not** appear at all in the Custom Game lobby.<br />For Halo 4, it will show Slayer, Flood, and Regicide as available game variants.

This file contains the list of entities that are provided by the map (e.g. its weapons, vehicles, grenades, and so on). The contents of this list define the compatibility of this multiplayer map with certain game variants.

The **multiplayer_object_types.bin** file can be generated for the map by one of Halo Modding Tools – **tool.exe**. This applies to Halo Reach, Halo 2 Anniversary, and Halo 4.

Alternatively, while a scenario is loaded in a **Standalone (Tag Test) tool**, running this command "**motl_dump_bitvector_for_scenario**" will generate the multiplayer_object_types.bin file in the root of the title's tools folder.

To generate this file you need to use the **multiplayer-generate-scenario-object-type-bitvector** command in this tool. The syntax of this command is the following:

```
multiplayer-generate-scenario-object-type-bitvector <scenario> <cache_file_resource_gestalt> <output_file>
```

Where:

- **\<scenario>** – The path to the **.scenario** tag file of the map. This path should be specified relative to the **tags** folder of your Halo Editing Kit directory and should include the name of the **.scenario** tag file *without* the file extension.

- **\<cache_file_resource_gestalt>** – The path to the **.cache_file_resource_gestalt** tag file, which is generated during the process of final building of the map (creation of the .map file). This path should be specified relative to the **tags** folder of your Halo Editing Kit directory and should include the name of the **.cache_file_resource_gestalt** tag file *without* the file extension.

    The file is located in the [Root Mod Tools Folder]\reports\\[map]. 

    - For example: Deadhead\reports\52_ivory_tower\52_ivory_tower.cache_file_resource_gestalt

    That file should be copied into the tags folder. It is recommended to use the map's scenario folder:

    - For example: Deadhead\tags\levels\multi\52_ivory_tower

- **\<output_file>** – The path to the resulting **multiplayer_object_types.bin** file.

For example:

```
tool.exe multiplayer-generate-scenario-object-type-bitvector path/to/scenario/name path/to/gestalt/name multiplayer_object_types.bin

```
