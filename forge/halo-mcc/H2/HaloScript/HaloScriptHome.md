---
title: Halo 2 HaloScript Home #Required; page title is displayed in search results. Include the brand.
description: HaloScript Home for Halo 2 HaloScript in MCC Modding Documentation. #Required; article description that is displayed in search results. 
author: mjordan343 #Required; your GitHub user alias, with correct capitalization.
ms.author: mjordan #Required; microsoft alias of author; optional team alias.
ms.service: halo-mcc #Required; service per approved list. slug assigned by ACOM.
ms.topic: quickstart #Required; leave this attribute/value as-is.
ms.date: 11/10/2022 #Required; mm/dd/yyyy format.
ms.custom: template-quickstart #Required; leave this attribute/value as-is.
---

# H2 HaloScript Reference

> [!NOTE]
> This list may be outdated. You can get the latest list using 'script_doc' in the game console or running the script-doc command in tool.exe to ensure you have a full list.

## (begin \<expression(s)>)
returns the last expression in a sequence after evaluating the sequence in order.

## (begin_random \<expression(s)>)
evaluates the sequence of expressions in random order and returns the last value evaluated.

## (if \<boolean> \<then> [\<else>])
returns one of two values based on the value of a condition.

## (cond (\<boolean1> \<result1>) [(\<boolean2> \<result2>) [...]])
returns the value associated with the first true condition.

## (set \<variable name> \<expression>)
set the value of a global variable.

## (and \<boolean(s)>)
returns true if all specified expressions are true.

## (or \<boolean(s)>)
returns true if any specified expressions are true.

## (+ \<number(s)>)
returns the sum of all specified expressions.

## (- \<number> \<number>)
returns the difference of two expressions.

## (* \<number(s)>)
returns the product of all specified expressions.

## (/ \<number> \<number>)
returns the quotient of two expressions.

## (min \<number(s)>)
returns the minimum of all specified expressions.

## (max \<number(s)>)
returns the maximum of all specified expressions.

## (= \<expression> \<expression>)
returns true if two expressions are equal

## (!= \<expression> \<expression>)
returns true if two expressions are not equal

## (> \<number> \<number>)
returns true if the first number is larger than the second.

## (< \<number> \<number>)
returns true if the first number is smaller than the second.

## (>= \<number> \<number>)
returns true if the first number is larger than or equal to the second.

## (<= \<number> \<number>)
returns true if the first number is smaller than or equal to the second.

## (sleep \<short> [\<script>])
pauses execution of this script (or, optionally, another script) for the specified number of ticks. 

## (sleep_forever [\<script>])
pauses execution of this script (or, optionally, another script) forever.

## (sleep_until \<boolean> [\<short>])
pauses execution of this script until the specified condition is true, checking once per second unless a different number of ticks is specified.

## (wake \<script name>)
wakes a sleeping script in the next update.

## (inspect \<expression>)
prints the value of an expression to the screen for debugging purposes.

## (unit \<object>)
converts an object to a unit.

## (not \<boolean>)
returns the opposite of the expression.

## (pin \<real> \<real> \<real>)
returns the first value pinned between the second two

## (print \<string>)
prints a string to the console.

## (players)
returns a list of the players

## (volume_teleport_players_not_inside \<trigger_volume> \<cutscene_flag>)
moves all players outside a specified trigger volume to a specified flag.

## (volume_test_object \<trigger_volume> \<object>)
returns true if the specified object is within the specified volume.

## (volume_test_objects \<trigger_volume> \<object_list>)
returns true if any of the specified objects are within the specified volume.

## (volume_test_objects_all \<trigger_volume> \<object_list>)
returns true if any of the specified objects are within the specified volume.

## (list_get \<object_list> \<short>)
returns an item in an object list.

## (list_count \<object_list>)
returns the number of objects in a list

## (effect_new \<effect> \<cutscene_flag>)
starts the specified effect at the specified flag.

## (effect_new_on_object_marker \<effect> \<object> \<string>)
starts the specified effect on the specified object at the specified marker.

## (damage_new \<damage> \<cutscene_flag>)
causes the specified damage at the specified flag.

## (damage_object \<damage> \<object>)
causes the specified damage at the specified object.

## (damage_objects \<damage> \<object_list>)
causes the specified damage at the specified object list.

## (damage_players \<damage>)
damages all players with the given damage effect

## (object_create \<object_name>)
creates an object from the scenario.

## (object_create_clone \<object_name>)
creates an object, potentially resulting in multiple objects if it already exists.

## (object_create_anew \<object_name>)
creates an object, destroying it first if it already exists.

## (object_create_containing \<string>)
creates all objects from the scenario whose names contain the given substring.

## (object_create_clone_containing \<string>)
creates clones for all objects from the scenario whose names contain the given substring.

## (object_create_anew_containing \<string>)
creates anew all objects from the scenario whose names contain the given substring.

## (object_destroy \<object>)
destroys an object.

## (object_destroy_containing \<string>)
destroys all objects from the scenario whose names contain the given substring.

## (object_destroy_all)
destroys all non player objects.

## (object_destroy_type_mask \<long>)
destroys all objects matching the type mask

## (objects_delete_by_definition \<object_definition>)
deletes all objects of type \<definition>

## (object_hide \<object> \<boolean>)
hides or shows the object passed in

## (object_set_shadowless \<object> \<boolean>)
set/reset shadow castingness of object

## (object_set_ranged_attack_inhibited \<object> \<boolean>)
FALSE prevents object from using ranged attack

## (object_set_melee_attack_inhibited \<object> \<boolean>)
FALSE prevents object from using melee attack

## (objects_dump_memory)
debugs object memory usage

## (object_get_health \<object>)
returns the health [0,1] of the object, returns -1 if the object does not exist

## (object_get_shield \<object>)
returns the shield [0,1] of the object, returns -1 if the object does not exist

## (object_set_shield_effect \<object> \<real> \<real>)
sets the shield response effect (not current shield amount) to a given value over the given number of seconds (cinematic use only, remember to call (object_set_shield_effect 0 0) after use!)

## (object_set_physics \<object> \<boolean>)
prevents an object from running physics or colliding with any other objects

## (object_get_parent \<object>)
returns the parent of the given object

## (objects_attach \<object> \<string> \<object> \<string>)
attaches the second object to the first both strings can be empty

## (objects_detach \<object> \<object>)
detaches from the given parent object the given child object

## (object_set_scale \<object> \<real> \<short>)
sets the scale for a given object and interpolates over the given number of frames to achieve that scale

## (object_set_velocity \<object> \<real>)
Sets the (object-relative) forward velocity of the given object

## (object_set_velocity \<object> \<real> \<real> \<real>)
Sets the (object-relative) velocity of the given object

## (garbage_collect_now)
causes all garbage objects except those visible to a player to be collected immediately

## (garbage_collect_unsafe)
forces all garbage objects to be collected immediately, even those visible to a player (dangerous!)

## (garbage_collect_multiplayer)
runs multiplayer garbage collection

## (object_cannot_take_damage \<object_list>)
prevents an object from taking damage

## (object_can_take_damage \<object_list>)
allows an object to take damage again

## (object_cinematic_lod \<object> \<boolean>)
makes an object use the highest lod for the remainder of the levels' cutscenes.

## (object_cinematic_collision \<object> \<boolean>)
makes an object not collide with other cinematic collision objects.

## (object_uses_cinematic_lighting \<object> \<boolean>)
makes an object use the cinematic directional and ambient lights instead of sampling the lightmap.

## (cinematic_lighting_set_primary_light \<real> \<real> \<real> \<real> \<real>)
sets the pitch, yaw, and color (red, green, blue) of the cinematic shadowing diffuse and specular directional light.

## (cinematic_lighting_set_secondary_light \<real> \<real> \<real> \<real> \<real>)
sets the pitch, yaw, and color (red, green, blue) of the cinematic non-shadowing diffuse directional light.

## (cinematic_lighting_set_ambient_light \<real> \<real> \<real>)
sets the color (red, green, blue) of the cinematic ambient light.

## (objects_predict \<object_list>)
loads textures/geometry/sounds necessary to present objects that are about to come on-screen

## (objects_predict_high \<object_list>)
loads textures/geometry/sounds necessary to present objects that are about to come on-screen

