---
title: Halo 3 Haloscript Overview #Required; page title is displayed in search results. Include the brand.
description: Haloscript Overview for Halo 3 Modding Documentation. #Required; article description that is displayed in search results. 
author: mjordan343 #Required; your GitHub user alias, with correct capitalization.
ms.author: mjordan #Required; microsoft alias of author; optional team alias.
ms.service: halo-mcc #Required; service per approved list. slug assigned by ACOM.
ms.topic: quickstart #Required; leave this attribute/value as-is.
ms.date: 03/21/2022 #Required; mm/dd/yyyy format.
ms.custom: template-quickstart #Required; leave this attribute/value as-is.
---

# **HaloScript Overview**

HaloScript is the scripting language used within the game engine to make everything happen throughout the course of a mission. To generate a complete list of HS commands, open Sapien and type script_doc from the command console in the game window. A text document listing every command will be generated and placed in your \main folder.

## **Script Types**

### **Startup Scripts**

This is the starting point of every mission in the script file. There is only one startup script per mission. This script will execute all of its commands sequentially and is normally used to wake other dormant scripts and get things rolling for the mission. A startup script is named like the example below:

(script startup example_script)

### **Dormant Scripts**

The most commonly used type of script. As the name implies, they are "dormant" until another script "wakes" them using the wake command. This is an instant command— the script that uses this command will not be blocked (or delayed).

**Example**

```
(wake example_script)
```

A dormant script can be seen as a separate thread when it is started. It will sequentially go through all of its commands until it is finished. There can only be one instance of that script at any time: it is not possible to wake the same dormant script two times in a row. Once a dormant script is finished, it is impossible to wake it again. If you want to wake a dormant script multiple times, consider using a static script instead, or use a continuous script with the following structure:

```
(script continuous looping_script
(sleep_forever)
(print "Do your things here")
)
```

You can stop a dormant script by using the **sleep_forever** command.

### **Static Scripts**

This form of script is used to develop functions with a specific goal. They can be used by different dormant scripts or reused by the same dormant script. They are blocking, which means that a thread calling a static script that takes 5 seconds to execute will have to wait the entire 5 seconds before resuming its other activities. Basically, calling a static script is the equivalent of copy/pasting the entire static script where the call has been made.

Static scripts can return values and accept arguments. If you want a function to tell you if three objects are destroyed, you will probably want it to return a boolean, as shown here:

```
(script static boolean AreThreeObjectsDown
    ; Evaluate if the three objects are down
    (if (;* condition *;)
    true
    false
    )
)
```

The above script returns either true or false depending on the condition tested.

If you want a static script to have different behaviors depending on where you call it in your script, you can pass arguments to it. If, for example, you want a static script to send debug information to the screen when you specify it, you can use the following static script structure:

```
(script static void (do_something (boolean debug_print))
    ;Do something
    (if (= debug_print TRUE)
        (print "debug information!")
    )
    ;Do something else
)
```

You can call this static script by using the simple command:

**(do_something TRUE)**.

### **Command Scripts**

Command scripts are scripts that will be individually executed by AIs. They are there to script the behavior of a particular squad member, so that he does something that he would not naturally do otherwise. Only within these scripts can you use most of the commands that start with **cs_**. You can attach a command script to a unit in sapien by putting the name of the command script in the "placement script" field of a squad or a squad’s starting point. You can also use the following command to attach the example_script to squad_A:

```
(cs_run_command_script squad_A cs_example_script)
```

A very useful thing to prevent troops from looking ridiculous when under the influence of a command script is to make sure they react when they are injured, thus snapping out of their scripted behavior:

```
(cs_abort_on_damage true)
```

A monster under the influence of a command script will not shoot unless you explicitly give him the right to using the following commands:

```
(cs_enable_moving true)
(cs_enable_targeting true)
```

The probably most useful command for command scripts is cs_go_to, which explicitly tells the character to go to a specified point placed in Sapien. This will guide the monster executing the command script to the point p0 of point set pts_example_point_set:

```
(cs_go_to pts_example_point_set/p0)
```

#### **How to exit a command script**

There is three ways for a unit to exit a command script. The first way is the simplest: the unit finishes the command script, resuming whatever activity it had before. The two other ways are less trivial.

Ending with exit conditions

