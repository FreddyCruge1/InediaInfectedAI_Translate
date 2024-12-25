# Configuration guide

First, you need to add your SteamID to the administrators config to gain access to additional commands (entered in the game chat) and features of this mod. For instance, to be able to reload the mod config without restarting the server, or to receive information in the chat about the damage taken by a zombie/animal/survivor. Also, in case of errors in the configuration file, you as an administrator will receive a message about this in the game chat when logging into the server. Find out more on how to do this [here](Description#admin-privileges-and-commands).

[Here](Description#configuration-file) you can find information about the mod configuration file, its location, nuances of configuring it, possible errors and reasons why configuration parameters may be ignored, as well as nuances of updating to a new version.

If you've changed a parameter and want to revert it back without deleting the current configuration file, you can check the current configuration file with default values [here](Default-configuration-file). It gets updated after each modification update.

Now regarding its configuration...

First and foremost, it's important to understand that ⚠ **ANY** ⚠ _Zombies.*_ parameter (excluding the _Zombies.Groups_, _Zombies.CustomIrritants_ and _Zombies.ThrowingProjectiles_ configuration lists) can be configured for various types of zombies, while some parameters are also configurable for animals and survivors, as typically indicated in the parameter description.

Instructions on configuring parameters for different types of zombies can be found [here](Description#configuration-options).

Next, I will simply provide descriptions of the features and mechanics present in the modification and provide links to the parameters used to configure these features.

By default, the majority of these features are enabled (unless stated otherwise) and balanced for hardcore gameplay. There is no need to manually enable or disable them unless a specific mechanic doesn't suit your preferences.

* Settings for breaking doors, lockpicked doors, prohibiting the breaking of certain doors, and so on, are controlled by the parameters _Zombies.BreakingDoors*_. ⚠️ If your server uses custom doors opened by keycards - make sure to read [this FAQ item](FAQ#key-card-doors-can-be-opened-using-the-quiet-door-opening-function-and-can-also-be-kicked-in-by-the-infected-how-to-fix-it).
    * [Zombies.BreakingDoors*](Description#zombiesbreakingdoorshandlerisactive)
* When attempting to open a door destroyed by infected, the player receives an informational message. With this parameter, you can customize the type of this message (pop-up notification, in-game chat, disable the message):
    * [Players.DestroyedDoorNotificationType](Description#playersdestroyeddoornotificationtype)
* The HP of the zombies (separate setting for legs HP), as well as the defence of zombies against players, vehicles, and explosions for various body parts, are configured using these parameters.
    * [Zombies.DamageToZombie*](Description#zombiesdamagetozombiehandlerisactive)
* Infected and animals in this mod have a blood system, meaning they can die from blood loss when wounded. Using these parameters, you can configure various aspects of the blood system, such as blood volume, bleeding severity, regeneration rate. You can also disable blood splatters when creatures take damage or turn off the blood trails that wounded creatures leave on the ground. Additionally, if your clients experience performance issues due to a large number of blood particles, there are server parameters that allow you to globally configure a limit on the number of particles and their duration for all clients (_BloodParticlesLimit_, _BloodParticleDurationSeconds_). Ideally, these settings should have been moved to the client, but since I'm too lazy to create an interface, I didn't do that. If interested, you can read about how the blood system for infected and animals works [here](FAQ#how-does-the-blood-and-bleeding-system-work). ⚠️ If you have mutants or bosses on your server, read [this](FAQ#strong-bosses-and-mutants-on-my-server-are-dying-from-bleeding-how-can-i-adjust-this).
    * [Zombies.Blood*](Description#zombiesbloodhandlerisactive)
    * [BloodParticlesLimit](Description#bloodparticleslimit)
    * [BloodParticleDurationSeconds](Description#bloodparticledurationseconds)
* When infected take damage to their arms or legs from players, they receive various debuffs depending on the limb. These settings allow you to configure the strength of debuffs for damaged limbs of infected, as well as the spawning of infected with already damaged limbs. If you're interested in how the system of infected injury and debuffs works, you can read about it [here](FAQ#how-does-the-injury-and-debuff-system-work). ⚠️ If you have mutants or bosses on your server, read [this](FAQ#strong-bosses-and-mutants-on-my-server-get-attack-and-speed-debuffs-from-damage-how-can-i-adjust-this).
    * [Zombies.InjuryHandler*](Description#zombiesinjuryhandlerisactive)
* Settings for infected damage upon falling from height.
    * [Zombies.FallHandler*](Description#zombiesfallhandlerisactive)
* Infected in close combat have become slightly smarter.
Now they recklessly rush only towards the player who has turned their back to them.
However, if the player is facing them directly, the infected analyze the threat and may slow down at a certain moment, thereby dodging a powerful blow.
This will create significant problems for those accustomed to killing infected with a precise head strike as they approach, already reflexively sensing when to strike.
Now battles will become less predictable and more intense, as even a single infected under certain circumstances can inflict damage regardless of the player's experience and level of preparation in close combat.
Using the following parameters, you can adjust the infected slow chance and cooldown, or disable this mechanic altogether.
    * [Zombies.MeleeAttacksDodge*](Description#zombiesmeleeattacksdodgehandlerisactive)
* In this modification, there is a mechanic that allows infected to jump toward players when approaching them, attempting to stun. This adds extra challenges in dealing with the infected, as they gain an attack that always stuns the player while bringing the infected right up close.
Using the following parameters, you can adjust the jump probability and cooldown, or disable this mechanic altogether.
    * [Zombies.JumpAttack*](Description#zombiesjumpattackhandlerisactive)
* Settings for various types of damage (health, shock, stamina, bleeding) inflicted by zombies on players.
    * [Zombies.DamageToPlayer*](Description#zombiesdamagetoplayerhandlerisactive)
* The ability for infected to attack unconscious players (by default, this option is enabled, meaning they will attack unconscious players).
    * [Zombies.AttackPlayersUnconscious](Description#zombiesattackplayersunconscious)
* When hit by zombies, the player may become stunned (animation is interrupted, for about a second they cannot do anything, and they may also be pushed back and potentially fall from their elevated position). These parameters can be used to adjust the chance or disable this mechanic altogether.
    * [Zombies.StunToPlayer*](Description#zombiesstuntoplayerchancepercent)
* If you need the weapon to be knocked out of the player's hands with a certain chance when they receive damage from a creature, use these parameters. By default, these chances are set to 0%, meaning creatures do not knock weapons out of the character's hands. Do not confuse these parameters with parameter [Zombies.PainToPlayerArms*DisarmMultiplier](Description#zombiespaintoplayerarmsdisarmmultiplier), which depends on the Inedia pain system and only works when the hands are damaged.
    * [Zombies.DisarmToPlayer*ChancePercent](Description#zombiesdisarmtoplayerchancepercent)
* When receiving damage from infected or animals - with a certain probability and under specific conditions, players may acquire agents of various diseases. Using these parameters, you can configure which agents are transmitted, the amount of agents transmitted, the transmission probability, and much more. Or you can completely disable this mechanic by setting parameter _Zombies.DiseasesToPlayerHandlerIsActive_ to "0". For further details, refer to the parameter descriptions.
    * [Zombies.DiseasesToPlayerHandlerIsActive](Description#zombiesdiseasestoplayerhandlerisactive)
    * [Zombies.DiseasesToPlayerAgents](Description#zombiesdiseasestoplayeragents)
* Characters have a pain mechanic. That is, when taking damage to limbs, they will receive various debuffs depending on the limb and the extent of its damage. These are debuffs such as reduced movement speed, decreased attack speed, stamina depletion, and disarming items from the player's arms, depending on the type of damaged limb. These debuffs also activated from player and animal damage, it's enabled by default, and if you're not satisfied with that, it can be individually disabled for players, zombies, or both. This mod also introduces a system of fractures, deep wounds, and gunshot injuries for each limb, as well as internal bleeding. If you want to completely disable the pain system, set the parameter _Players.PainSystemIsActive_ to "0". If for any reason you want to disable other systems, you can set _Players.LimbsBreakSystemIsActive_, _Players.LimbsDeepWoundSystemIsActive_, _Players.LimbsBulletSystemIsActive_, or _Players.InternalBleedingSystemIsActive_ to "0". Additionally, you can disable these systems for individual body parts separately. It is also possible to adjust the chance of fractures and deep wounds for each type of creature individually using the parameters _Zombies.PainToPlayerLimbsBreakChancesMultiplier_ and _Zombies.PainToPlayerLimbsDeepWoundChancesMultiplier_. Also, in case you're wondering, you can read more about the pain mechanic itself [here](Inedia-Pain-system-guide). You can also read about the medical system affecting pain and injuries introduced by this mod [here](Inedia-Medicine-guide).
    * [Zombies.PainToPlayer*](Description#zombiespaintoplayerhandlerisactive)
    * [Zombies.PainToPlayerLimbsBreakChancesMultiplier](Description#zombiespaintoplayerlimbsbreakchancesmultiplier)
    * [Zombies.PainToPlayerLimbsDeepWoundChancesMultiplier](Description#zombiespaintoplayerlimbsdeepwoundchancesmultiplier)
    * [Players.PainSystemIsActive](Description#playerspainsystemisactive)
    * [Players.LimbsBreakSystemIsActive](Description#playerslimbsbreaksystemisactive)
    * [Players.LimbsDeepWoundSystemIsActive](Description#playerslimbsdeepwoundsystemisactive)
    * [Players.LimbsBulletSystemIsActive](Description#playerslimbsbulletsystemisactive)
    * [Players.InternalBleedingSystemIsActive](Description#playersinternalbleedingsystemisactive)
* Settings for jumping infected up and down (уou can configure the maximum jump height, jump frequency, and jump chance).
Also, please note that there is a parameter _Zombies.StuckJumpHandlerIsActive_ that allows infected to jump towards the player while attempting to escape from a stuck position. This parameter is independent of the up and down jump handlers and must be disabled separately.
    * [Zombies.UpJump*](Description#zombiesupjumphandlerisactive)
    * [Zombies.DownJump*](Description#zombiesdownjumphandlerisactive)
    * [Zombies.StuckJumpHandlerIsActive](Description#zombiesstuckjumphandlerisactive)
* In this modification, infected have the ability to throw projectiles at players. Similarly, players can throw projectiles at infected and animals. Below are the settings related to this mechanic. You can also refer to the [FAQ section](FAQ#how-to-configure-the-projectiles-throwing-system) for configuring this mechanic.
    * [Zombies.ThrowingProjectiles](Description#zombiesthrowingprojectiles)
    * [Zombies.ThrowingProjectilesHandler*](Description#zombiesthrowingprojectileshandlerisactive)
* If, for some reason, you are not satisfied with the projectile throwing mechanics or jumping mechanics, this modification offers another mechanic that prevents players from killing infected while sitting on obstacles without consequences. This is the mechanic of ranged attacks, whereby infected will reach out to attack the player at approximately the same distance at which the player reaches them. By default, it is turned off, but you can enable it, adjust the radius, obstacle height, or leave the parameters at their default values.
    * [Zombies.RangeAttacksHandler*](Description#zombiesrangeattackshandlerisactive)
* With these parameters, you can adjust how zombies are attracted by the screams of other zombies.
    * [Zombies.Scream*](Description#zombiesscreamhandlerisactive)
* Adjusting the zombie movement speed in different modes.
    * [Zombies.Speed*](Description#zombiesspeedhandlerisactive)
* Settings for infected smell perception, as well as other mechanics related to smells.
    * [Zombies.Smells*](Description#zombiessmellshandlerisactive)
* The ability for infected to attack animals. If your server features custom animals and you want to flexibly configure their friendship with the infected, pay attention to parameter [Zombies.AttackAnimalsCustom](Description#zombiesattackanimalscustom).
    * [Zombies.AttackAnimals*](Description#zombiesattackanimalshandlerisactive)
* Configuring the relationship between zombies/animals and NPCs (including AI-controlled bots).
    * [Zombies.FriendlyNPC](Description#zombiesfriendlynpc)
* Settings for zombie attacks on vehicles, vehicle damage, attacks on players inside vehicles, vehicle durability, as well as damage from collisions with vehicles. Also, if you're interested, you can read [here](FAQ#how-does-the-logic-of-vehicle-attack-work) about how the logic of attacking vehicles works.
    * [Zombies.AttackCar*](Description#zombiesattackcarhandlerisactive)
* In the _Vehicles.*_ section, there is an option to influence the noise emitted by the vehicle, flexibly adjust the radius of attracting zombies by the noise of various vehicles. Also, in the _Vehicles.*_ section, you can influence the sound emitted by the vehicle when colliding with infected and the vehicle slowdown when colliding with infected.
    * [Vehicles.Noise](Description#vehiclesnoise)
    * [Vehicles.CollisionsSoundThreshold](Description#vehiclescollisionssoundthreshold)
    * [Vehicles.CollisionsSpeedReductionMultiplier](Description#vehiclescollisionsspeedreductionmultiplier)
* Infected can react to various irritants, such as light and noise items, player noise, door noise, the noise of another infected's body falling, and the screaming of another infected. Their reaction to such irritants, as well as their ability to destroy light and noise items, is customized by the _Zombies.React*_ parameters.
    * [Zombies.React*](Description#zombiesreacthandlerisactive)
    * [Zombies.ReactAndDestroy*](Description#zombiesreactanddestroyflashlightsvisual)
* There is also an option to configure custom irritants, such as mod items that can be turned on and off.
    * [Zombies.CustomIrritants](Description#zombiescustomirritants)
    * [Zombies.ReactCustomIrritants](Description#zombiesreactcustomirritants)
* You can also influence the time after which an infected will lose interest in the irritant if it cannot reach it. This is a global parameter and cannot be configured for a specific type of zombie.
    * [LossInterestToIrritantAfterSeconds](Description#lossinteresttoirritantafterseconds)
* Since infected in the game can hear the sound of doors opening/closing, there is a mechanic for silently opening/closing doors in the game. If you disable the mechanic of quiet door opening/closing for players, zombies will also stop hearing the sound of door opening/closing. By default, the quiet door opening function is disabled in the modification, and only the quiet door closing function is active. However, if for any reason you wish to enable the quiet door opening function, please make sure to read [this FAQ item](FAQ#key-card-doors-can-be-opened-using-the-quiet-door-opening-function-and-can-also-be-kicked-in-by-the-infected-how-to-fix-it).
    * [Players.QuietDoorOpeningMechanic*](Description#playersquietdooropeningmechanicisactive)
* You can enable or disable the ability to butcher zombies like animals, and also configure the list of items that will drop from them.
    * [Zombies.CanBeButchered](Description#zombiescanbebutchered)
    * [Zombies.Butchering*](Description#zombiesbutcheringseconds)
    * [Zombies.ItemsAfterButchering](Description#zombiesitemsafterbutchering)
* When taking damage from zombies, the player's camera shakes, but this can be disabled.
    * [Zombies.CameraShakeToPlayerIntensity](Description#zombiescamerashaketoplayerintensity)
* There is also the option to configure the knockback of zombies when they receive damage (shock).
    * [Zombies.DamageToZombieShockToStun*](Description#zombiesdamagetozombieshocktostunhandlerisactive)
* There is a possibility to flexibly adjust the damage of various weapons against different types of zombies. These settings only affect damage to zombies.
    * [Zombies.DamageToZombieWeaponsMultipliers](Description#zombiesdamagetozombieweaponsmultipliers)
* There is an option to configure the resistance of zombies to chemical zones.
    * [Zombies.ResistContaminatedEffect](Description#zombiesresistcontaminatedeffect)
* You can disable players ability to cripple infected legs, as well as configure the spawn of zombies with crippled legs.
    * [Zombies.AllowCrawling](Description#zombiesallowcrawling)
    * [Zombies.RespawnInCrawlingChancePercent](Description#zombiesrespawnincrawlingchancepercent)
* You can disable or enable searching of zombies/players bodies by players, as well as adjust the search time, or forbid searching if the player is holding something in their hands. You can also enable/disable debuffs if a player searches a body without gloves or a mask.
    * [Zombies.SearchBody*](Description#zombiessearchbodytoviewcargo)
    * [Players.SearchBodyToViewCargo](Description#playerssearchbodytoviewcargo)
* If necessary, you can disable the ability for a player to perform a backstab on an infected.
    * [Zombies.CanBeBackstabbed*](Description#zombiescanbebackstabbedhandlerisactive)
* The following parameters can affect the vanilla visibility multiplier of a player by infected, for any time of day.
    * [Zombies.VisionRangeMultiplier*](Description#zombiesvisionrangemultiplierday)
* If necessary, you can configure the size of infected, which will be randomly generated within the specified parameters from and to. By default, this option is disabled.
    * [Zombies.Size*](Description#zombiessizehandlerisactive)
* There is an option to influence the multiplier of the vanilla noise level emitted by the player. In general, if you are interested in making infected less sensitive to player sounds, you need to study [this FAQ item](FAQ#how-to-make-zombies-less-sensitive-to-player-noise), as several mechanics are responsible for this.
    * [Players.NoiseMultiplier*](Description#playersnoisemultiplierday)
* There is an option to make any clothing camouflage, affecting its visibility multipliers. It is possible to set the multiplier to "0", and infected will not see the player at all.
    * [Players.CamoClothingVisibilityMultipliers](Description#playerscamoclothingvisibilitymultipliers)
* Settings for the search sphere and extended search mode. Typically, this is not required, as the functionality has been thoroughly tested and is currently well-balanced and functioning as intended. You can learn about what search spheres are by watching [this video](https://youtu.be/bjz2MtyO4Co?t=268) (enable subtitles).
    * [Zombies.SearchSphere*](Description#zombiessearchhandlerisactive)
* This modification uses its own custom damage distribution system for limbs. For example, infected in this modification can attack the player's head, but if the player is blocking, the damage is redirected to the arms. If for any reason you don't like this mechanic, if you don't like that infected deal damage to the head and damage headgear, and you want to revert to the vanilla system, you can do so using this parameter.
    * [Players.OverrideGetHitComponentChances](Description#playersoverridegethitcomponentchances)
* In this modification, pathfinding for infected is enabled by default both on water and underwater. This is done through the game config (config.cpp) and cannot be disabled through the configuration of this modification. However, you can disable their ability to walk on water, for this, please refer to [this FAQ item](FAQ#infected-walk-in-water-and-underwater-how-can-this-be-fixed).