## (objects_predict_low \<object_list>)
loads textures/geometry/sounds necessary to present objects that are about to come on-screen

## (object_type_predict_high \<object_definition>)
loads textures necessary to draw an object that's about to come on-screen.

## (object_type_predict_low \<object_definition>)
loads textures necessary to draw an object that's about to come on-screen. 

## (object_type_predict \<object_definition>)
loads textures necessary to draw an object that's about to come on-screen.

## (object_teleport \<object> \<cutscene_flag>)
moves the specified object to the specified flag.

## (object_set_facing \<object> \<cutscene_flag>)
turns the specified object in the direction of the specified flag.

## (object_set_shield \<object> \<real>)
sets the shield vitality of the specified object (between 0 and 1).

## (object_set_permutation \<object> \<string> \<string>)
sets the desired region (use "" for all regions) to the permutation with the given name, e.g. (object_set_permutation flood "right arm" ~damaged)

## (object_set_region_state \<object> \<string> \<model_state>)
sets the desired region (use "" for all regions) to the model state with the given name, e.g. (object_set_region_state marine head destroyed)

## (objects_can_see_object \<object_list> \<object> \<real>)
returns true if any of the specified units are looking within the specified number of degrees of the object.

## (objects_can_see_flag \<object_list> \<cutscene_flag> \<real>)
returns true if any of the specified units are looking within the specified number of degrees of the flag.

## (objects_distance_to_object \<object_list> \<object>)
returns minimum distance from any of the specified objects to the specified destination object. (returns -1 if there are no objects to check)

## (objects_distance_to_flag \<object_list> \<cutscene_flag>)
returns minimum distance from any of the specified objects to the specified flag. (returns -1 if there are no objects, or no flag, to check)

## (position_predict \<real> \<real> \<real>)
in: x, y, z position. loads textures/geometry/sounds necessary to present locations that are about to come on-screen.

## (shader_predict \<string>)
in: shader name. loads textures necessary for a shader.

## (bitmap_predict \<string>)
in: bitmap name. loads all the bitmaps in that bitmap group

## (script_recompile)
recompiles scripts.

## (script_doc)
saves a file called hs_doc.txt with parameters for all script commands.

## (help \<string>)
prints a description of the named function.

## (random_range \<short> \<short>)
returns a random value in the range [lower bound, upper bound)

## (real_random_range \<real> \<real>)
returns a random value in the range [lower bound, upper bound)

## (physics_constants_reset)
resets all physics constants to earthly values

## (physics_set_gravity \<real>)
set global gravity acceleration relative to earth

## (havok_debug_start)
start up the havok visual debugger

## (havok_dump_world \<string> \<boolean>)
dump the state of the havok world, with our without a movie

## (havok_dump_world_close_movie)
end the capture of a havok dump movie

## (breakable_surfaces_enable \<boolean>)
enables or disables breakability of all breakable surfaces on level

## (breakable_surfaces_reset)
restores all breakable surfaces

## (recording_play \<unit> \<cutscene_recording>)
make the specified unit run the specified cutscene recording.

## (recording_play_and_delete \<unit> \<cutscene_recording>)
make the specified unit run the specified cutscene recording, deletes the unit when the animation finishes.

## (recording_play_and_hover \<vehicle> \<cutscene_recording>)
make the specified vehicle run the specified cutscene recording, hovers the vehicle when the animation finishes.

## (recording_kill \<unit>)
kill the specified unit's cutscene recording.

## (recording_time \<unit>)
return the time remaining in the specified unit's cutscene recording.

## (render_lights \<boolean>)
enables/disables dynamic lights

## (render_debug_structure_cluster \<long>)
enables cluster debugging

## (render_debug_structure_fog_plane \<long>)
enables fog plane debugging

## (render_debug_structure_fog_zone \<long>)
enabled fog zone debugging

## (render_debug_structure_fog_zone_floodfill \<long>)
enables fog zone debugging

## (render_debug_structure_opacity \<real>)
sets the opacity (0 is default)

## (render_debug_structure_non_occluded_fog_planes \<boolean>)
controls non-occluded fog plane debugging

## (scenery_get_animation_time \<scenery>)
returns the number of ticks remaining in a custom animation (or zero, if the animation is over).

## (scenery_animation_start \<scenery> \<animation_graph> \<string>)
starts a custom animation playing on a piece of scenery

## (scenery_animation_start_at_frame \<scenery> \<animation_graph> \<string> \<short>)
starts a custom animation playing on a piece of scenery at a specific frame

## (scenery_animation_start_relative \<scenery> \<animation_graph> \<string> \<object>)
starts a custom animation playing on a piece of scenery relative to a parent object

## (scenery_animation_idle \<scenery>)
starts the idle animation (if any) for a piece of scenery

## (render_effects \<boolean>)

## (debug_pvs \<boolean>)
displays the current pvs.

## (unit_can_blink \<unit> \<boolean>)
allows a unit to blink or not (units never blink when they are dead)

## (unit_open \<unit>)
opens the hatches on the given unit

## (unit_close \<unit>)
closes the hatches on a given unit

## (unit_kill \<unit>)
kills a given unit, no saving throw