For each command script you can specify if you want the script to end in specific conditions. For example, to end the command script whenever the unit engages in combat, would use the following command:

```
(cs_abort_on_combat_status ai_combat_status_active)
```

There are also some other ai combat states that you can utilize. To end when the unit is on alert:

```
(cs_abort_on_alert TRUE)
```

To end when the unit receives damage:

```
(cs_abort_on_damage TRUE)
```

Ending by overriding with another command script

You can stop a unit from running a command script by telling the unit to run another command script that immediately ends.

```
(script command_script cs_exit
    (sleep 1)
)
```

To tell a unit to run the script above, you would use the following command:

```
(cs_run_command_script cov_elite_0 cs_exit)
```

## Variables

Variables are really useful to keep track of things in a script. There are no local variables - variables that only exist within a certain scope - they are all global and are declared as follows:

```
(global boolean var_A)
```

The main types of variables you will need are:

**boolean**— TRUE or FALSE

**short**— Discrete numbers (0, 45, -590)

**real**— Floating points (0.2, -8.5647, 3.1416) 

You can change the value of a global variable using the set command. The following example changes var_A to 3.

```
(set var_A 3)
```

Variables are also used by the game to change its behavior. These variables are usually booleans, but not always. While playing the game you can for example at any time change the speed of the game by typing the following in console. The following will slow the game by a factor of 2.

```
    (set game_speed 0.5)
```

## **Simple Commands**

Looking at existing scripts will probably be the most useful thing to do, but there are certain things that can be underlined upfront:

All commands begin and end with (parentheses)

A command always starts with the first parenthesis and the name of the command. Most functions then need parameters to follow. Ex:

- (save_game)
- (+ var_A 5)
- (print "debugging text to be seen ingame")
- In algebra commands, the following order is applied: (- 5 3) will return "2", and can be translated by **"5 – 3"**.
- Every script starts with the script block that has the startup tag in it: **(script startup mission)**
- ";" comments a line, and a text block within ";*" and "*;" will be commented as well

### **Print**

Prints text to the screen while playing the game. Useful to debug scripts.

```
(print "Hello World")
```

### **Begin**

The **begin** command is there only to make sure that multiple commands can be issued in places where only one command is expected. You will often use that command, and its use is really only to execute commands in a sequence. The next example prints two lines to the screen if var_A is equal to 3:

```
(if (= var_A 3)
    (begin
        (print "line 1")
        (print "line 2")
    )
)
```

### **If**

Conditions are done with the if command.

```
(if (= var_A 3)
    (sleep 30)
    (sleep 60)
)
```

The above command will sleep 1 second if the global variable var_A is equal to 3, and sleep 2 seconds if it is different.

### **Sleep_Until**

This command has multiple purposes, such as waiting until a certain condition is true, or waiting until certain other events have occurred. A simple command like the following will simply wait until either the squad jackal_c_2 is entirely dead or until var_A is equal to 3:

```
(sleep_until
    (OR
        (= (ai_living_count jackal_c_2) 0)
        (= var_A 3)
    )
)
```

The condition is evaluated once every 30 ticks (once per second). The first condition evaluates to true if the number returned by the command ai_living_count is equal to 0.

The second way to use the command sleep_until is to create a looping sequence (the equivalent to a "while" in C++, java, etc.). The way to do this is by placing a begin statement right after the sleep_until begins, and by putting the exit condition as the last command of that sequence. The next example will print "Halo" every second, until variable var_A is equal to 3:

```
(sleep_until
    (begin
        (print "Halo")
        (sleep 30)
        (= var_A 3)
    )
)
```

There are two optional parameters for that command: the first one is the number of ticks between each evaluation (default is 30). The second argument is a timeout for the sleeping command. After the timeout is reached, the **sleep_until** command is skipped and the script goes on.

## **Advanced Commands**

### **Checkpoints**

Checkpoints should be placed regularly throughout your levels. The command to initiate a checkpoint is:

```
(game_save)
```

> [!IMPORTANT]
> This command will not always save the game!

It will first wait for the player to be safe: the player is not engaged in combat, the player is not falling off a cliff, etc. If all these conditions are not met for a certain time (around 10 seconds), the command will terminate without saving the game. If you want the game to continue checking for the conditions to be met and save, use the following command:

```
(game_save_no_timeout)
```

