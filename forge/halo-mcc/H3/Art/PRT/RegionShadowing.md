---
title: Halo 3 PRT Region Shadowing #Required; page title is displayed in search results. Include the brand.
description: PRT Region Shadowing for Halo 3 Modding Documentation. #Required; article description that is displayed in search results. 
author: mjordan343 #Required; your GitHub user alias, with correct capitalization.
ms.author: mjordan #Required; microsoft alias of author; optional team alias.
ms.service: halo-mcc #Required; service per approved list. slug assigned by ACOM.
ms.topic: quickstart #Required; leave this attribute/value as-is.
ms.date: 03/21/2022 #Required; mm/dd/yyyy format.
ms.custom: template-quickstart #Required; leave this attribute/value as-is.
---

# Region Shadowing

By default, **PRT** (Pre-computer Radiance Transfer) uses the first permutation of a region to cast shadows on all the other regions. Because you don't have any control over which is the first permutation (the assignment is random) the **Shadow Cast Override** parameter has been added to the .model tag, which allows you to set which (if any) permutation for a given region will cast shadows over the other regions. Only one permutation can cast shadows.

## **PRT Console Commands**

You can disable PRT by using the console command render_disable_prt true. You will also find this in the debug menu under **4 Graphics -> 1 Lighting -> 9 Object Lighting -> 1 disable PRT**.

## **Default PRT Region Shadowing**

Here's a simple object with two regions: **box** with no permutations and **number** with two permutations: **zero** and **one** (see Figure 1).

|![A box displaying no permutations.](./media/H3_PRT_NoPermutations.png)|![A box displaying a permutation causing the number zero to apppear.](./media/H3_PRT_ZeroPermutation.png)|![A box displaying a permutation causing the number one to apppear.](./media/H3_PRT_OnePermutation.png)|

Figure 1 - Boxes

By default, PRT uses the initial permutation for a region to cast shadows on all permutations of all of the other regions. There is no way to set which is the initial permutation. In this case, the initial permutation for the region number is zero. You can see this in the .render_model tag:

![View of the permutations section of the regions tag in guerrilla with the drop down menu set to zero.](./media/H3_PRT_RegionZero.png)

Figure 2 - Region set to zero

So the **zero** permutation of the **number** regions casts a shadow on the **box** region. Note that this shadow is baked into the **box** region and is visible whether the number region is set to permutation \<none>, **zero** or **one**.

|![A box displaying no permutations and shadow for the number zero.](./media/H3_PRT_NoPermutationsShadow.png)|![A box displaying a permutation causing the number zero to apppear with a shadow.](./media/H3_PRT_ZeroPermutationShadow.png)|![A box displaying a permutation causing the number one to apppear but a shadow for the number zero.](./media/H3_PRT_OnePermutationShadow.png)|

Figure 3 - Shadow Example

## **Overriding the Default PRT Region Shadowing**

You can override the default PRT region shadowing by using the **Shadow Cast Override** in the .model tag. Enter a region and the permutation name you want to be shadow casting. The names **must** match existing region and permutation names - check the .render_model tag if you are unsure.

![View of the shadow cast override section in guerrilla with fields for region and shadow cast permutation.](./media/H3_PRT_RegionZero.png)

Figure 4 - Shadow cast override

|![A box displaying no permutations with a shadow of the number one.](./media/H3_PRT_NoPermutationsShadowOverride.png)|![A box displaying a permutation causing the number zero to apppear with a shadow for the number one.](./media/H3_PRT_ZeroPermutationShadowOverride.png)|![A box displaying a permutation causing the number one to apppear with the correct shadow.](./media/H3_PRT_OnePermutationShadowOverride.png)|

Figure 5 - Shadow Example

You can make it so no permutations for a given region cast shadows by leaving the permutation field blank (see Figure 6).

![View of the shadow cast override section in guerrilla with fields for region and shadow cast permutation with the field left blank.](./media/H3_PRT_RegionZero.png)

Figure 6 - Blank permutation field
