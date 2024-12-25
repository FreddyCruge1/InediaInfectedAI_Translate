* [Is there a guide for initial configuration? Where can I find the configuration options related to the functionality I need?](#is-there-a-guide-for-initial-configuration-where-can-i-find-the-configuration-options-related-to-the-functionality-i-need)
* [I set some parameters in configuration file, but server ignores them](#i-set-some-parameters-in-configuration-file-but-server-ignores-them)
* [Where can I view the default configuration file?](#where-can-i-view-the-default-configuration-file)
* [How to make zombies less sensitive to player noise?](#how-to-make-zombies-less-sensitive-to-player-noise)
* [Why do some Zombies.React* parameters not affect the irritation radius of the infected?](#why-do-some-zombiesreact-parameters-not-affect-the-irritation-radius-of-the-infected)
* [The infected can hear the silencer shot very well. Why is that?](#the-infected-can-hear-the-silencer-shot-very-well-why-is-that)
* [Infected deal damage through blocking. How can this be configured?](#infected-deal-damage-through-blocking-how-can-this-be-configured)
* [Is there a way to make infected and NPCs (AI Bots) friendly towards each other?](#is-there-a-way-to-make-infected-and-npcs-ai-bots-friendly-towards-each-other)
* [Infected walk in water and underwater. How can this be fixed?](#infected-walk-in-water-and-underwater-how-can-this-be-fixed)
* [How to change the damage of players clothing by projectiles thrown by infected and players?](#how-to-change-the-damage-of-players-clothing-by-projectiles-thrown-by-infected-and-players)
* [Key card doors can be opened using the quiet door opening function and can also be kicked in by the infected. How to fix it?](#key-card-doors-can-be-opened-using-the-quiet-door-opening-function-and-can-also-be-kicked-in-by-the-infected-how-to-fix-it)
* [How does the logic of vehicle attack work?](#how-does-the-logic-of-vehicle-attack-work)
* [How to configure the projectile throwing system?](#how-to-configure-the-projectiles-throwing-system)
* [When dealing damage, the infected stun the player and apply various debuffs. How can I configure this?](#when-dealing-damage-the-infected-stun-the-player-and-apply-various-debuffs-how-can-i-configure-this)
* [How does the player pain system work?](#how-does-the-player-pain-system-work)
* [How to affect the Inedia pain system with custom medicines and statuses from other mods?](#how-to-affect-the-inedia-pain-system-with-custom-medicines-and-statuses-from-other-mods)
* [Strong bosses and mutants on my server are dying from bleeding, how can I adjust this?](#strong-bosses-and-mutants-on-my-server-are-dying-from-bleeding-how-can-i-adjust-this)
* [How does the blood and bleeding system work?](#how-does-the-blood-and-bleeding-system-work)
* [Strong bosses and mutants on my server get attack and speed debuffs from damage, how can I adjust this?](#strong-bosses-and-mutants-on-my-server-get-attack-and-speed-debuffs-from-damage-how-can-i-adjust-this)
* [How does the injury and debuff system work?](#how-does-the-injury-and-debuff-system-work)
* [How can I activate the search mode for infected in my scripts?](#how-can-i-activate-the-search-mode-for-infected-in-my-scripts)
* [How does vanilla weather affect the mechanics of this mod?](#how-does-vanilla-weather-affect-the-mechanics-of-this-mod)

***

### Is there a guide for initial configuration? Where can I find the configuration options related to the functionality I need?

You can find a detailed guide on the initial configuration [here](Configuration-guide).

If the server is ignoring your configuration parameters, please refer to [this FAQ item](#i-set-some-parameters-in-configuration-file-but-server-ignores-them).

***

### I set some parameters in configuration file, but server ignores them

If there is an parse error in configuration file, the server will ignore all parameters from the configuration file and will use the default parameters.

If for some reason server ignores parameters from configuration file - check content of the config file using:

JSON validator: https://jsonlint.com

Just copy contents of the file, paste it into text area and click "Validate JSON" button, the validator will output errors if there are any.

Also be sure to check the server crash report, as the online validator cannot detect parameter type mismatch errors:

    %DayZserverDir%/profiles/crash_*.log

***

### Where can I view the default configuration file?

If you've changed a parameter and want to revert it back without deleting the current configuration file, you can check the current configuration file with default values [here](Default-configuration-file). It gets updated after each modification update.

***

### How to make zombies less sensitive to player noise?

In this modification, zombies can react to player noise and enter search mode through multiple methods:

1. Reacting to player's vanilla noise;
2. Reacting to the irritant specific to this mod, activated by the player when moving every 5 seconds, with a radius that depends on the type of movement;

In the first case, you can try adjusting the  "[Players.NoiseMultiplier*](Description#playersnoisemultiplierday)" and "[Players.NoiseMultiplierCrouch*](Description#playersnoisemultipliercrouchday)" parameters.

This multipliers is not dependent on the zombie type and only modifies the vanilla sounds produced by the player. The default value in the vanilla version of the game is "1". In this modification, the default value is set to "2" for all states except crouching (which means that the vanilla noise produced by the player is twice as loud, and consequently, zombies react to this vanilla player noise twice as effectively as in the standard version of the game), and "1" for the crouching state, indicating that a player in the crouching state produces the same noise as in the vanilla game.

For the second case, there is a flexible configuration for the response of any zombie type to the sound of footsteps during different player movement types.

You can try configuring the response of specific zombies to footsteps using the parameters [Zombies.ReactFootsteps*](Description#zombiesreactfootstepsjogdaynoise). This functionality is not related to the vanilla mechanics but is part of the irritant mechanics of this mod, so it is separate from the aforementioned _Players.NoiseMultiplier*_ and should be adjusted independently.

***

### Infected deal damage through blocking. How can this be configured?

First and foremost, it's important to understand that block penetration animation does not signify regular health damage, it can occur due to shock damage in block, a chance to inflict bleeding on a blocked hit, or from receiving pain damage in block (InediaInfectedAI pain/injury system, parameters _Zombies.PainToPlayer*InBlockMultiplier_).

However, if default modification settings are used, infected indeed penetrate blocks, but any damage/shock damage/pain damage dealt is halved. Additionally, chances of inflicting various statuses (stunning, bleeding) are also halved.

Essentially, block penetration animation is not activated without reason. Without this animation, certain functionality of this mod regarding block penetration will not work (the handler PlayerBase.EEHitBy() simply won't return damage necessary for applying multipliers and calculating probabilities). Therefore, even if all damage to the block is disabled except, for example, shock damage, this mod activates the block penetration animation for it, as this animation is necessary for the functionality of dealing shock damage to the block, otherwise, it won't work.

If you are using a custom mod that applies statuses due to this animation and this animation interferes with its proper functioning, you can only disable it by turning off all types of damage to the block that trigger the block penetration animation. You can also disable it by turning off just one parameter, _Zombies.DamageToPlayerHandlerIsActive_, but in doing so, you'll lose all functionality of damage control to the player associated with this parameter.

Below are all the mechanics that depend on block penetration animation and activate it if they are active themselves:

The logic of block piercing animation appearance:

    Zombies.DamageToPlayerHandlerIsActive = 1
    AND
    (
        Zombies.DamageToPlayerInBlockHealthMultiplier > 0
        OR
        Zombies.DamageToPlayerInBlockShockMultiplier > 0
        OR
        (
            Zombies.DamageToPlayerBleedingHandlerIsActive = 1
            AND
            Zombies.DamageToPlayerInBlockBleedingChancePercent > 0
        )
        OR
        (
            Players.PainSystemIsActive = 1
            AND
            Zombies.PainToPlayerHandlerIsActive = 1
            AND
            (
                Zombies.PainToPlayerHeadInBlockMultiplier > 0
                OR
                Zombies.PainToPlayerArmsInBlockMultiplier > 0
                OR
                Zombies.PainToPlayerLegsInBlockMultiplier > 0
                OR
                Zombies.PainToPlayerTorsoInBlockMultiplier > 0
            )
        )
    )

Remember that if there is block piercing animation, regardless of whether the character takes damage or not, the character's clothing will be damaged. To disable clothing damage, you will need to completely disable the block piercing animation by following the conditions above.

***

### Why do some Zombies.React* parameters not affect the irritation radius of the infected?

This is because, in addition to the irritation mechanics introduced by "InediaInfectedAI", there is also the vanilla irritation mechanic. "InediaInfectedAI" reacts to the vanilla mechanic, which means that the infected have two ways to switch to search mode:
* Entering the radius of the Inedia irritant;
* Through vanilla irritation;

In the Inedia configuration, there are certain _Zombies.React*_ parameters that overlap with the vanilla mechanics. For example, the infected's reaction to the noise of a gunshot, _Zombies.ReactWeaponShotNoise_. This can lead to confusion as to why adjusting the radius through these parameters doesn't affect the irritation radius. It's because you're only disabling the effect of the Inedia irritant, while the vanilla irritant remains active.

So, the question arises: why introduce these Inedia irritants and parameters to configure them if the vanilla mechanic overrides them?

Originally, I didn't plan to introduce this parameters because I was completely satisfied with activating the search mode when zombies react to the vanilla noises.
Unfortunately, when the zombie was already in MINDSTATE_ALERTED mode, I had no way to somehow process its irritation caused by footstep noise and change the search goal (for example, a zombie will run towards a gunshot or any other irritant and won't react to the vanilla footsteps noise for some time).
That's precisely why this Inedia irritants was introduced, allowing you to change the zombie's goal independently of the vanilla mindstate mode.

As for the parameters _Zombies.React*_ that overlap with the vanilla mechanics and how they can still be used.

"InediaInfectedAI" allows you to limit the search mode activation radius for vanilla irritants. This is done using the [Zombies.ReactVanillaMindstateChange](Description#zombiesreactvanillamindstatechange) parameter. If you limit this radius to, for example, 50 meters, the only way to switch the infected to search mode outside of those 50 meters will be through the Inedia irritant, which is configured via the _Zombies.React*_ parameters. Accordingly, these parameters gain some purpose. You can read more about it in the description of the [Zombies.ReactVanillaMindstateChange](Description#zombiesreactvanillamindstatechange) parameter."

***

### The infected can hear the silencer shot very well. Why is that?

First of all, you need to realize that there are several irritants that you might have confused with the reaction of infected to a shot from a silencer:
* Reaction to the fall of another infected's body (about 15 meters radius from where the body falls by default);
* Reaction to the fall of the bullet if you shoot into a bush, ground or wall - the infected hear it well and react;

If it's not about these irritants, consider how the vanilla mechanics of infected irritation work. In vanilla mechanics, zombies have a cumulative irritation scale. If you shoot with a silencer too often - it will reach a critical level and irritation will occur. Try to shoot once every 5 seconds - and there will be no problems, because the irritation scale is lowered if there are no sounds.

My trigger reacts to vanilla irritation mechanic and triggers when the infected's mindstate changes from CALM to ALERTED/DISTURBED and the infected has a target.

If in a vanilla game you shoot 3-4 times very quickly with a silencer, this is exactly what will happen.

The MKII and AS VAL are the quietest weapons in the game, so they raise the infected's irritation scale very slowly, however if you fire the MKII long like a machine gun they will react the same way, well, maybe the irritation radius will be a little smaller.

After the irritation happens - in my modification they run to the source of irritation, in vanilla they can run in different directions, so they don't run to you and you don't have the whole city of infected. That's the difference.

But they get irritated in both cases.

To prevent the entire infected city from flocking to you after such shots, you can try adjusting the "[Zombies.ReactVanillaMindstateChange](Description#zombiesreactvanillamindstatechange)" parameter. Learn how it works by clicking the link. However, I do not recommend setting its value below "0.3".

***

### Is there a way to make infected and NPCs (AI Bots) friendly towards each other?

Yes, you can do it using parameter "[Zombies.FriendlyNPC](Description#zombiesfriendlynpc)", but not all mods introducing NPCs are available.

This parameter can be set not only for infected classes, but also for animals, meaning animals can be befriended with NPC and AI bots.

***

### Infected walk in water and underwater. How can this be fixed?

This is designed this way in this modification, they are allowed to build a path under any water.

It's toggled via the game config, so this mod cannot provide a setting for toggling it off.

However, you can modify the game configuration by connecting your mod with the following contents in config.cpp:

    class CfgPatches {
        class InediaInfectedAI_PathGraphFiltersNoWater {
            requiredAddons[] = {"InediaInfectedAI"};
        };
    };

    class PathGraphFilters {
        class ZombieAlerted {
            class Flags {
                include[] = {"walk", "door", "inside", "jump", "climb"};
                exclude[] = {"disabled", "crawl", "crouch"};
            };
        };
    };


Alternatively, you can use [this mod](https://steamcommunity.com/sharedfiles/filedetails/?id=3119213010) (repackaging is allowed) that will do this for you.

***

### How to change the damage of players clothing by projectiles thrown by infected and players?

It's impossible to achieve through the configuration of this modification due to the specific implementation details of damage application in this modification. It utilizes the vanilla method of damage application, which calculates player clothing damage based on the ammo type provided. For all projectiles, it uses ammo "InediaInfectedAI_ThrowingProjectile", so by modifying the damage of ammo "InediaInfectedAI_ThrowingProjectile" in config.cpp, we can influence the degree of clothing damage caused to the player when hit by a projectile.

Due to the above-mentioned reasons, it's not possible to influence the damage of individual projectiles, it can only be adjusted universally for all projectiles, as they all use ammo "InediaInfectedAI_ThrowingProjectile".

To modify the damage caused by ammo "InediaInfectedAI_ThrowingProjectile", you need to create your own modification of config.cpp with the following content:

    class CfgPatches {
        class InediaInfectedAI_ThrowingProjectile {
            requiredAddons[] = {"InediaInfectedAI"};
        };
    };

    class CfgAmmo
    {
        class MeleeDamage;
        class InediaInfectedAI_ThrowingProjectile: MeleeDamage
        {
            class DamageApplied
            {
                class Health
                {
                    damage=10
                };
            };
        };
    };

Instead of "damage=10", you can specify any damage value greater than 0 and less than 30. The default damage is set to 10. It's advisable not to set it higher than 30, as hitting a player in the head could result in death, since the head has just over 30 hit points.

***

### Key card doors can be opened using the quiet door opening function and can also be kicked in by the infected. How to fix it?

Currently, InediaInfectedAI supports the following modifications that add doors with keycards: "DNA Keycards", "Custom Keycards", "KeyCard-Rooms", "Banov", "DeerIsle", "Sakhal" (for the Sakhal map, all doors of the "Land_WarheadStorage_Main" building are currently completely excluded, which is not quite right, so if you have information on the indexes of specific doors that should be excluded, as well as any other buildings to exclude, please provide it, and I will update the modification and the guide). If you are using them and you have an updated configuration file, you probably won't encounter any issues, and you can proceed without further reading. If you encounter any issues with these modifications, please submit a report.

As for other modifications - InediaInfectedAI doesn't have information about custom doors to exclude them.

**Thus, infected will be breaking down these doors.**

The exclusion of such doors for infected can be done by the server owner using a configuration parameter specifically introduced for this purpose: [Zombies.BreakingDoorsRestrictedDoors](Description#zombiesbreakingdoorsrestricteddoors)

**Regarding the quiet door opening function.**

By default, this feature is disabled in the modification, and no further action is required, and the text can be disregarded from this point.

However, if you intentionally enabled this feature, _Players.QuietDoorOpeningMechanicDisabledForOpening_ = 0, then custom doors locked with a key card - will open with the quiet door opening feature.

In this case, it depends on the modification that adds custom doors and how it closes these doors. If this modification closes them with a lock pick - then everything will be fine, because the function of quiet door opening - does not open doors closed with a lock. If it uses its own mechanisms for closing doors, InediaInfectedAI does not know anything about such mechanisms, and therefore such doors will be opened by the quiet door opening function.

In order for the quiet door opening function not to work for such doors, a special parameter [Players.QuietDoorOpeningMechanicRestrictedBuildings](Description#playersquietdooropeningmechanicrestrictedbuildings) has been created, allowing their exclusion.

***

### How does the logic of vehicle attack work?

Damage to a vehicle can be of two types:
* Damage from collisions with entities;
* Damage from entity strikes;

**Damage from collisions with entities.**

Damage is distributed randomly among the vehicle's components. Initially, protective elements of the vehicle (such as bumpers, fenders, and the hood) take the damage. Only after these elements are completely destroyed, damage is applied to important components of the vehicle (engine, radiator, car battery, spark plug, fuel tank, etc.).

Protective elements essentially act as the vehicle's armor, which must be maintained in good condition to prevent damage to important vehicle components.

Vehicle doors, including the rear door, are not damaged in collisions with entities and are neither protective nor important components. However, they play a crucial role in player protection, which will be explained below.

**Damage from entity strikes.**

In this case, the entity is searching for a player to attack within the radius of _Zombies.AttackCarPlayersDistanceMeters_ meters.

If the player is found and there are no doors in the path to the player, the player is attacked.

If there are doors in the path to the player and there is glass on the doors, the door glass is attacked first, and only after that, the door and the player. The door itself plays a crucial role in protecting the player because if the door is not destroyed, there is a _Zombies.AttackCarDoorChancePercent_% chance that the damage intended for the player will be redirected to the door, damaging it.

If the door is destroyed, the player will receive damage with a 100% probability.

If no players are detected around the entity, all possible elements of the vehicle within _Zombies.AttackCarElementsDistanceMeters_ meter radius are considered for attack. Elements are attacked based on the collision logic described above, starting with protective elements and then important ones.

***

### How to configure the projectiles throwing system?

First and foremost, you need to configure the projectiles themselves, their type, conditions of use, this is done using parameter [Zombies.ThrowingProjectiles](Description#zombiesthrowingprojectiles).

If you have an updated configuration file, then by default the following types of projectiles are already set up: "GarbageIfPlayerOnObstacle", "FlashGrenade", "HEGrenade", "GasGrenade", as well as some thematic projectiles. If you have an old configuration file or you deleted some projectiles, you can always find the default parameter values in the [default configuration file](Default-configuration-file).

After you have configured the projectiles or if you are satisfied with the default projectiles, you need to bind them to the infected. This is done using parameter [Zombies.ThrowingProjectilesHandlerProjectilesList](Description#zombiesthrowingprojectileshandlerprojectileslist).

If you have an updated configuration file, projectiles such as "GarbageIfPlayerOnObstacle" and some thematic projectiles will already be bound to the infected.
* "GarbageIfPlayerOnObstacle" is ground garbage (sticks, stones). This projectile is infinite, but they can only throw it when the player is on an obstacle. They also throw this projectile very often.
* Thematic projectiles consist of several projectiles depending on the infected locations (village, city, industrial zone, etc.). These projectiles are available only in limited quantities, with a 10% chance of throwing them and a 10-second cooldown even after an unsuccessful attempt. However, they can throw them even when the player is not on an obstacle. The damage, bleeding, or stun chance of these projectiles is determined by the type of thrown item and its weight. For example, a kitchen knife is more likely to cause bleeding when hitting a player, but it won't stun them, whereas a frying pan is more likely to stun a player without causing bleeding, whereas an axe is more likely to cause both bleeding and stun.

After binding the projectiles, or if you are satisfied with the default binding, the configured infected should start throwing the specified projectiles according to the conditions described in the projectile settings.

Since the same projectile, for example a stick, can cause different damage depending on the person who threw it, a multiplier [Zombies.ThrowingProjectilesHandlerDamageMultiplier](Description#zombiesthrowingprojectileshandlerdamagemultiplier) has been added. This global multiplier allows for adjusting the damage of all projectiles associated with the infected, thereby implementing the logic of damage alteration based on the infected's strength. By default, this parameter is already configured for infected groups "lowstr", "mediumstr", and "highstr".

You can also disable their ability to throw projectiles at vehicles using parameter [Zombies.ThrowingProjectilesHandlerVehiclesDamageMultiplier](Description#zombiesthrowingprojectileshandlervehiclesdamagemultiplier). Simply set the value of this parameter to "0".

Keep in mind that regardless of the conditions, the infected cannot make a throw more often than once every 3 seconds, and also cannot make a throw if the distance to the player exceeds 50 meters. This is done to save server FPS, reduce the distance of raycasts, and their quantity. He can also throw projectiles only in a state of chasing, otherwise he simply does not see the target.

Also, please note that damage from projectiles is not considered damage from infected, so all damage configuration multipliers of this mod will not affect this damage. This is done deliberately to avoid conflicts with mods that apply various statuses on damage from infected, such as virus Z, and these statuses should not be transmitted through projectiles.

If for some reason you are not satisfied with the projectile throwing system, or if another mod handles this mechanic and you want to disable it, you can do so using parameter [Zombies.ThrowingProjectilesHandlerIsActive](Description#zombiesthrowingprojectileshandlerisactive), simply set it to "0".

Within this mechanic, a pleasant bonus has been implemented: projectiles thrown by players at infected, animals or other players now deal damage to them. To disable this mechanic, you will need to deactivate the [Zombies.ThrowingProjectilesHandlerIsActive](Description#zombiesthrowingprojectileshandlerisactive) parameter for class "SurvivorBase":

    "ThrowingProjectilesHandlerIsActive": {
        "all": 1,
        "SurvivorBase": 0
    },

Alternatively, if you want to prevent infected from throwing projectiles but allow projectiles thrown by players to cause damage to infected, set this parameter as follows:

    "ThrowingProjectilesHandlerIsActive": {
        "all": 0,
        "SurvivorBase": 1
    },

***

### When dealing damage, the infected stun the player and apply various debuffs. How can I configure this?

**Stun mechanic.**

The purpose of this mechanic is to prevent players from easily engaging in close-quarters combat alone against a large number of infected. While facing a single infected may not pose much of a problem, dealing with three or more simultaneously may make players think twice before entering such a battle, just as they would in real life.

The essence of the mechanic is that when dealing damage, there is a chance that the infected may stun the player. The stun lasts for approximately a second, interrupting any player animation, whether it be climbing a ladder, reloading, entering a vehicle, block, or any other action, and deprives the player of the ability to do anything. Additionally, when stunned, the player is pushed away, potentially resulting in a fall from their elevated position.

The stun chance is adjustable in the parameters _Zombies.StunToPlayerChancePercent_ and _Zombies.StunToPlayerInBlockChancePercent_. Set the value of these parameters to "0" to disable this mechanic or choose a value that suits your preferences.

**Pain mechanic.**

When receiving damage to any part of the body (head, arms, legs, torso), the player incurs injuries (pain) that apply a specific debuff to that body part and may also result in a fracture/deep wound/bullet wound/internal bleeding.

You can completely disable the pain system (including fractures/deep wounds/bullet wounds/internal bleedings) by setting the parameter _Players.PainSystemIsActive_ to "0". Alternatively, you can customize the pain system by increasing limb recovery time or reducing limb damage. For instructions on how to do this, refer to the full description of the Inedia pain system, link below.

You can also disable any type of injury (fractures/deep wounds/bullet wounds/internal bleedings) individually. More detailed information can be found in the Inedia pain system description.

You can read more about the Inedia pain system [here](Inedia-Pain-system-guide).

If you want to disable the pain system for the damage that players receive from other players but leave it for damage from infected and animals, disable the parameter _Zombies.PainToPlayerHandlerIsActive_ for the class "SurvivorBase":

    "PainToPlayerHandlerIsActive": {
        "all": 1,
        "SurvivorBase": 0
    },

Please note that in the InediaInfectedAI modification, there is also damage from projectiles, which are separate entities themselves, inflicting damage and not affected by this parameter. To disable the pain inflicted by projectiles, it is necessary to set the projectile parameter _Parameters.TargetPainMultiplier_ to "0" for all projectiles.
The projectiles themselves are configured in the parameter [Zombies.ThrowingProjectiles](Description#zombiesthrowingprojectiles).

You can find information on how to configure the parameters for different types of entities [here](Description#configuration-options).

***

### How does the player pain system work?

Due to the fact that the section describing the pain system is very large, it has been moved [here](Inedia-Pain-system-guide).

***

### How to affect the Inedia pain system with custom medicines and statuses from other mods?

You can read about the medical items introduced by this mod, as well as how to make your own custom item medical with specific properties, [here](Inedia-Medicine-guide).

***

### Strong bosses and mutants on my server are dying from bleeding, how can I adjust this?

There are several ways to address this issue.

You can disable the bleeding system entirely for the specific boss/mutant by setting the parameter _Zombies.BloodHandlerIsActive_ to "0" for that boss/mutant:

    {
        "Zombies": {
            ...
            "BloodHandlerIsActive": {
                "all": 1,
                "YourBossMutantClass": 0
            },
            ...
        },
        ...
    }

If you don't want to disable the bleeding system entirely, you can try increasing the blood volume with _Zombies.BloodVolumeMl_ parameter. The default value for a regular zombie is 5000 ml. Depending on the boss's strength, you can set it to 10000, 20000, or even 30000, and the boss/mutant will bleed for a much longer time.

Alternatively, you can reduce _Zombies.BloodLossRateMaxMl_. The default value is 50 ml, which means that regardless of injuries, the bleeding rate cannot exceed 50 ml. Set it to 20 ml or even 10 ml, and the boss will bleed very slowly.

This modification also includes a mechanic for blood splatters when a creature takes damage, blood trails when a creature is wounded, and blood pools that form when a creature dies with an open wound. Using the _Zombies.BloodSplatParticlesIsActive_, _Zombies.BloodTrailParticlesIsActive_ and _Zombies.BloodPoolParticlesIsActive_ parameters, you can enable/disable this blood particles.

You can find information on how to configure the parameter for different types of zombies [here](Description#configuration-options).

More information on how the blood and bleeding system works can be found [here](#how-does-the-blood-and-bleeding-system-work).

***

### How does the blood and bleeding system work?

It's quite simple.

Unlike players, entities have only one parameter, which is the bleeding rate in seconds. Visually, it may seem like they have multiple bleedings, but in reality, "under the hood" they always have only one, and you can adjust the rate of this bleeding.

If you haven't changed the value of the _Zombies.BloodVolumeMl_ parameter - the initial blood volume (liters) in an entity is determined based on its weight:

`WeightKG * 0.07`

For regular infected, it's approximately 5000 ml, for a bear, it's 11000 ml, deer - 14000 ml, cow - 40000 ml.

After taking damage from a weapon that causes bleeding (the chance is determined from the vanilla ammo configuration "_CfgAmmo #AMMO# DamageApplied bleedThreshold_", head damage boosts the chance `3x`), the bleeding rate per second is determined by the formula:

`BleedingRatePerSecond = (DamageTakenHealth * DamageTakenBlood) * BleedingCoef`

_BleedingCoef_ - `0.0025` for melee attacks, `0.005` for other attacks.

_DamageTakenBlood_ - blood damage, which is determined from the vanilla configuration of the ammo that inflicts damage. Typically, it is equal to 100 for weapons capable of causing bleeding, but it depends on armor and distance to the target.

The _Zombies.DamageToZombie*Multiplier_ defense parameters do not affect the incurred damage used in the calculation.

Upon receiving the next hit, the existing bleeding rate is increased by the value determined by this formula.

If after taking damage, the bleeding rate is lower than _Zombies.BloodLossRateMinMl_, it's set to _Zombies.BloodLossRateMinMl_.

If after taking damage, the bleeding rate becomes higher than _Zombies.BloodLossRateMaxMl_, it's set to _Zombies.BloodLossRateMaxMl_.

Every second, the bleeding rate decreases by _Zombies.BloodLossRateRegenMl_, meaning the wounds are healing.

**Let's look at an example:**

An infected entity takes 30 Health and 100 Blood damage from a CZ75 pistol.

It starts bleeding at a rate of `30 * 100 * 0.005 = 15 ml/sec`.

Then, it's immediately hit for another 30 Health, so the bleeding rate becomes:

`15 ml/sec + (30 * 100 * 0.005) = 30 ml/sec`

Consequently, the entity loses 30 ml of blood every second.

And wounds heal every second, subtracting _Zombies.BloodLossRateRegenMl_ from this value. By default, it's set to 0.2 ml, so with default settings, the current wounds will heal in:

`30 / 0.2 = 150 seconds`

If an entity or infected loses more than **40%** of its blood within this time, they will die.

If an animal loses more than **30%** of its blood, it will switch to a trot, allowing players to catch or run away from it without sprinting.

If an infected loses more than **20%** of its blood, it won't be able to run quickly.
If an infected loses more than **30%** of its blood, it won't be able to run at all, only move at a walking pace. It also won't be able to jump, break doors, and its attacks will be half as strong.

Damage reduction will not work if parameter _Zombies.DamageToPlayerHandlerIsActive_ is disabled.

Speed reduction will not work if parameter _Zombies.SpeedHandlerIsActive_ is disabled.

With the _Zombies.BloodOnExplosiveDamageChancePercent_ parameter, you can adjust the chance that a creature will bleed when it takes damage from an explosion.

Using the _Zombies.BloodSplatParticlesIsActive_, _Zombies.BloodTrailParticlesIsActive_ and _Zombies.BloodPoolParticlesIsActive_ parameters, you can enable or disable the display of blood particles left by creatures under various conditions. For more details, refer to the parameter descriptions. By default, the blood particle remains unchanged for 400 seconds and then gradually fades over the course of 200 seconds. To prevent client performance drop from a large number of blood particles, a maximum limit of 1000 particles per client has been introduced. When this limit is exceeded, older particles are removed. That is, this will allow the player to enjoy the blood particles for a very long time without them disappearing while maintaining client performance. Ideally, these settings should have been moved to the client, but since I'm too lazy to create an interface, I didn't do that. However, on the server side, you can adjust these parameters globally for all clients using the _BloodParticlesLimit_ and _BloodParticleDurationSeconds_ global settings. Also, if the parameter _BloodParticleDurationSeconds_ is set to a value greater than zero, the vanilla blood particle system, as well as possibly some modded systems, will be disabled. To restore them, you need to set _BloodParticleDurationSeconds_ to "0", which will disable the blood particle system of "InediaInfectedAI".

<!--
The _Zombies.BloodParticlesBirthRateLimit_ parameter allows you to reduce the "bloodiness" of the particles by adjusting the amount per particle from 1 to 3. Simply put, reduce this number if the effects seem too gory to you, or you can decrease the bloodiness of effects for specific creatures, such as armored ones. This parameter does not affect client or server performance, as it does not limit the number of particles created. It only influences the visual aspect of the particle itself.
-->

***

### Strong bosses and mutants on my server get attack and speed debuffs from damage, how can I adjust this?

There are several ways to address this issue.

You can disable the injury system entirely for the specific boss/mutant by setting the parameter _Zombies.InjuryHandlerIsActive_ to "0".

If you don't want to disable the injury system entirely, you can try increasing the amount of damage the infected needs to incur limb injury (parameters _InjuryHandlerDamageThresholdToInjury(Arm/Leg)_). By default, it is set to 30 HP, but you can adjust it to 500 HP, 1000 HP, and beyond.

You can find information on how to configure the parameter for different types of zombies [here](Description#configuration-options).

Alternatively, you can influence the effects of the debuffs themselves. You can read more about the effects and the injury system itself [here](#how-does-the-injury-and-debuff-system-work).

***

### How does the injury and debuff system work?

When taking sufficient damage to a limb, the infected incurs limb injury.

Injury occurs if the damage to the limb exceeds _Zombies.InjuryHandlerDamageThresholdToInjuryArm_ for arms and _Zombies.InjuryHandlerDamageThresholdToInjuryLeg_ for legs.

The parameter _Zombies.InjuryHandlerDamageThresholdToInjury(Arm/Leg)_ sets the damage that the arm/leg needs to accumulate to sustain an injury.

For example, if the infected arm receives several hits, one for 10 HP and another for 15 HP, and the value of this parameter is 20 HP, then the arm will be injured because (10 + 15) > 20.

The _Zombies.DamageToZombie*Multiplier_ defense parameters do not affect the incurred damage used in the calculation.

After a limb has been injured, the following debuffs are applied:
* If only one of the arms is injured, multiplier _Zombies.InjuryHandlerInjuredOneArmAttackMultiplier_ is applied to the damage (default - 0.5), multiplier _Zombies.InjuryHandlerInjuredOneArmBreakingDoorChanceMultiplier_ is applied to the door break chance (default - 0.5), multiplier _Zombies.InjuryHandlerInjuredOneArmStunChanceMultiplier_ is applied to the player's stun chance, introduced by the mechanics of parameters _Zombies.StunToPlayer*_ (default - 0.5), multiplier _Zombies.InjuryHandlerInjuredOneArmPainMultiplier_ is applied to the pain damage, introduced by the mechanics of parameters _Zombies.PainToPlayer*_ (default - 0.5), multiplier _Zombies.InjuryHandlerInjuredOneArmBleedingChanceMultiplier_ is applied to the player's bleeding chance, introduced by the mechanics of parameters _Zombies.DamageToPlayerBleeding*_ (default - 0.5);
* If both arms are injured, multiplier _Zombies.InjuryHandlerInjuredBothArmsAttackMultiplier_ is applied to the damage (default - 0.2), multiplier _Zombies.InjuryHandlerInjuredBothArmsBreakingDoorChanceMultiplier_ is applied to the door break chance (default - 0), multiplier _Zombies.InjuryHandlerInjuredBothArmsStunChanceMultiplier_ is applied to the player's stun chance, introduced by the mechanics of parameters _Zombies.StunToPlayer*_ (default - 0), multiplier _Zombies.InjuryHandlerInjuredBothArmsPainMultiplier_ is applied to the pain damage, introduced by the mechanics of parameters _Zombies.PainToPlayer*_ (default - 0), multiplier _Zombies.InjuryHandlerInjuredBothArmsBleedingChanceMultiplier_ is applied to the player's bleeding chance, introduced by the mechanics of parameters _Zombies.DamageToPlayerBleeding*_ (default - 0);
* If only one leg is injured, the speed of the infected is limited to _Zombies.InjuryHandlerInjuredOneLegSpeedLimit_ (default - 2.1) and multiplier of _Zombies.InjuryHandlerInjuredOneLegJumpHeightMultiplier_ is applied to the maximum jump height of the infected (default - 0.5);
* If both legs are injured, the speed of the infected is limited to _Zombies.InjuryHandlerInjuredBothLegsSpeedLimit_ (default - 1) and multiplier of _Zombies.InjuryHandlerInjuredBothLegsJumpHeightMultiplier_ is applied to the maximum jump height of the infected (default - 0);

It is possible to specify which of the infected limbs will be damaged upon its spawn (parameters _Zombies.InjuryHandlerSpawnWithInjured(OneArm|BothArms|OneLeg|BothLegs)ChancePercent_).

There is also an option to set the time in seconds, after which the limb of the infected will completely regenerate after being damaged (parameters _Zombies.InjuryHandlerRestoreInjured(Arm|Leg)AfterSeconds_).

With the _Zombies.InjuryHandlerInjuryOnExplosiveDamageChancePercent_ parameter, you can adjust the chance that a creature takes limb damage when it takes damage from an explosion.

Injury system works for animals too, but in a simplified form, only parameters _Zombies.InjuryHandlerIsActive_ and _Zombies.InjuryHandlerDamageThresholdToInjuryLeg_ are configurable. Accordingly, only one debuff works for animals - the speed limit on leg damage.

Damage reduction will not work if parameter _Zombies.DamageToPlayerHandlerIsActive_ is disabled.

The bleeding chance will not decrease if parameter _Zombies.DamageToPlayerBleedingHandlerIsActive_ is disabled.

Speed reduction will not work if parameter _Zombies.SpeedHandlerIsActive_ is disabled.

***

### How can I activate the search mode for infected in my scripts?

For this purpose, the class _InediaInfectedAI_IrritantsManager_ has a special static method _ModMassSearchActivation(...)_:

    class InediaInfectedAI_IrritantsManager
    {
        ...

        static void ModMassSearchActivation(
            vector fromPosition,
            float irritantRadius,
            int irritantType = 0,
            int irritantPriority = 777,
            vector toPosition = vector.Zero
        )
        { ... }

        ...
    }

Where:
* **fromPosition** - The epicenter of the irritation sphere is usually the coordinates of the irritant's position;
* **irritantRadius** - The radius of the irritation sphere, with a maximum value of 1000 meters;
* **irritantType** - Irritant type: "1" - visual, "2" - noise, "0" - custom. The irritant type affects the suppression and reduction of the radius by various conditions, such as weather or the irritant being inside a building. If type "0" is chosen, no conditions will affect the radius of this irritant.
* **irritantPriority** - Irritant priority. You can read more about what priority is in the text at the bottom of the [linked page](Description#zombiescustomirritants).
* **toPosition** - In 99% of cases, this parameter is not used. If not specified, it will be set equal to _fromPosition_. The purpose of this parameter is to allow you to specify the coordinates where the search mode target will be set. For example, we can select infected in one position but send them not to the center of the irritation sphere, but to any other position. This works similarly to a strategy game: you select the infected with a sphere at the center of _fromPosition_ and send them to the coordinates of _toPosition_. If _fromPosition_ and _toPosition_ are the same, or _toPosition_ is not specified, they will go to the center of the selection sphere.

Exapmle:

For example, we have an object that emits a loud noise within a radius of 120 meters at a certain moment. In this case, when the noise trigger activates, we simply call the aforementioned static method for this object:

    InediaInfectedAI_IrritantsManager.ModMassSearchActivation(object.GetPosition(), 120, 2);

***

### How does vanilla weather affect the mechanics of this mod?

- **Rain**
    - Linearly reduces the effectiveness of noise irritants by up to 60% depending on the intensity of the rain. For example, at 100% rain intensity, the range of noise irritants will be only 40% of their default range.
    - Linearly reduces the effectiveness of visual irritants by up to 30% depending on the intensity of the rain. For example, at 100% rain intensity, the range of visual irritants will be only 70% of their default range.
    - Affects the smell detection radius of infected, linearly reducing it by up to 100% depending on the intensity of the rain. For example, at 100% rain intensity, the smell detection radius of the infected will be zero.
    - Affects the lifespan of player smells, linearly reducing it by up to 100% depending on the intensity of the rain. For example, at 100% rain intensity, the player will not emit any smells.

- **Snowfall (introduced in DayZ 1.26)**
    - The effect of snowfall on noise irritants depends on the wind speed:
        - Wind speed up to 10 m/s (light wind):
            - Linearly reduces the effectiveness of noise irritants by up to 20% depending on the intensity of the snowfall. For example, at 100% snowfall intensity, the range of noise irritants will be 80% of their default range.
        - Wind speed from 10 to 15 m/s (light snowstorm):
            - Linearly reduces the effectiveness of noise irritants by up to 40% depending on the intensity of the snowfall. For example, at 100% snowfall intensity, the range of noise irritants will be 60% of their default range.
        - Wind speed above 15 m/s (heavy snowstorm):
            - Linearly reduces the effectiveness of noise irritants by up to 60% depending on the intensity of the snowfall. For example, at 100% snowfall intensity, the range of noise irritants will be 40% of their default range.
    - Linearly reduces the effectiveness of visual irritants by up to 60% depending on the intensity of the snowfall. For example, at 100% snowfall intensity, the range of visual irritants will be only 40% of their default range.
    - Affects the smell detection radius of infected, linearly reducing it by up to 60% depending on the intensity of the snowfall. For example, at 100% snowfall intensity, the smell detection radius of the infected will be 40% of its original size.
    - Affects the lifespan of player smells, linearly reducing it by up to 60% depending on the intensity of the snowfall. For example, at 100% snowfall intensity, the lifespan of player smells will be only 40% of their original lifespan.

- **Fog**
    - Does not affect visual and noise irritants.
    - Affects the smell detection radius of infected, linearly reducing it by up to 30% depending on the intensity of the fog. For example, at 100% fog intensity, the smell detection radius of the infected will be 70% of its original size.
    - Affects the lifespan of player smells, linearly reducing it by up to 30% depending on the intensity of the fog. For example, at 100% fog intensity, the lifespan of player smells will be only 70% of their original lifespan.

- **Wind**
    - Affects the effectiveness of noise irritants during snowfall, for more details, see the snowfall description.
    - Affects the direction and speed of player smell dispersal. Smell objects spread at the speed of the wind in the direction of the wind's movement.

The percentage impact of different factors on the same irritant is not added but multiplied. For example, if rain reduces the effectiveness of noise irritants to 40% of their original effectiveness, and snowfall reduces it to 70%, the final effectiveness will be: 40% * 70% = 28%.

***