### **Dialog**

In game dialog consists of two types: scripted and non-scripted dialog. The non-scripted dialog is managed by the engine, so we won’t describe it here. Scripted dialog is started when the designer wants it to. The following two commands will make Johnson speak, and then wait for him to finish his speech:

```
(sound_impulse_start sound\dialog\test\objective_sp_zanzibar\johnson_00 (ai_get_object mar_sgt_johnson) 1)
(sleep (sound_impulse_language_time sound\dialog\test\objective_sp_zanzibar\johnson_00))
```

The first function takes an object as a second argument. Notice how we converted from an AI squad to an object using the ai_get_object command. The second argument specifies the source of the dialog; it can be replaced by "none" so that the players always hear the dialog clearly (it is not coming from a particular object). The long path leading to johnson_00 actually refers to a sound tag.

### **Music**

Starting and stopping music is really easy in scripts. Once a song is started, it will continue looping until you stop it, so be sure to do so. Below is an example of how to start and stop a piece of music within the game:

```
(sound_looping_start sound\music\ec_ingame\ec_ingame none 1)
(sound_looping_stop sound\music\ec_ingame\ec_ingame)
```

### **Character Animation**

You can control the animation of a specific character in scripts. You usually do that for very specific moments, like a marine waving at you, Johnson pointing out an objective, etc. Here's a sample script for playing a custom animation:

```
(custom_animation (ai_get_unit ai_current_actor) "objects\characters\marine\marine" "combat:rifle:wave" true)
(sleep (unit_get_custom_animation_time (ai_get_unit ai_current_actor)))
```

The first argument refers to the object that will execute the animation, while the second argument points in which tag to look for the animation. The third argument reflects the actual animation. These animations can be found by exploring the model_animation_graph tag in Guerilla. The second command waits for the animation to be finished before moving to the next point in the script.

### **Navigation Points**

Activating and deactivating a waypoint is quite simple. You first need to have an object to attach the waypoint to, and you then activate/deactivate it with the following commands:

```
(hud_activate_team_nav_point_flag)
(hud_deactivate_team_nav_point_flag)
```

In this case the object is a scenery object named generator_E that was placed in Sapien.

### **Garbage collection**

The engine can only manage a fixed number of objects in the environment. When a large number of enemies are killed in a small space, the amount of weapons and corpses can easily become too large. The engine then automatically garbage collects the objects: it removes weapons and corpses that are not in the same section as the players.

Although the engine manages how many corpses can stay in the environment at the same time, sometimes you need to manually tell it when to remove them. This can happen in certain situations where performance is an issue and the garbage collecting is not done often enough. The first way to force it to garbage collect is the safest: it tells the engine to do the usual garbage collecting now. The weapons / corpses that are in the non visible areas will disappear. The command looks like this:

```
(garbage_collect_now)
```

If that doesn’t work, there is another, riskier, version:

```
(garbage_collect_unsafe)
```

This garbage collecting will delete every object in the environment, even those visible to the players. You should use it only when you control the position of the player and you know there are no weapons / corpses in that area.

### **AI Vision**

Sometimes you need to play with the AI awareness to make sure certain events happen. You can first make sure a squad sees another one by using the following command:

```
(ai_magically_see marines cov_base_attackers)
```

The command above reveals the Covenant to the marines, even if they wouldn’t normally see them. You can also prevent all squads from attacking a specific squad. This can be useful to prevent situations where the Covenant would shoot a Pelican instead of a marine, for example. In the following command, no one will attack the pelican (pelican_1):

```
(ai_disregard (ai_actors pelican_1) TRUE)
```

## **Randoms**

### **Random Numbers**

It is sometimes useful to get a random number, for purposes like waiting a random amount of time between each point in a patrol. A "random_range" command would look like this:

```
(sleep (random_range 15 30))
```

The above command causes the script to sleep for 15 to 30 ticks. Note that you can use random_range outside of a sleep command.

### **Random command execution**

The replayability of a game is better when some encounters are randomized. You can randomize events with a simple command: begin_random. This is a normal begin command, with the difference that it will execute all tasks in a random order. You can still have sequential events occurring randomly using nested begin commands, like in the following example:

