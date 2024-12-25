# Compatibility with PvZ or PvZ Dark Horde

According to information from several players, compatibility issues are also observed with the "PvZmoD_TheDarkHorde" modification, where infected may become invulnerable. Therefore, point [☑️ 3](#%EF%B8%8F-3-disabling-inediainfectedai-damage-control-system), i.e., disabling damage handlers, should also be executed for "Dark Horde." If you are using "Dark Horde", just disable the damage handlers for "InediaInfectedAI" (point [☑️ 3](#%EF%B8%8F-3-disabling-inediainfectedai-damage-control-system))) and use "Dark Horde" in combination with "PvZ". These mods are compatible with each other and do not conflict.

If you know of any additional compatibility details not covered in this guide, please write about them in Discord, and I will update the guide.

### Information on compatibility with PvZ received from other players

Please note that the dot in the Inedia parameter indicates JSON nesting.

That is, for example, the parameter _Zombies.ParameterName_ means:

    "Zombies": {
        "ParameterName": ...
    }

### ☑️ 1) Disabling "PvZ" door-breaking mechanics

You need to disable doors breaking handler in "PvZ" (not necessary in "PvZ" version 1.23 stable and higher).

Note:
If you are using "PvZ" version 1.23 stable or higher, you do not need to complete this step or disable the door-breaking handler, as in this version, it will be automatically disabled if you have the "InediaInfectedAI" mod enabled.

If your "PvZ" version is less than 1.23, then you need to do this because there it does not have functionality that is required for "InediaInfectedAI" mod to work correctly, i.e. functionality that switches zombie search mode if he cannot knock down a door. In this case - zombie will simply get stuck in door until the search mode ends, which is a very long time;

Disabling these mechanics for "PvZ" mod (PvZmoD_CustomisableZombies_Globals.xml):

    Features_Activation.Zombies_Breaking_Doors_Activated = 0


### ☑️ 2) Disabling vehicle attack mechanics

There may probably be problems with car attack functionality working together, you need to disable this in one of the mods.

Disabling these mechanics for "PvZ" mod (PvZmoD_CustomisableZombies_Globals.xml):

(haven't checked, need to confirm)

    Damages_To_Vehicles_Radiator_When_Cruching_Zombies.Activated = 0
    Zombies_Attacking_Stopped_Vehicles.Activated = 0


Disabling these mechanics for "InediaInfectedAI" mod:

    Zombies.AttackCarHandlerIsActive = 0


### ☑️ 3) Disabling "InediaInfectedAI" damage control system

For damage mechanics against players and zombies to work correctly you can disable this mechanic for "InediaInfectedAI" mod.

I tried to find a way to disable these mechanics in "PvZ" and keep the "InediaInfectedAI" mechanics, but nothing worked for me. Zombies are either simply invulnerable or cannot be killed while in a crawling state. Therefore, please just disable these mechanics in "InediaInfectedAI" and use "PvZ". In that case, there were no issues found.

Disabling these mechanics for "InediaInfectedAI" mod:

    Zombies.DamageToPlayerHandlerIsActive = 0
    Zombies.DamageToZombieHandlerIsActive = 0


### ☑️ 4) Disabling speed control system in one of the mods

For zombie speed settings to work correctly, you must disable them in one of the mods.

Disabling these mechanics for "PvZ" mod (PvZmoD_CustomisableZombies_Globals.xml):

    Features_Activation.Zombies_Speed_Activated = 0
    Features_Activation.Zombies_Speed_Adjust_Activated = 0

Disabling these mechanics for "InediaInfectedAI" mod:

    Zombies.SpeedHandlerIsActive = 0

More information about speed parameters [here](Description#zombiesspeedhandlerisactive).

### ☑️ 5) Mechanics of attacking unconscious players

To prevent zombies from attacking unconscious players, you need to disable this mechanic in both mods.

Disabling these mechanics for "PvZ" mod (PvZmoD_CustomisableZombies_Globals.xml):

    Features_Activation.Zombies_Hit_Unconscious_Players_Activated = 0

Disabling these mechanics for "InediaInfectedAI" mod:

    Zombies.AttackPlayersUnconscious = 0


### ☑️ 6) Disabling projectile throwing system in one of the mods

In "InediaInfectedAI", there is a system for infected to throw projectiles at the player. In "PvZ", infected also throw stones at players.
To prevent these systems from working simultaneously, you need to disable one of them in one of the mods.

Disabling stones throwing for "PvZ" mod (PvZmoD_CustomisableZombies_Globals.xml):

    Zombies_Throw_Stones.Zombies_Throw_Stones_Activated = 0

Disabling the projectiles throwing system in "InediaInfectedAI":

    Zombies.ThrowingHandlerIsActive = 0
