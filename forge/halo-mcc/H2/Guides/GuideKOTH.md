---
title: Halo 2 Guides KOTH in MP #Required; page title is displayed in search results. Include the brand.
description: KOTH in MP for Halo 2 Guides in MCC Modding Documentation. #Required; article description that is displayed in search results. 
author: mjordan343 #Required; your GitHub user alias, with correct capitalization.
ms.author: mjordan #Required; microsoft alias of author; optional team alias.
ms.service: halo-mcc #Required; service per approved list. slug assigned by ACOM.
ms.topic: quickstart #Required; leave this attribute/value as-is.
ms.date: 11/09/2022 #Required; mm/dd/yyyy format.
ms.custom: template-quickstart #Required; leave this attribute/value as-is.
---

# How-To - Set Up King of the Hill in MP

Hills are differentiated by their team designator. The team marked "Alpha" team is the one used in a non-moving hill game. Hills with an identifier of "0" are used to mark the hill boundary.

Each boundary point in a hill is one of two handles defining a point on a bezier curve--the hill periphery. I know, it's ugly. The first point placed is the second handle of the first point, the next is the first handle of the next point, and so on, until you close the loop with your last netgame flag being the first handle of the first point. **Your total number of points defining the perimeter must be even!**

Points with an identifier of "1" are not used to define the perimeter, but instead are used to define the upper and lower boundaries of the hill. These can be left off and the hill will use default heights, but the bottom will be level with the perimeter points, resulting in a hill where even the smallest depression causes a player to leave the boundary. Typical hills have an even number of boundary points, a point marking the lower bounds, and a point marking the upper bounds.