```
(begin_random
    (begin
            (cs_go_to pts_cov_base_attackers/p0)
            (sleep_until (= var_flag_0 TRUE) 30 210)
    )
    (begin
            (cs_go_to pts_cov_base_attackers/p1)
            (sleep_until (= var_flag_1 TRUE) 30 210)
    )
)
```

In the above example a unit will first go to either p0 or p1, wait for a flag to be true, and then go to the other point he didn’t explore yet. There is no easy way to have only one command execute randomly, but you can accomplish it using a global variable. The following example will print either A, B, or C:

```
(global boolean var_cmd_done FALSE)
(begin_random
    (if (= var_cmd_done FALSE)
            (begin
                (print "A")
                (set var_cmd_done TRUE)
            )
    )
    (if (= var_cmd_done FALSE)
            (begin
                (print "B")
                (set var_cmd_done TRUE)
            )
    )
    (if (= var_cmd_done FALSE)
            (begin
                (print "C")
                (set var_cmd_done TRUE)
            )
    )
)
```

## **Object Management**

All objects are placed in Sapien, but sometimes you want to control when they appear on the map. To prevent an object from being created when the map is loaded, you must set the flag "not automatically" to true in Sapien. You then place or delete the object in script using the following commands:

```
(object_create weapons_BR_0)
(object_destroy weapons_BR_0)
```

You can also poll an object to get its health. The sample below will return a real number between 0 and 1:

```
(object_get_health generator_D)
```

### **Contextual Examples**

Tracking the player’s position

It is a good practice to always have a separate thread testing your trigger volumes. This ensures you don’t have two different threads testing the same trigger volume. You can either just latch the player’s position to TRUE, or put it back to FALSE when the player is not in the space anymore (if that is important for your needs). Here is a sample script with the two examples in it:

```
(global boolean var_pos_room_a_0 0)
(global boolean var_pos_room_a_1 0)
```

```
;*Update global variables indicating what is the player's current position*;
(script dormant room_a_pos_updater
    (sleep_until
            (begin
                (if (= (volume_test_objects vol_room_a_0 (players)) TRUE)
                        (set var_pos_room_a_0 1)
                        (set var_pos_room_a_0 0)
                )
                (if (AND
                        (var_pos_room_a_1 FALSE)
                        (= (volume_test_objects vol_room_a_1 (players)) TRUE)
                )
                (set var_pos_room_a_1 1)
                )
            )
    )
)
```

### **Guiding the marines** (or other player allies)

You probably want a separate thread (dormant script) to lead the marines within the level. The reason behind this is simple: the marines will sometimes wait on different conditions than the monsters to move. If a single script is used, you might end up waiting for a walking condition for the monsters while the marines should have moved. When both the marines and the monsters are waiting for the same condition, you can create a trigger within Sapien that can be queried from both scripts using the command **ai_trigger_test**.

### **Patrolling**

There are two ways to do a patrol. You can give the squad a bunch of firing points and have an order on "idle" combat status. The squads under that order will randomly go from a firing point to another. If you want more control, you need to use a command script that precisely tells where to go next, like the example below:

```
(script command_script cs_A_elite_patrol_0
    (cs_abort_on_combat_status ai_combat_status_active)
```

Above is the exit condition that allows you to stop patrolling whenever the squad engages the enemy.

```
    (cs_enable_pathfinding_failsafe true)
```

The default behavior for cs_go_to commands is to skip the walking point if a small pathfinding problem occurs. You want to turn that variable to true to make sure the AI will really go to the specified points.

```
    (sleep_until
            (begin
                (cs_go_to pts_A_elite_patrol_0/p0 1)
```

The real command that makes it all possible. pts_A_elite_patrol_0/p0 is a point that is part of the pts_A_elite_patrol_0 point set. They are placed in Sapien.

```
                (cs_go_to pts_A_elite_patrol_0/p1 1)
                (sleep (random_range 15 30))
```

We usually make sure to add some amount of sleeping between two points, so that the unit stops for while, looks around, and then continues his patrol.

```
                (cs_go_to pts_A_elite_patrol_0/p2 1)
                (sleep (random_range 15 30))
                (cs_go_to pts_A_elite_patrol_0/p3 1)
                (sleep (random_range 60 90))
    false)
```

Always loop: patrolling goes back to the first point.

```
    )

)
```

### **Dropships**

Dropships are all scripted. You tell them where to go, how to get there, at which speed, etc. Let’s look at a script example.

