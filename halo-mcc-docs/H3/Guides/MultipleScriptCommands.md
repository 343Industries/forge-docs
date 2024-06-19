---
title: Halo 3 HowTos Executing Multiple Script Commands #Required; page title is displayed in search results. Include the brand.
description: HowTos Executing Multiple Script Commands for Halo 3 Modding Documentation. #Required; article description that is displayed in search results. 
author: mjordan343 #Required; your GitHub user alias, with correct capitalization.
ms.author: mjordan #Required; microsoft alias of author; optional team alias.
ms.service: halo-mcc #Required; service per approved list. slug assigned by ACOM.
ms.topic: quickstart #Required; leave this attribute/value as-is.
ms.date: 02/16/2022 #Required; mm/dd/yyyy format.
ms.custom: template-quickstart #Required; leave this attribute/value as-is.
---

# Executing Multiple Script Commands

Executing multiple script commands in a single line

It is possible, and quite handy, to execute multiple script/console commands within a single line. Here's how to do it:

1. Wrap each command in parentheses. For example:
    - (game_speed 0.5)
    - (print "hello")
    - (drop "objects\vehicles\ghost\ghost")
1. Put all the commands in a single line:
    - (game_speed 0.5)(print "hello")(drop "objects\vehicles\ghost\ghost")
1. Finally, wrap the whole line with a (begin \<commands>) statement like so:
    - (begin(game_speed 0.5)(print "hello")(drop "objects\vehicles\ghost\ghost"))
    - Don't forget the parentheses at the end!