## (unit_kill_silent \<unit>)
kills a given unit silently (doesn't make them play their normal death animation or sound)

## (unit_get_custom_animation_time \<unit>)
returns the number of ticks remaining in a unit's custom animation (or zero, if the animation is over).

## (unit_stop_custom_animation \<unit>)
stops the custom animation running on the given unit.

## (custom_animation \<unit> \<animation_graph> \<string> \<boolean>)
starts a custom animation playing on a unit (interpolates into animation if last parameter is TRUE)

## (custom_animation_relative \<unit> \<animation_graph> \<string> \<boolean> \<object>)
starts a custom animation relative to some other object (interpolates into animation if last parameter is TRUE)

## (custom_animation_list \<object_list> \<animation_graph> \<string> \<boolean>)
starts a custom animation playing on a unit list (interpolates into animation if last parameter is TRUE)

## (unit_set_actively_controlled \<unit> \<boolean>)
sets unit's actively controlled flag

## (unit_custom_animation_at_frame \<unit> \<animation_graph> \<string> \<boolean> \<short>)
starts a custom animation playing on a unit at a specific frame index(interpolates into animation if next to last parameter is TRUE)

## (unit_is_playing_custom_animation \<unit>)
returns TRUE if the given unit is still playing a custom animation

## (unit_aim_without_turning \<unit> \<boolean>)
allows a unit to aim in place without turning

## (unit_set_enterable_by_player \<unit> \<boolean>)
can be used to prevent the player from entering a vehicle

## (unit_enter_vehicle \<unit> \<vehicle> \<string>)
puts the specified unit in the specified vehicle (in the named seat)

## (unit_board_vehicle \<unit> \<string>)
Causes the given unit to attempt to board the named seat

## (unit_set_emotion \<unit> \<short>)
sets a unit's facial expression (-1 is none, other values depend on unit)

## (unit_set_emotion_animation \<unit> \<string>)
sets the emotion animation to be used for the given unit

## (unit_set_emotional_state \<unit> \<string> \<real> \<short>)
sets a unit's facial expression by name with weight and transition time

## (unit_enable_eye_tracking \<unit> \<boolean>)
enable/disable eye aiming on a unit

## (unit_in_vehicle \<unit>)
returns true if the given unit is seated on a parent unit

## (vehicle_test_seat_list \<vehicle> \<string> \<object_list>)
tests whether the named seat has an object in the object list (use "" to test all seats for any unit in the list)

## (vehicle_test_seat \<vehicle> \<string> \<unit>)
tests whether the named seat has a specified unit in it (use "" to test all seats for this unit)

## (unit_set_prefer_tight_camera_track \<unit> \<boolean>)
sets the unit to prefer a tight camera track

## (unit_exit_vehicle \<unit>)
makes a unit exit its vehicle

## (unit_exit_vehicle \<unit> \<short>)
makes a unit exit its vehicle (0 = normal exit to airborne, 1 = ejection, 2 = ejection + death, 3 = exit to ground)

## (unit_set_maximum_vitality \<unit> \<real> \<real>)
sets a unit's maximum body and shield vitality

## (units_set_maximum_vitality \<object_list> \<real> \<real>)
sets a group of units' maximum body and shield vitality

## (unit_set_current_vitality \<unit> \<real> \<real>)
sets a unit's current body and shield vitality

## (units_set_current_vitality \<object_list> \<real> \<real>)
sets a group of units' current body and shield vitality

## (vehicle_load_magic \<unit> \<string> \<object_list>)
makes a list of units (named or by encounter) magically get into a vehicle, in the substring-specified seats (e.g. CD-passenger... empty string matches all seats)

## (vehicle_unload \<unit> \<string>)
makes units get out of a vehicle from the substring-specified seats (e.g. CD-passenger... empty string matches all seats)

## (unit_set_animation_mode \<unit> \<string>)
this unit will assume the named animation mode

## (magic_melee_attack)
causes player's unit to start a melee attack

## (vehicle_riders \<unit>)
returns a list of all riders in a vehicle

## (vehicle_driver \<unit>)
returns the driver of a vehicle

## (vehicle_gunner \<unit>)
returns the gunner of a vehicle

## (unit_get_health \<unit>)
returns the health [0,1] of the unit, returns -1 if the unit does not exist

## (unit_get_shield \<unit>)
returns the shield [0,1] of the unit, returns -1 if the unit does not exist

## (unit_get_total_grenade_count \<unit>)
returns the total number of grenades for the given unit, 0 if it does not exist

## (unit_has_weapon \<unit> \<object_definition>)
returns TRUE if the \<unit> has \<object> as a weapon, FALSE otherwise

## (unit_has_weapon_readied \<unit> \<object_definition>)
returns TRUE if the \<unit> has \<object> as the primary weapon, FALSE otherwise

## (unit_lower_weapon \<unit> \<short>)
lower the units weapon over x ticks

## (unit_raise_weapon \<unit> \<short>)
raises the units weapon over x ticks

## (unit_animation_forced_seat \<string>)
all units controlled by the player will assume the given seat name (valid values are 'asleep', 'alert', 'stand', 'crouch' and 'flee')

## (unit_doesnt_drop_items \<object_list>)
prevents any of the given units from dropping weapons or grenades when they die

## (unit_impervious \<object_list> \<boolean>)
prevents any of the given units from being knocked around or playing ping animations

## (unit_suspended \<unit> \<boolean>)
stops gravity from working on the given unit

## (units_set_desired_flashlight_state \<object_list> \<boolean>)
sets the units' desired flashlight state

## (unit_set_desired_flashlight_state \<unit> \<boolean>)
sets the unit's desired flashlight state

## (unit_get_current_flashlight_state \<unit>)
gets the unit's current flashlight state

## (unit_add_equipment \<unit> \<starting_profile> \<boolean>)
adds/resets the unit's health, shield, and inventory (weapons and grenades) to the named profile. resets if third parameter is true, adds if false.

## (device_set_never_appears_locked \<device> \<boolean>)
changes a machine's never_appears_locked flag, but only if paul is a bastard

## (device_set_power \<device> \<real>)
immediately sets the power of a named device to the given value

## (device_get_power \<device>)
gets the current power of a named device

## (device_set_position \<device> \<real>)
set the desired position of the given device (used for devices without explicit device groups)

## (device_get_position \<device>)
gets the current position of the given device (used for devices without explicit device groups)

## (device_set_position_immediate \<device> \<real>)
instantaneously changes the position of the given device (used for devices without explicit device groups

## (device_group_get \<device_group>)
returns the desired value of the specified device group.

## (device_group_set \<device_group> \<real>)
changes the desired value of the specified device group.

## (device_group_set_immediate \<device_group> \<real>)
instantaneously changes the value of the specified device group.

## (device_one_sided_set \<device> \<boolean>)
TRUE makes the given device one-sided (only able to be opened from one direction), FALSE makes it two-sided

## (device_operates_automatically_set \<device> \<boolean>)
TRUE makes the given device open automatically when any biped is nearby, FALSE makes it not

## (device_group_change_only_once_more_set \<device_group> \<boolean>)
TRUE allows a device to change states only once

## (cheat_all_powerups)
drops all powerups near player

## (cheat_all_weapons)
drops all weapons near player

## (cheat_all_vehicles)
drops all vehicles on player

## (cheat_teleport_to_camera)
teleports player to camera location

## (cheat_active_camouflage)
gives the player active camouflage

## (cheat_active_camouflage_by_player \<short>)
gives a specific player active camouflage

## (cheats_load)
reloads the cheats.txt file

## (ai_enable \<boolean>)
turns all AI on or off.

## (ai_enabled)
returns whether AI is turned on or off.

## (ai_dialogue_triggers \<boolean>)
turns impromptu dialogue on or off.

## (ai_grenades \<boolean>)
turns grenade inventory on or off.

## (ai_get_object \<ai>)
returns the unit/object corresponding to the given actor

## (ai_get_unit \<ai>)
returns the unit/object corresponding to the given actor

## (ai_attach \<unit> \<ai>)
attaches the specified unit to the specified encounter.

## (ai_attach_units \<object_list> \<ai>)
attaches the specified list of units to the specified encounter.

## (ai_detach \<unit>)
detaches the specified unit from all AI.

## (ai_detach_units \<object_list>)
detaches the specified list of units from all AI.

## (ai_place \<ai>)
places the specified squad on the map.

## (ai_place \<ai> \<short>)
places the given number of members of the specified squad.

## (ai_place_in_vehicle \<ai> \<ai>)
places the specified squad (1st arg) on the map in the vehicles belonging to the specified vehicle squad (2nd arg).

## (ai_kill \<ai>)
instantly kills the specified encounter and/or squad.

## (ai_kill_silent \<ai>)
instantly and silently (no animation or sound played) kills the specified encounter and/or squad.

## (ai_erase \<ai>)
erases the specified encounter and/or squad.

## (ai_erase_all)
erases all AI.

## (ai_select \<ai>)
selects the specified squad.

## (ai_deselect)
clears the selected encounter.

## (ai_set_deaf \<ai> \<boolean>)
enables or disables hearing for actors in the specified encounter.

## (ai_set_blind \<ai> \<boolean>)
enables or disables sight for actors in the specified encounter.

## (ai_magically_see \<ai> \<ai>)
Make one squad magically aware of another.

## (ai_magically_see_object \<ai> \<object>)
Make a squad magically aware of a particular object.

## (ai_timer_start \<ai>)
makes a squad's delay timer start counting.

## (ai_timer_expire \<ai>)
makes a squad's delay timer expire and releases them to enter combat.

## (ai_migrate \<ai> \<ai>)
makes all or part of an encounter move to another encounter.

## (ai_allegiance \<team> \<team>)
creates an allegiance between two teams.

## (ai_allegiance_remove \<team> \<team>)
destroys an allegiance between two teams.

## (ai_braindead \<ai> \<boolean>)
makes a group of actors braindead, or restores them to life (in their initial state)

## (ai_braindead_by_unit \<object_list> \<boolean>)
makes a list of objects braindead, or restores them to life. if you pass in a vehicle index, it makes all actors in that vehicle braindead (including any built-in guns)

## (ai_disregard \<object_list> \<boolean>)
if TRUE, forces all actors to completely disregard the specified units, otherwise lets them acknowledge the units again

## (ai_prefer_target \<object_list> \<boolean>)
if TRUE, *ALL* enemies will prefer to attack the specified units. if FALSE, removes the preference.

## (ai_teleport_to_starting_location \<ai>)
teleports a group of actors to the starting locations of their current squad(s)

## (ai_teleport_to_starting_location_if_unsupported \<ai>)
teleports a group of actors to the starting locations of their current squad(s), only if they are not supported by solid ground (i.e. if they are falling after switching BSPs)

## (ai_renew \<ai>)
refreshes the health and grenade count of a group of actors, so they are as good as new

## (ai_force_active \<ai> \<boolean>)
forces an encounter to remain active (i.e. not freeze in place) even if there are no players nearby

## (ai_force_active_by_unit \<unit> \<boolean>)
forces a named actor that is NOT in an encounter to remain active (i.e. not freeze in place) even if there are no players nearby

## (ai_playfight \<ai> \<boolean>)
sets an encounter to be playfighting or not

## (ai_reconnect)
reconnects all AI information to the current structure bsp (use this after you create encounters or command lists in sapien, or place new firing points or command list points)

## (ai_vehicle_enterable_distance \<unit> \<real>)
sets a vehicle as being impulsively enterable for actors within a certain distance

## (ai_vehicle_enterable_team \<unit> \<team>)
sets a vehicle as being impulsively enterable for actors on a certain team

## (ai_vehicle_enterable_actor_type \<unit> \<actor_type>)
sets a vehicle as being impulsively enterable for actors of a certain type (grunt, elite, marine etc)

## (ai_vehicle_enterable_actors \<unit> \<ai>)
sets a vehicle as being impulsively enterable for a certain encounter/squad of actors

## (ai_vehicle_enterable_disable \<unit>)
disables actors from impulsively getting into a vehicle (this is the default state for newly placed vehicles) 

## (ai_look_at_object \<unit> \<object>)
tells an actor to look at an object until further notice

## (ai_stop_looking \<unit>)
tells an actor to stop looking at whatever it's looking at

## (ai_automatic_migration_target \<ai> \<boolean>)
enables or disables a squad as being an automatic migration target

## (ai_berserk \<ai> \<boolean>)
forces a group of actors to start or stop berserking

## (ai_set_team \<ai> \<team>)
makes an encounter change to a new team

## (ai_allow_dormant \<ai> \<boolean>)
either enables or disables automatic dormancy for a group of actors

## (ai_is_attacking \<ai>)
returns whether a platoon is in the attacking mode (or if an encounter is specified, returns whether any platoon in that encounter is attacking)

## (ai_fighting_count \<ai>)
return the number of actors that are fighting in a squad or squad_group

## (ai_living_count \<ai>)
return the number of living actors in the specified encounter and/or squad.

## (ai_living_fraction \<ai>)
return the fraction [0-1] of living actors in the specified encounter and/or squad.

## (ai_strength \<ai>)
return the current strength (average body vitality from 0-1) of the specified encounter and/or squad.

## (ai_swarm_count \<ai>)
return the number of swarm actors in the specified encounter and/or squad.

## (ai_nonswarm_count \<ai>)
return the number of non-swarm actors in the specified encounter and/or squad.

## (ai_actors \<ai>)
converts an ai reference to an object list.

## (ai_allegiance_broken \<team> \<team>)
returns whether two teams have an allegiance that is currently broken by traitorous behavior

## (ai_set_orders \<ai> \<ai_orders>)
Takes the squad or squad group (arg1) and gives it the order (arg3) in zone (arg2). Use the zone_name/order_name format

## (ai_spawn_count \<ai>)
returns the number of actors spawned in the given squad or squad group

## (ai_trigger_test \<string> \<ai>)
Tests the named trigger on the named squad

## (generate_pathfinding)
Generate pathfinding info for all structure bsps in the current scenario

## (ai_sectors_intersect \<long> \<long>)
Intersect two sectors (for debugging)

## (ai_sector_link_between \<long> \<long>)
Returns the link that connects the two given sectors

## (ai_render_paths_all)
Turns on raw, smoothed, avoided paths and avoidance obstacles

## (ai_vehicle_get \<ai>)
Returns the vehicle that the given actor is in.

## (ai_vehicle_get_from_starting_location \<ai>)
Returns the vehicle that was spawned at the given starting location.

## (ai_vehicle_reserve_seat \<vehicle> \<string> \<boolean>)
Reserves the given seat on the given vehicle (so that AI may not enter it

## (ai_vehicle_reserve \<vehicle> \<boolean>)
Reserves the given vehicle (so that AI may not enter it

## (ai_vehicle_enter \<ai> \<unit> \<string>)
tells a group of actors to get into a vehicle, in the substring-specified seats (e.g. passenger for pelican)... does not interrupt any actors who are already going to vehicles

## (ai_vehicle_enter \<ai> \<unit>)
tells a group of actors to get into a vehicle... does not interrupt any actors who are already going to vehicles

## (ai_vehicle_enter_immediate \<ai> \<unit> \<string>)
the given group of actors is snapped into a vehicle, in the substring-specified seats (e.g. passenger for pelican)... does not interrupt any actors who are already going to vehicles

## (ai_vehicle_enter_immediate \<ai> \<unit>)
the given group of actors is snapped into a vehicle

## (ai_vehicle_exit \<ai> \<string>)
tells a group of actors to get out of any vehicles that they are in (if their seat matches the substring)

## (ai_vehicle_exit \<ai>)
tells a group of actors to get out of any vehicles that they are in

## (vehicle_overturned \<vehicle>)
Returns true if the vehicle is overturned

## (vehicle_flip \<vehicle>)
Flips an overturned vehicle

## (ai_combat_status \<ai>)
Returns the highest integer combat status in the given squad-group/squad/actor

## (ai_verify_tags)
Verifies state of ai-related tags (e.g. orders, squads, zones, etc.)

## (ai_wall_lean \<ai>)
Makes the actor lean against a wall RIGHT NOW

## (cs_run_command_script \<ai> \<ai_command_script>)
Causes the specified actor(s) to start executing a command script immediately (discarding any other command scripts in the queue)

## (cs_queue_command_script \<ai> \<ai_command_script>)
Add a command script onto the end of an actor's command script queue

## (cs_stack_command_script \<ai> \<ai_command_script>)
Push a command script to the top of the actor's command script queue

## (cs_run_joint_command_script \<ai_command_script> \<ai> \<ai>)
Causes the specified actor(s) to start executing a command script immediately (discarding any other command scripts in the queue)

## (cs_run_joint_command_script \<ai_command_script> \<ai> \<ai> \<ai>)
Causes the specified actor(s) to start executing a command script immediately (discarding any other command scripts in the queue)

## (cs_command_script_running \<ai> \<ai_command_script>)
Returns true if the ai is running the command script in question

## (cs_command_script_queued \<ai> \<ai_command_script>)
Returns true if the command script is in the ai's cs queue

## (cs_number_queued \<ai>)
Returns the number of queued command scripts

## (cs_switch \<short>)
Switch control of the joint command script to the given member

## (cs_transfer \<ai>)
Transfer control of the command script to the given actor (replacing what he has)

## (cs_transfer_stack \<ai>)
Transfer control of the command script to the given actor (stacking it)

## (cs_transfer_queue \<ai>)
Transfer control of the command script to the given actor (queueing it)

## (cs_fly_to \<point reference>)
Flies the actor to the given point

## (cs_fly_to \<point reference> \<real>)
Flies the actor to the given point (within the given tolerance)

## (cs_fly_to_and_face \<point reference> \<point reference>)
Flies the actor to the given point and orients him in the appropriate direction

## (cs_fly_to_and_face \<point reference> \<point reference> \<real>)
Flies the actor to the given point and orients him in the appropriate direction (within the given tolerance)

## (cs_fly_by \<point reference>)
Flies the actor through the given point

## (cs_fly_by \<point reference> \<real>)
Flies the actor through the given point (within the given tolerance)

## (cs_go_to \<point reference>)
Moves the actor to a specified point

## (cs_go_to \<point reference> \<real>)
Moves the actor to a specified point, attenuating throttle by the given amount when near the goal

## (cs_go_by \<point reference> \<point reference>)
Actor moves toward the point, and considers it hit when it breaks the indicated plane

## (cs_go_by \<point reference> \<point reference> \<real>)
Actor moves toward the point, and considers it hit when it breaks the indicated plane, attenuating throttle by the given amount when near the goal

## (cs_go_to_and_face \<point reference> \<point reference>)
Moves the actor to a specified point and has him face the second point

## (cs_look \<boolean> \<point reference>)
Actor looks at the point for the remainder of the cs, or until overridden

## (cs_look_player \<boolean>)
Actor looks at nearest player for the duration of the cs, or until overridden

## (cs_look_object \<boolean> \<object>)
Actor looks at the object for the duration of the cs, or until overridden

## (cs_aim \<boolean> \<point reference>)
Actor aims at the point for the remainder of the cs, or until overridden (overrides look)

## (cs_aim_player \<boolean>)
Actor aims at nearest player for the duration of the cs, or until overridden (overrides look)

## (cs_aim_object \<boolean> \<object>)
Actor aims at the object for the duration of the cs, or until overridden (overrides look)

## (cs_face \<boolean> \<point reference>)
Actor faces exactly the point for the remainder of the cs, or until overridden (overrides aim, look)

## (cs_face_player \<boolean>)
Actor faces exactly the nearest player for the duration of the cs, or until overridden (overrides aim, look)

## (cs_face_object \<boolean> \<object>)
Actor faces exactly the given object for the duration of the cs, or until overridden (overrides aim, look)

## (cs_move_in_direction \<real> \<real> \<real>)
Actor moves at given angle, for the given distance, optionally with the given facing (angle, distance, facing)

## (cs_pause \<real>)
The actor does nothing for the given number of seconds

## (cs_shoot \<boolean>)
Actor is allowed to shoot at its target or not

## (cs_shoot \<boolean> \<object>)
Actor shoots at given target

## (cs_shoot_point \<boolean> \<point reference>)
Actor shoots at given point

## (cs_vehicle_speed \<real>)
Set the speed at which the actor will drive a vehicle, expressed as a multiplier 0-1

## (cs_grenade \<point reference> \<short>)
Actor throws a grenade, either by tossing (arg2=0), lobbing (1) or bouncing (2)

## (cs_jump \<real> \<real>)
Actor jumps in direction of angle at the given velocity (angle, velocity)

## (cs_jump_to_point \<real> \<real>)
Actor jumps with given horizontal and vertical velocity

## (cs_vocalize \<short>)
Actor emits vocalization of given type

## (cs_play_sound \<sound>)
Actor plays an impulse sound

## (cs_play_sound \<sound> \<real>)
Actor plays an impulse sound and the atom blocks for the given percentage of the sound's total length

## (cs_play_sound \<sound> \<real> \<real>)
Actor plays an impulse sound and the atom blocks for the given percentage of the sound's total length, at the given volume (0..1)

## (cs_stop_sound \<sound>)
Stops the specified impulse sound.

## (cs_custom_animation \<animation_graph> \<string> \<real> \<boolean>)
starts a custom animation playing on the unit (interpolates into animation if last parameter is TRUE)

## (cs_stop_custom_animation)
Stop running a custom animation

## (cs_die \<short>)
Actor dies in specified manner

## (cs_teleport \<point reference> \<point reference>)
Actor teleports to point1 facing point2

## (cs_animate \<long> \<short>)
Actor performs animation with given modifier (anim-ref, modifier)

## (cs_animation_mode \<short>)
Actor switches to given animation mode

## (cs_crouch \<boolean>)
Actor crouches for the remainder of the command script, or until overridden

## (cs_set_pathfinding_radius \<real>)
Sets the actor's pathfinding radius (this distance at which a destination is considered to have been reached) for the remainder of the command script

## (cs_go_to_vehicle \<vehicle>)
Actor gets in the appropriate vehicle

## (cs_set_behavior \<ai_behavior>)
Actor performs the indicated behavior

## (cs_formation \<short> \<ai> \<point reference> \<point reference>)
Actor initiates a formation of the given type at the given point, facing (initially) at the given other point. Formation types are (0) 1x column (1) 2x column ... (4) wall (5) wedge.

## (cs_ignore_obstacles \<boolean>)
Actor does not avoid obstacles when true

## (cs_turn_sharpness \<boolean> \<real>)
Set the sharpness of a vehicle turn (values 0 -> 1). Only applicable to nondirectional flying vehicles (e.g. dropships)

## (cs_vehicle_speed_instantaneous \<real>)
Set the instantaneous speed of the vehicle we're driving

## (cs_abort_on_alert \<boolean>)
Command script ends prematurely when actor's combat status raises to 'alert' or higher

## (cs_abort_on_damage \<boolean>)
Command script ends prematurely when actor is damaged

## (cs_enable_targeting \<boolean>)
Actor autonomous target selection disabled.

## (cs_enable_looking \<boolean>)
Actor autonomous looking disabled.

## (cs_enable_moving \<boolean>)
Actor autonomous moving disabled.

## (cs_set_style \<style>)
Override the actor's style

## (cs_force_combat_status \<short>)
Force the actor's combat status (0= no override, 1= asleep, 2=idle, 3= alert, 4= active)

## (cs_enable_pathfinding_failsafe \<boolean>)
Actor blocks until pathfinding calls succeed

## (camera_control \<boolean>)
toggles script control of the camera.

## (camera_set \<cutscene_camera_point> \<short>)
moves the camera to the specified camera point over the specified number of ticks.

## (camera_set_relative \<cutscene_camera_point> \<short> \<object>)
moves the camera to the specified camera point over the specified number of ticks (position is relative to the specified object).

## (camera_set_animation \<animation_graph> \<string>)
begins a prerecorded camera animation.

## (camera_set_animation_relative \<animation_graph> \<string> \<unit> \<cutscene_flag>)
begins a prerecorded camera animation synchronized to unit relative to cutscene flag.

## (camera_set_first_person \<unit>)
makes the scripted camera follow a unit.

## (camera_set_dead \<unit>)
makes the scripted camera zoom out around a unit as if it were dead.

## (camera_place_relative \<object>)
all subsequent camera placement in sapien be marked as relative to this object

## (camera_place_worldspace)
all subsequent camera placement in sapien will be marked as worldspace

## (camera_time)
returns the number of ticks remaining in the current camera interpolation.

## (camera_set_field_of_view \<real>)
sets the field of view

## (debug_camera_save)
saves the camera position and facing.

## (debug_camera_load)
loads the saved camera position and facing.

## (debug_camera_save_name \<string>)
saves the camera position and facing to filename

## (debug_camera_load_name \<string>)
loads the camera position and facing from filename

## (director_debug_camera \<boolean>)
enable/disable camera debugging

## (camera_set_pan \<cutscene_camera_point> \<short>)
moves the camera to the specified camera point over the specified number of ticks with a constant speed.

## (camera_pan \<cutscene_camera_point> \<cutscene_camera_point> \<short> \<short> \<real> \<short> \<real>)
camera_pan \<start point> \<end point> \<ticks> \<ease-in ticks> \<start velocity scale> \<ease-out ticks> \<end velocity scale>

## (camera_predict \<cutscene_camera_point>)
predictes resources given a camera view

## (game_time)
gets ticks elapsed since the start of the game.

## (game_difficulty_get)
returns the current difficulty setting, but lies to you and will never return easy, instead returning normal

## (game_difficulty_get_real)
returns the actual current difficulty setting without lying

## (pvs_set_object \<object>)
sets the specified object as the special place that activates everything it sees.

## (pvs_set_camera \<cutscene_camera_point>)
sets the specified cutscene camera point as the special place that activates everything it sees.

## (pvs_clear)
removes the special place that activates everything it sees.

## (players_unzoom_all)
resets zoom levels on all players

## (player_enable_input \<boolean>)
toggle player input. the player can still free-look, but nothing else.

## (player_camera_control \<boolean>)
enables/disables camera control globally

## (player_action_test_reset)
resets the player action test state so that all tests will return false.

## (player_action_test_jump)
returns true if any player has jumped since the last call to (player_action_test_reset).

## (player_action_test_primary_trigger)
returns true if any player has used primary trigger since the last call to (player_action_test_reset).

## (player_action_test_grenade_trigger)
returns true if any player has used grenade trigger since the last call to (player_action_test_reset).

## (player_action_test_zoom)
returns true if any player has hit the zoom button since the last call to (player_action_test_reset).

## (player_action_test_rotate_weapons)
returns true if any player has hit the rotate-weapon button since the last call to (player_action_test_reset).

## (player_action_test_rotate_grenades)
returns true if any player has hit the rotate-grenades button since the last call to (player_action_test_reset).

## (player_action_test_action)
returns true if any player has hit the action key since the last call to (player_action_test_reset).

## (player_action_test_accept)
returns true if any player has hit accept since the last call to (player_action_test_reset).

## (player_action_test_cancel)
returns true if any player has hit cancel key since the last call to (player_action_test_reset).

## (player_action_test_look_relative_up)
returns true if any player has looked up since the last call to (player_action_test_reset).

## (player_action_test_look_relative_down)
returns true if any player has looked down since the last call to (player_action_test_reset).

## (player_action_test_look_relative_left)
returns true if any player has looked left since the last call to (player_action_test_reset).

## (player_action_test_look_relative_right)
returns true if any player has looked right since the last call to (player_action_test_reset).

## (player_action_test_look_relative_all_directions)
returns true if any player has looked up, down, left, and right since the last call to (player_action_test_reset).

## (player_action_test_move_relative_all_directions)
returns true if any player has moved forward, backward, left, and right since the last call to (player_action_test_reset).

## (player_action_test_start)
returns true if any player has pressed the start button since the last call to (player_action_test_reset).

## (player_action_test_back)
returns true if any player has pressed the back button since the last call to (player_action_test_reset).

## (debug_teleport_player \<long> \<long>)
for testing: teleports one player to another's location

## (map_reset)
starts the map from the beginning.

## (switch_bsp \<short>)
takes off your condom and changes to a different structure bsp

## (switch_bsp_by_name \<string>)
leaves your condom on and changes to a different structure bsp by name

## (structure_bsp_index)
returns the current structure bsp index

## (crash \<string>)
crashes (for debugging).

## (version)
prints the build version.

## (status)
prints the value of all global status variables.

## (record_movie \<short> \<long> \<short>)
\<frame rate> \<seconds> \<screen size>

## (record_movie_distributed \<short> \<long> \<short> \<long> \<long>)
\<frame rate> \<seconds> \<screen size> \<mod count> \<mod index>

## (screenshot \<string>)
takes a screenshot and saves as \<name>.tif

## (screenshot_big \<short> \<string>)
takes an NxN multiple-page screenshot and saves as \<name>.tif

## (screenshot_big_jittered \<short> \<string>)
takes an NxN subpixel sampled 640x480 screenshot and saves as \<name>.tif

## (screenshot_cubemap \<string>)
takes a cubemap screenshot and saves as \<name>.tif

## (main_menu)
goes back to the main menu

## (main_halt)
goes to a halted pregame state

## (map_name \<string>)
the same as game_start: launches a game for debugging purposes

## (game_multiplayer \<string>)
debug map launching: sets the multiplayer variant for the next map.

## (game_splitscreen \<long>)
debug map launching: sets the number of multiplayer splitscreen players for the next map.

## (game_difficulty \<game_difficulty>)
debug map launching: sets the difficulty of the next map.

## (game_coop_players \<long>)
debug map launching: sets the number of coop players for the next map.

## (game_initial_bsp \<long>)
debug map launching: sets the initial bsp for the next map.

## (game_start \<string>)
debug map launching: starts a game on the specified map.

## (texture_cache_flush)

## (geometry_cache_flush)

## (sound_cache_flush)

## (debug_memory)
dumps memory leaks.

## (debug_memory_by_file)
dumps memory leaks by source file.

## (debug_memory_for_file \<string>)
dumps memory leaks from the specified source file.

## (debug_tags)
writes all memory being used by tag files into tag_dump.txt

## (tags_verify_all)
verifies usage of infidel fields is correct

## (profile_reset)
resets profiling data.

## (profile_activate \<string>)
activates profile sections based on a substring.

## (profile_deactivate \<string>)
deactivates profile sections based on a substring.

## (profile_mode \<string>)
sets the current profiling mode.

## (damage_control_get \<string>)
gets a damage control setting by string

## (damage_control_set \<string> \<boolean>)
sets a damage control setting by string

## (ai_lines)
cycl## es through AI line-spray modes

## (ai_debug_sound_point_set)
drops the AI debugging sound point at the camera location

## (ai_debug_vocalize \<string> \<string>)
makes the selected AI vocalize

## (ai_debug_teleport_to \<string>)
teleports all players to the specified zone

## (ai_debug_speak \<string>)
makes the currently selected AI speak a vocalization (e.g. ai_speak "pain minor")

## (ai_debug_speak_list \<string>)
makes the currently selected AI speak a list of vocalizations (e.g. ai_speak_list "involuntary")

## (fade_in \<real> \<real> \<real> \<short>)
does a screen fade in from a particular color

## (fade_out \<real> \<real> \<real> \<short>)
does a screen fade out to a particular color

## (cinematic_start)
initializes game to start a cinematic (interruptive) cutscene

## (cinematic_stop)
initializes the game to end a cinematic (interruptive) cutscene

## (cinematic_skip_start_internal)

## (cinematic_skip_stop_internal)

## (cinematic_show_letterbox \<boolean>)
sets or removes the letterbox bars

## (cinematic_set_title \<cutscene_title>)
activates the chapter title

## (cinematic_set_title_delayed \<cutscene_title> \<real>)
activates the chapter title, delayed by \<real> seconds

## (cinematic_suppress_bsp_object_creation \<boolean>)
suppresses or enables the automatic creation of objects during cutscenes due to a bsp switch

## (cinematic_dolly_start \<object> \<string>)
lock dolly-zoom onto object marker

## (cinematic_dolly_stop \<real>)
unlock dolly-zoom \<seconds>

## (cinematic_subtitle \<string> \<real>)
lock dolly-zoom onto object marker

## (attract_mode_start)
starts an attract mode movie

## (game_won)
causes the player to successfully finish the current level and move to the next

## (game_lost)
causes the player to revert to his previous saved game

## (game_is_cooperative)
returns TRUE if the game is cooperative

## (game_skip_ticks \<long>)
skips some amount of game ticks. only usable in cutscenes, for durations less than 1/2 second.

## (game_revert)
reverts to last saved game, if any (for testing, the first bastard that does this to me gets it in the head)

## (game_save_unsafe)
saves right now, even if the game is in an immediate-loss state (NEVER USE THIS! EVER!)

## (debug_spawning \<string> \<boolean>)
debugs spawn points for the inputted player

## (king_set_hill \<long>)
sets which index the active hill should be

## (headhunter_set_bin \<long>)
sets which index the active hill should be

## (core_load)
loads debug game state from core\core.bin

## (core_load_name \<string>)
loads debug game state from core\\\<path>

## (core_save)
saves debug game state to core\core.bin

## (core_save_name \<string>)
saves debug game state to core\\\<path>

## (core_load_game)
loads level and game state from core\core.bin

## (core_load_game_name \<string>)
loads level and game state from core\\\<path>

## (core_regular_upload_to_debug_server \<boolean>)
toggle periodic core uploading to debug server

## (core_upload)
saves the game state to disk core\core.bin and uploads it to the debug server

## (core_upload_name \<string>)
saves the game state to disk core\\\<path> and uploads it to the debug server

## (core_set_upload_option \<string>)
sets options for game state uploading (current options are 'default', 'repro', and 'stress'

## (game_safe_to_save)
returns FALSE if it would be a bad idea to save the player's game right now

## (game_all_quiet)
returns FALSE if there are bad guys around, projectiles in the air, etc.

## (game_safe_to_speak)
returns FALSE if it would be a bad idea to save the player's game right now

## (game_save)
checks to see if it is safe to save game, then saves (gives up after 8 seconds)

## (game_save_cancel)
cancels any pending game_save, timeout or not

## (game_save_no_timeout)
checks to see if it is safe to save game, then saves (this version never gives up)

## (game_save_immediate)
disregards player's current situation and saves (BE VERY CAREFUL!)

## (game_saving)
checks to see if the game is trying to save the map.

## (game_reverted)

## (sound_impulse_predict \<sound>)

## (sound_impulse_trigger \<sound> \<object> \<real> \<long>)
plays an impulse sound from the specified source object (or "none"), with the specified scale.

## (sound_impulse_start \<sound> \<object> \<real>)
plays an impulse sound from the specified source object (or "none"), with the specified scale.

## (sound_impulse_start_cinematic \<sound> \<object> \<real> \<real> \<real>)
\<sound> \<object> \<scale> \<3d gain> \<first person gain> plays an impulse sound from the specified source object.

## (sound_impulse_start_effect \<sound> \<object> \<real> \<string>)
plays an impulse sound from the specified source object (or "none"), with the specified scale and effect.

## (sound_impulse_time \<sound>)
returns the time remaining for the specified impulse sound.

## (sound_impulse_stop \<sound>)
stops the specified impulse sound.

## (sound_looping_predict \<looping_sound>)

## (sound_looping_start \<looping_sound> \<object> \<real>)
plays a looping sound from the specified source object (or "none"), with the specified scale.

## (sound_looping_stop \<looping_sound>)
stops the specified looping sound.

## (sound_looping_stop_immediately \<looping_sound>)
stops the specified looping sound immediately.

## (sound_looping_set_scale \<looping_sound> \<real>)
changes the scale of the sound (which should affect the volume) within the range 0 to 1.

## (sound_looping_set_alternate \<looping_sound> \<boolean>)
enables or disables the alternate loop/alternate end for a looping sound.

## (sound_loop_spam)
start all loaded looping sounds

## (sound_class_show_channel \<string> \<boolean>)
shows/hides sound classes w/ substring in debug_sound_channels view

## (sound_class_debug_sound_start \<string> \<boolean>)
shows/hides when sounds of sound classes w/ substring start

## (debug_sounds_enable \<string> \<boolean>)
enables or disables all sound classes matching the substring.

## (sound_class_set_gain \<string> \<real> \<short>)
changes the gain on the specified sound class(es) to the specified gain over the specified number of ticks.

## (sound_class_set_gain_db \<string> \<real> \<short>)
changes the gain on the specified sound class(es) to the specified gain(dB) over the specified number of ticks.

## (sound_class_enable_ducker \<string> \<boolean>)
enables or disables the ducker on all sound classes matching the substring.

## (debug_sound_environment_parameter \<long> \<real>)

## (sound_set_global_effect \<string> \<real>)

## (sound_set_global_effect_scale \<string> \<real>)

## (vehicle_hover \<vehicle> \<boolean>)
stops the vehicle from running real physics and runs fake hovering physics instead. 

## (vehicle_count_bipeds_killed \<vehicle>)
returns how many people this vehicle has killed

## (show_hud \<boolean>)
shows or hides the hud

## (show_hud_help_text \<boolean>)
shows or hides the hud help text

## (show_hud_messages \<boolean>)
shows or hides the hud messages

## (enable_hud_help_flash \<boolean>)
starts/stops the help text flashing

## (hud_help_flash_restart)
resets the timer for the help text flashing

## (activate_nav_point_flag \<navpoint> \<unit> \<cutscene_flag> \<real>)
activates a nav point type \<string> attached to (local) player \<unit> anchored to a flag with a vertical offset \<real>. If the player is not local to the machine, this will fail

## (activate_nav_point_object \<navpoint> \<unit> \<object> \<real>)
activates a nav point type \<string> attached to (local) player \<unit> anchored to an object with a vertical offset \<real>. If the player is not local to the machine, this will fail

## (activate_team_nav_point_flag \<navpoint> \<team> \<cutscene_flag> \<real>)
activates a nav point type \<string> attached to a team anchored to a flag with a vertical offset \<real>. If the player is not local to the machine, this will fail

## (activate_team_nav_point_object \<navpoint> \<team> \<object> \<real>)
activates a nav point type \<string> attached to a team anchored to an object with a vertical offset \<real>. If the player is not local to the machine, this will fail

## (deactivate_nav_point_flag \<unit> \<cutscene_flag>)
deactivates a nav point type attached to a player \<unit> anchored to a flag

## (deactivate_nav_point_object \<unit> \<object>)
deactivates a nav point type attached to a player \<unit> anchored to an object

## (deactivate_team_nav_point_flag \<team> \<cutscene_flag>)
deactivates a nav point type attached to a team anchored to a flag

## (deactivate_team_nav_point_object \<team> \<object>)
deactivates a nav point type attached to a team anchored to an object

## (cls)
clears console text from the screen

## (error_overflow_suppression \<boolean>)
enables or disables the suppression of error spamming

## (error_geometry_show \<string>)
highlights all error geometry with a name that includes the given substring

## (error_geometry_hide \<string>)
hides all error geometry with a name that includes the given substring

## (error_geometry_show_all)
highlights all error geometry

## (error_geometry_hide_all)
hides all error geometry

## (error_geometry_list)
prints out a list of all error geometry types and counts

## (player_effect_set_max_translation \<real> \<real> \<real>)
\<x> \<y> \<z>

## (player_effect_set_max_rotation \<real> \<real> \<real>)
\<yaw> \<pitch> \<roll>

## (player_effect_set_max_rumble \<real> \<real>)
\<left> \<right>

## (player_effect_start \<real> \<real>)
\<max_intensity> \<attack time>

## (player_effect_stop \<real>)
\<decay>

## (hud_show_health \<boolean>)
hides/shows the health panel

## (hud_blink_health \<boolean>)
starts/stops manual blinking of the health panel

## (hud_show_shield \<boolean>)
hides/shows the shield panel

## (hud_blink_shield \<boolean>)
starts/stops manual blinking of the shield panel

## (hud_show_motion_sensor \<boolean>)
hides/shows the motion sensor panel

## (hud_blink_motion_sensor \<boolean>)
starts/stops manual blinking of the motion sensor panel

## (hud_show_crosshair \<boolean>)
hides/shows the weapon crosshair

## (hud_show_ammo \<boolean>)
hides/shows the weapon/grenade ammo counter

## (hud_clear_messages)
clears all non-state messages on the hud

## (hud_set_help_text \<hud_message>)
displays \<message> as the help text

## (hud_set_objective_text \<hud_message>)
sets \<message> as the current objective

## (hud_set_timer_time \<short> \<short>)
sets the time for the timer to \<short> minutes and \<short> seconds, and starts and displays timer

## (hud_set_timer_warning_time \<short> \<short>)
sets the warning time for the timer to \<short> minutes and \<short> seconds

## (hud_set_timer_position \<short> \<short> \<hud_corner>)
sets the timer upper left position to (x, y)=>(\<short>, \<short>)

## (show_hud_timer \<boolean>)
displays the hud timer

## (pause_hud_timer \<boolean>)
pauses or unpauses the hud timer

## (hud_get_timer_ticks)
returns the ticks left on the hud timer

## (time_code_show \<boolean>)
shows the time code timer

## (time_code_start \<boolean>)
starts/stops the time code timer

## (time_code_reset)
resets the time code timer

## (rasterizer_profile_include \<string>)

## (rasterizer_profile_include_all)

## (rasterizer_profile_include_all_except \<string>)

## (rasterizer_profile_exclude \<string>)

## (rasterizer_profile_exclude_all)

## (rasterizer_profile_exclude_all_except \<string>)

## (rasterizer_artist_profile \<long>)
used to turn on artist profile modes 0-disabled, 1-simple mode, 2-detailed mode

## (rasterizer_debug_display_bitmap \<string>)
displays a bitmap

## (rasterizer_decals_flush)
flush all decals

## (rasterizer_lens_flares_reset_for_new_map)

## (decorator_debug_set_filter \<long> \<long> \<long>)

## (decorator_debug_precision_add)

## (decorator_debug_density_erase)

## (decorator_debug_density_low)

## (decorator_debug_density_high)

## (script_screen_effect_set_value \<short> \<real>)
sets a screen effect script value

## (cinematic_screen_effect_start \<boolean>)
starts screen effect pass TRUE to clear

## (cinematic_screen_effect_set_convolution \<short> \<short> \<real> \<real> \<real>)
sets the convolution effect

## (cinematic_screen_effect_set_filter \<real> \<real> \<real> \<real> \<boolean> \<real>)
sets the filter effect

## (cinematic_screen_effect_set_filter_desaturation_tint \<real> \<real> \<real>)
sets the desaturation filter tint color

## (cinematic_screen_effect_set_video \<short> \<real>)
sets the video effect: \<noise intensity[0,1]>, \<overbright: 0=none, 1=2x, 2=4x>

## (cinematic_screen_effect_set_depth_of_field \<real> \<real> \<real> \<real> \<real> \<real> \<real>)
sets dof: \<seperation dist>, \<near blur lower bound> \<upper bound> \<time> \<far blur lower bound> \<upper bound> \<time>

## (cinematic_screen_effect_set_bloom \<real> \<real> \<real> \<real> \<real>)
blur threshold overbright tint modulation

## (bloom \<real> \<real> \<real>)
new brightness, new overbrightness, delta time

## (cinematic_bloom \<real> \<real> \<real>)
new brightness, new overbrightness, delta time

## (cinematic_screen_effect_set_bloom_transition \<real> \<real> \<real> \<real> \<real> \<real>)
blur threshold overbright tint modulation transition-time

## (cinematic_screen_effect_set_bloom_threshold_color \<real> \<real> \<real>)
red green blue

## (cinematic_screen_effect_set_bloom_overbright_color \<real> \<real> \<real>)
red green blue

## (cinematic_screen_effect_set_bloom_tint_color \<real> \<real> \<real>)
red green blue

## (cinematic_screen_effect_set_bloom_modulation_color \<real> \<real> \<real>)
red green blue

## (cinematic_screen_effect_set_crossfade \<real>)
transition-time

## (cinematic_screen_effect_set_crossfade2 \<real> \<real>)
transition-time, exponent

## (cinematic_screen_effect_stop)
returns control of the screen effects to the rest of the game

## (cinematic_set_near_clip_distance \<real>)

## (cinematic_set_far_clip_distance \<real>)

## (cinematic_set_environment_map_attenuation \<real> \<real> \<real>)
interpolates environment-map attenuation (on flagged shaders) from \<low> to \<high> over \<time>

## (cinematic_set_environment_map_bitmap \<bitmap>)
sets environment-map bitmap (on flagged shaders) instantly

## (cinematic_reset_environment_map_bitmap)
resets environment-map bitmap (on flagged shaders) to default instantly

## (cinematic_set_environment_map_tint \<real> \<real> \<real> \<real> \<real> \<real> \<real> \<real>)
perpendicular color: (red green blue brightness), parallel color: (red green blue brightness)... sets environment-map tint (on flagged shaders) instantly

## (cinematic_reset_environment_map_tint)
resets environment-map tint (on flagged shaders) to default instantly

## (cinematic_layer \<long> \<real> \<real>)
interpolates the value of \<cinematic layer x> from current position to \<value> over \<time>

## (cinematic_dynamic_reflections \<boolean> \<boolean>)
sets up dynamic reflections: \<enabled: [true, false]> \<filtering enabled: [true, false]>

## (lightmaps_expose \<real> \<real> \<real>)
re-exposes the lightmap palettes

## (create_player_profile \<string> \<short> \<short> \<boolean>)
create a player profile

## (controller_invert_look)
invert look on all attached controllers

## (controller_look_speed \<short>)
set look speed for all attached controllers

## (ui_debug_load_main_menu)
loads the main menu screen

## (ui_debug_text_bounds \<boolean>)
toggle rendering of widget text boundaries

## (ui_debug_show_title_safe_bounds \<boolean>)
toggle display of title safe boundary

## (ui_dispose)
dispose of halo2 gameshell ui

## (ui_debug_screen_tag \<string>)
test a ui screen

## (ui_transition_out_console_window)
transition out any ui on the console window

## (ui_debug_show_screen_tag_path \<boolean>)
display tag path of screens as they load

## (ui_set_beta \<boolean>)
set ui beta testing on/off

## (ui_set_automation_mode \<short>)
set ui automation mode

## (ui_set_automation_hopper_type \<short>)
set ui / mp automation hopper

## (ui_set_automation_desired_local_user_count \<short>)
set ui / mp automation desired local user count

## (ui_set_automation_desired_desired_network_game_player_count \<short>)
set ui / mp automation desired network game player count

## (ui_set_automation_desired_network_game_length_seconds \<long>)
set ui / mp automation desired game time length

## (ui_set_automation_desired_network_session_name \<string>)
set ui / mp automation desired session name

## (ui_set_automation_desired_controller_team \<short> \<short>)
set desired mp team for a controller

## (ui_set_automation_desired_controller_player_profile \<short> \<string> \<string> \<boolean>)
set desired player profile and gamertag for a controller

## (input_suppress_rumble \<boolean>)
disable the friggin' rumble

## (update_remote_camera)
force synchronization of remote machine camera

## (net_status_filter \<string>)
filters the set of network status to display

## (net_sim_reset)
network simulation: resets the simulation state

## (net_sim_spike_now)
network simulation: starts a latency spike immediately

## (net_sim_dropspike_now)
network simulation: starts a packet loss spike immediately

## (net_test_ping)
network test: sends a ping

## (net_test_channel_loopback)
network test: creates loopback channels

## (net_test_channel_delete)
network test: deletes all channels

## (net_test_leave_squad)
network test: leave current squad

## (net_test_delegate_leader \<long>)
network test: delegate leadership to the specified player

## (net_test_map_name \<string>)
network test: sets the name of the scenario to play

## (net_test_player_color \<long>)
network test: temporarily sets the color for all local players

## (net_test_reset_objects)
network test: resets all objects on the map

## (net_set_machine_name \<string>)
sets the nickname of your xbox

## (net_event_display_category \<string> \<network_event>)
sets the display level for a named category of network events

## (net_event_log_category \<string> \<network_event>)
sets the log level for a named category of network events

## (net_event_list_categories \<string>)
lists all categories that exist under a particular category string

## (net_test_create_group_session)
network test: create group session

## (net_test_matchmaking_initiate)
network test: initiate matchmaking

## (net_test_matchmaking_abort)
network test: abort the matchmaking process

## (play_bink_movie \<string>)

## (set_global_doppler_factor \<real>)
new doppler factor: \<real>

## (set_global_mixbin_headroom \<long> \<long>)

## (data_mine_insert \<string>)
insert text and camera position in the data mine

## (data_mine_upload)
upload all data mining data files to debug server

## (data_mine_playback \<string>)
loads and displays data mine data from a file

## (data_mine_playback_last)
loads and displays last data mine data

## (data_mine_playback_exit)
exit data visualization

## (data_mine_enable \<boolean>)
enable/disable data mining

## (data_mine_track_event \<string>)
enable mining of an event

## (data_mine_display_event \<string>)
enable displaying of an event

## (data_mine_show_all_events)
show all data mine events

## (data_mine_show_tracked_events)
show what events are being tracked by the data mine

## (data_mine_show_displayed_events)
show what events are being displayed by the data mine

## (data_mine_display_session_data)
show data mine session, game, and network ids

## (data_mine_display_disk_writes \<boolean>)
enable/disable console message on disk writes

## (error_enable \<string> \<boolean>)
enables/disables display for a class of errors

## (render_layer_enable \<string> \<boolean>)
enable/disables a render_layer

## (render_layer_enable_all \<boolean>)
enable/disables all render_layers

## (rasterizer_overdraw_z)
toggles overdraw with z compare on

## (rasterizer_overdraw)
toggles overdraw with z compare off

## (test_memory_allocators \<long> \<short> \<short> \<short> \<long>)
performs tests on different memory allocators

## (test_memory_allocators \<long> \<short> \<short> \<short> \<long> \<string>)
performs tests on different memory allocators and saves the results

## (test_xcr_monkey_enable \<boolean>)
enable/disable controller monkeys for all in game players

## (test_web_map_snapshot \<string>)
takes two special screenshots and saves them, along with the camera information, as \<name>.tif, \<name>_secondary.tif and \<name>_camera.txt

## (test_telnet_status_enable \<boolean>)
enable/disable status events being sent to the telnet console

## (test_telnet_status_interval \<long>)
sets the interval that status events are sent to the telnet console.

## (script_temporary_disable_lightmap_shadows \<boolean>)
disable lightmap shadows

## (flag_new \<string> \<string>)
\<name> \<description>

## (flag_new_at_look \<string> \<string>)
\<name> \<description>

## (flags_clear)
erases all comment flags when not in editor (sapien)

## (flags_save)
dump comment flags to vrml file

## (flags_save_filtered \<string>)
\<substring filter>

## (flags_save_named \<string>)
\<file name>

## (flags_save_named_filtered \<string> \<string>)
\<filter string> \<file name>

## (flags_default_name \<string>)
\<default comment flag name>

## (flags_default_comment \<string>)
\<default comment flag description>

## (flags_set_filter \<string>)
\<flag name filter>

## (flags_export)
dump comment flags to a .txt file

## (flags_export_filtered \<string>)
\<substring filter>

## (flags_export_named \<string>)
\<file name>

## (flags_export_named_filtered \<string> \<string>)
\<filter string> \<file name> 