Loading the guys in - This function loads in guys you would have spawned just before. They will instantly teleport to their respective seat.

```
      (vehicle_load_magic (ai_vehicle_get_from_starting_location LZ_phantom_02/pilot) "phantom_p" (ai_actors LZ_jackals_phantom_02))
```

The ride

```
      (script command_script LZ_phantom_arrives_01
            (cs_enable_pathfinding_failsafe TRUE)
            (cs_vehicle_speed .5)
            (cs_vehicle_boost TRUE)
```

The speed of the vehicle from 0 to 1, and if you want the phantom to come in really fast (boost).

```
            (cs_fly_by LZ_airspace/ph0a)
```

cs_fly_by means that the phantom will pass near the point but will not stop at it.

```
            (cs_vehicle_boost FALSE)
            (cs_fly_by LZ_airspace/ph1a)
            (cs_fly_by LZ_airspace/ph2a)
            (cs_vehicle_speed .3)
            (cs_fly_to LZ_airspace/pel6 2)
```

This time the phantom will stop at this point before moving on to the next command.

```
            (cs_fly_to_and_face LZ_airspace/pel6 LZ_airspace/p0 1)
```

Same as cs_fly_to, but the phantom position itself to face the second point given in argument.

```
            (wake lz_phantom_01_drop)
```

You usually wake a different thread that will drop the covenants on that spot. Waking a different thread to drop while still moving is an 
option. The other option is to wait for the phantom to unload before moving.

```
            (cs_fly_to_and_face LZ_airspace/ph3a LZ_airspace/p0 1)
            (sleep_until (<(ai_living_count lz_phantom_01) 2) 30 900)
```

You want to wait until a certain condition before taking off. Sleep at least long enough to let your guys drop off the phantom.

```
            (cs_fly_by LZ_airspace/ph2a)
            (cs_vehicle_speed .5)
            (cs_fly_by LZ_airspace/ph1a)
            (cs_fly_by LZ_airspace/ph0a)
            (cs_fly_to LZ_airspace/phxa)
            (ai_erase LZ_phantom_01)
```

You always want to erase a guy once he’s out of sight. Make sure to lead the phantom far enough so that you don’t hear its ambient sound no longer.

```
      )
```

Dropping the guys - Dropping guys is straight forward. The only thing you need to remember is to have some time between drops so the squads don’t land on each other’s head.

```
      (script dormant lz_phantom_02_drop

            (object_set_phantom_power (ai_vehicle_get_from_starting_location lz_phantom_02/pilot) TRUE)
```

You want to activate power on a phantom so that the dropping bay opens and that the phantom can actually drop its troops.

```
            (vehicle_unload (ai_vehicle_get_from_starting_location lz_phantom_02/pilot) "phantom_p_a01")
```

This function unloads troops from the phantom_p_a01 seat. There could be guys in the following seats, as well as in the phantom_p_b… and phantom_p_c… seats. See the phantom tag in guerilla to get a list of all the seats.

```
            (sleep 15)
            (vehicle_unload (ai_vehicle_get_from_starting_location lz_phantom_02/pilot) "phantom_p_a02")
            (sleep 15)
            (vehicle_unload (ai_vehicle_get_from_starting_location lz_phantom_02/pilot) "phantom_p_a03")
            (vehicle_unload (ai_vehicle_get_from_starting_location bridge_phantom_01/pilot) "phantom_lc")
```

This will unload the large cargo, which usually contains a ghost.

```
            (sleep 60)
            (object_set_phantom_power (ai_vehicle_get_from_starting_location lz_phantom_01/pilot) FALSE)
      )
```

### **Doors & Switches**

The way doors and switches connect is done through scripting. You have to always check for the position of a switch, and when that position changes you decide to do what you want next, usually open a door. This can be done really easily with the following two commands:

```
      (sleep_until (> (device_get_position beach_switch) 0))
```

device_get_position returns the position of the switch, which is 0 by default. When the player activates it, it changes from 0 to 1. The switch is a device control object named beach_switch.

```
      (device_set_position beach_door 1.0)
```

This command simply opens a door, beach_door, a device machine object.

### **AI/Vehicle Interaction**

Here is some information about AIs and vehicles.

#### **Enter/Exit**

