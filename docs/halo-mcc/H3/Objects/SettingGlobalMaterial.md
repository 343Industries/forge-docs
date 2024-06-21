---
title: Halo 3 Objects Setting Global Material Types #Required; page title is displayed in search results. Include the brand.
description: Objects Setting Global Material Types for Halo 3 Modding Documentation. #Required; article description that is displayed in search results. 
author: mjordan343 #Required; your GitHub user alias, with correct capitalization.
ms.author: mjordan #Required; microsoft alias of author; optional team alias.
ms.service: halo-mcc #Required; service per approved list. slug assigned by ACOM.
ms.topic: quickstart #Required; leave this attribute/value as-is.
ms.date: 03/17/2022 #Required; mm/dd/yyyy format.
ms.custom: template-quickstart #Required; leave this attribute/value as-is.
---

# Setting Global Material Types

Global Material Types for objects can be set in 3ds Max, but sometimes it's useful to use the collision material name to identify damage sections. If you do, it's important to set the global material type correctly in the tags.

![Flow chart showing physics material taking the material name from Max and making a physics model material and a collision material taking a name from Max and making a collision model which becomes a model with the material name.](./media/H3_Objects_PhysicsCollisionMaterials.png)

Figure 1 - Physics and Collision Materials.


## Setting global material types: collision vs. physics

**.physics_model**

After import, the .physics_model tag will pick up the material name as set in 3ds Max. You can override this in the .physics_model tag by setting the Global Material Type. Right-click global material name in the tag and a hierarchal menu will appear (see Figure 2).

![View of the menu selection in the physics model hierarchy going from global material type to hard to hard metal thin to hard metal thin cov to hard metal thin cov.](./media/H3_Objects_GlobalMaterial.png)

Figure 2 - Setting the global material type in the .model tag.

**.collision_model**

After import, the .collision_model tag will pick up the material name as set in 3ds Max. **You cannot override this in the .collision_model tag**. The .model tag will pick up the material name from the .collision_model tag. You can override this in the .model tag by setting the Global Material Type.
