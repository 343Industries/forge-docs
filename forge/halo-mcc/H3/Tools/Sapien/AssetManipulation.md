---
title: Halo 3 Sapien Asset Manipulation Gizmo #Required; page title is displayed in search results. Include the brand.
description: Sapien Asset Manipulation Gizmo for Halo 3 Modding Documentation. #Required; article description that is displayed in search results. 
author: mjordan343 #Required; your GitHub user alias, with correct capitalization.
ms.author: mjordan #Required; microsoft alias of author; optional team alias.
ms.service: halo-mcc #Required; service per approved list. slug assigned by ACOM.
ms.topic: quickstart #Required; leave this attribute/value as-is.
ms.date: 02/14/2022 #Required; mm/dd/yyyy format.
ms.custom: template-quickstart #Required; leave this attribute/value as-is.
---

# Asset Manipulation Gizmo

The Asset Manipulation gizmo in Sapien accomplishes a variety of tasks: It can move, rotate, resize, and reshape various elements within your scenario. The operation of the Asset Manipulation Gizmo is closely tied to the [*Tool Window*](ToolWindow.md). Refer to that article for more information on changing properties of the manipulate gizmo.

![View of the Asset Manipulation Gizmo](./media/H3_Sapien_AssetManipulationGizmo.png)

Figure 1 - Sapien's Asset Manipulation Gizmo

## Use

**Rotate**— You can rotate an asset with the manipulate gizmo along 3 different axes, represented by the three colored triangles (yellow, magenta, and turquoise). To rotate an object, mouse over it until it enlarges, then click and drag to your desired rotation. The rotation function can also be slightly contextual. For example, when placing a light object, you'll need to press the SHIFT key to access the rotate handles.

- ![View of the yellow triangle yaw rotation handle](./media/H3_Sapien_YArrow.png) — The yellow triangle rotates the asset around its **Y** axis (Y = Yaw). This results in sort of spinning the asset.
- ![View of the magenta triangle roll rotation handle](./media/H3_Sapien_RArrow.png) — The magenta triangle rotates the asset along its **R** axis (R = Roll). It tilts the object from side to side (or front-back depending on the direction you're looking at it from).
- ![View of the turquoise triangle pitch rotation handle](./media/H3_Sapien_PArrow.png) — The turquoise triangle rotates the asset along its **P** axis (P = Pitch), resulting in a tilt from forward-back (or side-to-side depending on the direction you're looking at it from).

**Move** (also known as Translation)— You can move assets along their X, Y, and Z axes by mousing over one of the gizmo's four cubes until it turns a semi-solid color, then click and drag to move the asset along that particular axis.

- ![View of the green cube handle used for Y axis movement](./media/H3_Sapien_GreenCube.png) — Click the green cube and drag to move the asset along the Y axis.
- ![View of the green cube handle used for X axis movement](./media/H3_Sapien_OrangeCube.png) — Click the orange cube and drag to move the asset along the X axis.
- ![View of the purple cube handle used for Z axis movement](./media/H3_Sapien_PurpleCube.png) — Click the purple cube and drag to move the asset along the Z axis.
- ![View of the grey cube handle used for free movement](./media/H3_Sapien_GreyCube.png) — Click the grey cube in the center of the gizmo and drag to enter free move mode. This allows you to move the asset along all axes at once and simply place it wherever you want in your scenario.

**Scale** (Resize)— The Scale/resize function of the manipulation gizmo is accessed by pressing the ALT key (and in some cases the CTRL key) and changes based on the type of asset selected. For objects (such as a simple box), the scale tool creates a sphere that matches the bounding sphere of the object (See Figure 2). When moused over, the sphere turns red. Then, you can click and drag to scale the object larger or smaller. For other objects, such as a custom light, there can be more than one scale implementation and you need to use either ctrl or alt to access them— this is so you can resize various planes of the light. See Figure 3 for an example of the scale function on a custom light object.

![View of the scale tool when used on a scenery object](./media/H3_Sapien_ScaleScenery.png)

Figure 2 - The scale function of the gizmo with a box scenery object selected

![View of the scale tool when used on a light object](./media/H3_Sapien_ScaleLight.png)

Figure 3 - The scale function of the gizmo on a custom light object

On a final note, while the asset manipulation gizmo provides a visual reference for making changes to assets, it is also important to note that the changes can be made with more precision via the position, rotation, and scale attributes in the [*Properties Palette*](PropertiesPalette.md) window.