Two quick commands to know: **ai_vehicle_enter** and **ai_vehicle_exit**. Here’s an example on how to use them:

```
      (ai_vehicle_enter mar_sgt_johnson (ai_vehicle_get_from_starting_location warthog_0/driver) "warthog_d")
```

The command above tells the mar_sgt_johnson squad to try to get into the vehicle that was originally spawned by the warthog_0 squad, in the driver position. The seat is specified with the last argument (warthog_d). The following command tells anybody occupying the warthog to exit the vehicle. The warthog is referenced as a vehicle that was originally spawned by the warthog_0 squad:

```
      (ai_vehicle_exit warthog_0)
```

Some sandbox behaviors may override these commands. For example, if a unit is driving a vehicle and the player makes him exit (by pressing X), the AI driver won’t enter the vehicle again for a long time. Even the ai_vehicle_enter command won’t for him to.

#### **Reserving Seats**

As part of their sandbox behavior, brutes, elites and even grunts will use vehicles by themselves. Sometimes you want to prevent that situation by making a vehicle impossible to drive. This can be achieved by reserving a vehicle, or a specific seat.

```
      (ai_vehicle_reserve_seat (ai_vehicle_get_from_starting_location warthog_0/driver) "warthog_d" TRUE)
```

In the above command we tell every AI not to drive the vehicle that was spawned with the warthog_0 squad. Sometimes you want to prevent the player from driving a vehicle (maybe it wasn’t introduced as a drivable vehicle yet). This can be done using the following command:

```
      (unit_set_enterable_by_player (ai_vehicle_get_from_starting_location warthog_0/driver) FALSE)
```

#### **Driving a Vehicle**

You can let an AI drive a vehicle by himself, giving firing points from a vehicle area. You can also script a ride so that the driver always takes the same route. This is done quite easily with points placed in Sapien, in a point set.

```
      (script command_script cs_warthog_escape
            (cs_enable_pathfinding_failsafe true)
            (cs_vehicle_speed 0.75)
            (cs_go_to pts_marines_warthog/p0 2)
```

The line above tells the AI to drive to a specific point. The second argument, 2, is the acceptable radius around the point. If the vehicle is within that range, the cs_go_to command is considered accomplished.

```
            (cs_go_to pts_marines_warthog/p1 2)
      )
```

After this command script has ended, the AI driver will look for his normal firing points and use them.

## **Effects**

Playing from Scenery objects

You use scenery objects when you want an effect that is permanent. You place a scenery effect (usually under tags/effects/scenery) and deactivate it with the "not automatically" flag. You can then activate it with the following command:

```
      (object_create_anew fx_0)
```

The above command creates the effect scenery object named fx_0.

Using flags

This effect is used for quick scripted explosions, sparkles, etc. You first need to place a flag in Sapien. You then choose an effect you like. An effect can include sound, visual effect, damage, etc:

```
      (effect_new "effects\scenarios\solo\alphagasgiant\wall_explosion" flag_fx_0)
```

The command above will start an explosion on the flag flag_fx_0.

## ** Volume Return Objects by Type

Below is information concerning the usage of the volume_return_objects_by_type HS command.

Here's the enumeration that's used:

```
enum e_object_type

{

_object_type_biped,

_object_type_vehicle,

_object_type_weapon,

_object_type_equipment,

_object_type_terminal,

_object_type_projectile,

_object_type_scenery,

_object_type_machine,

_object_type_control,

_object_type_light_fixture,

_object_type_sound_scenery,

_object_type_crate,

_object_type_creature,

_object_type_giant,

k_object_types_count,

_object_type_first= _object_type_biped,

_object_type_none= NONE

};
```

The number that corresponds to each entry is 2^entry_index (where entry_index starts at 0). So biped is 2^0= 1 and projectile is 2^5= 32.

You can add numbers together to get masks: 35= 32 + 2 + 1= 2^5 + 2^1 + 2^0, so that would mask projectile, vehicle, and biped.

## **Helpful Hints**

This section is just a bunch of points that one might struggle with when learning the scripting language.

- Some commands need an "object" type parameter. When you want to use that command on a squad, you need to first convert it using the command ai_actors.
- You might find it useful in some command scripts to have a reference to the unit that is currently executing it. The unit currently running the script can be accessed with ai_current_actor.
