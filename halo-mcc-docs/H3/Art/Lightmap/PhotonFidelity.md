---
title: Halo 3 Lightmap Photon Fidelity #Required; page title is displayed in search results. Include the brand.
description: Lightmap Photon Fidelity for Halo 3 Modding Documentation. #Required; article description that is displayed in search results. 
author: mjordan343 #Required; your GitHub user alias, with correct capitalization.
ms.author: mjordan #Required; microsoft alias of author; optional team alias.
ms.service: halo-mcc #Required; service per approved list. slug assigned by ACOM.
ms.topic: quickstart #Required; leave this attribute/value as-is.
ms.date: 03/17/2022 #Required; mm/dd/yyyy format.
ms.custom: template-quickstart #Required; leave this attribute/value as-is.
---

# Lightmap Photon Fidelity

> [!IMPORTANT]
> This section is built from the original documentation and is tailored for use in 3ds Max, but the important principles can be used in any 3d program.

Adjust the photon fidelity in 3ds Max (see Figure 1). The settings are:

- 0: Don't cast photons off this surface (useful for large outdoor areas on the edges of maps, like deltatemple)

- 1 (default): Normal photons cast off this surface

- 2: Dim photons (so more photons per unit light) cast off this surface. good for darker-than-normal spaces

- 3: Really dim photons cast off this surface. Good for extremely dark spaces with lots of bounced light

![View of the parameters menu in 3 d s max with the field for Photon Fidelity outlined in red.](./media/H3_Lightmap_PhotonFidelity.png)

Figure 1 - Photon Fidelity.
