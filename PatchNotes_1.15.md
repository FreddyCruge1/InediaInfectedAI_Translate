### ☑️ 1) Many issues related to the DayZ 1.26 update have been fixed

Interaction between Inedia-irritants and the new vanilla snowfall mechanics has been added.

The impact of rain and snowfall on the visual detection of other creatures by the infected has also been added, which, as it turned out, was not present in the vanilla game.

You can read more about how the weather now affects Inedia-irritants here: https://github.com/ysaroka/InediaInfectedAI/wiki/FAQ#how-does-vanilla-weather-affect-the-mechanics-of-this-mod

The admin commands **\isnow <0...100>** and **\iwind <0...20>** have been added, allowing control over snowfall and wind levels for testing irritants.

### ☑️ 2) A major refactoring of the irritants functionality

- The slow method of searching for objects within a certain radius, _GetGame().GetObjectsAtPosition3D(...)_, has been replaced with _DayZPlayerUtils.SceneGetEntitiesInBox(...)_, which works thousands of times faster. As a result, the impact of irritants on the server's FPS has been significantly reduced.
  This gave me the idea to completely redesign the irritant functionality, allowing for practically unlimited configurable reaction radii for the infected, as well as adding levels of alertness for the infected. However, since this would break backward compatibility with the configs, I decided against it for now. A future version 2.0 of the modification with a new irritant system and many possibilities and optimizations in the config structure may be released, but for the time being, this is on hold.
- If anyone has used the method _ZombieBase.InediaInfectedAI_MassSearchActivation(...)_ in their scripts, please note that it has been moved to the _InediaInfectedAI_IrritantsManager_ class, and its format has changed - the priority and irritant radius parameters have been removed. Yes, I broke backward compatibility, but I had no other choice.
  In general, I do not recommend using the _ZombieBase.InediaInfectedAI_MassSearchActivation(...)_ method. Instead, to activate search mode using your custom triggers, you should use the new method specifically created for this purpose, _InediaInfectedAI_IrritantsManager.ModMassSearchActivation(...)_.
  More details here:

  https://github.com/ysaroka/InediaInfectedAI/wiki/FAQ#how-can-i-activate-the-search-mode-for-infected-in-my-scripts

Also a command **\iirrdebug** has been added, allowing the activation of debug message output for various Inedia-irritants affecting the activation of the infected search mode (irritant name, irritant type, irritant radius, etc.). Note that the command shows a fixed radius of effect for the irritant, without taking into account the sensitivity of the infected, which is configured individually for each infected.

### ☑️ 3) An extended limb fracture system has been added as part of the Inedia pain system

In addition to leg fractures, there are now rib fractures, arm fractures, and skull cracks.

For compatibility with other mods, leg fracture remain fully vanilla and the duration of the fracture cannot be configured through this mod. Only the vanilla leg fracture icon has been replaced to match the style of Inedia extended fractures.

As for Inedia fractures, they do not require a splint for treatment, it’s strange to apply a splint to ribs or the head 😂, as for the hands, refer to update point ☑️ 4. All fractures heal over time, while being accompanied by several specific debuffs and intensifying some pain debuff effects. They also lock the pain level in the limb at 80% while the fracture is active, just like the leg fracture previously locked pain in the legs while active.

Also the logic for obtaining a fracture has been changed, now the very small chance of a fracture starts at 30% limb damage (orange level), but it is non-linear and increases significantly only by 80%.

You can find information about fractures in the updated description of the pain system here: https://github.com/ysaroka/InediaInfectedAI/wiki/FAQ#how-does-the-player-pain-system-work

You can also completely disable the extended fracture system by setting the parameter _Players.LimbsBreakChancesMultiplier_ to "0". In this case, only the vanilla leg fracture will remain, and the vanilla icon will return. In other words, limb pain will no longer affect fractures at all, including leg fractures and creatures will no longer break the player's limbs (including legs) by any method other than the vanilla one - keep that in mind. Also with this parameter, you can globally influence the chances of limb fractures. For example, by setting this multiplier to "0.5", you reduce the chances by half, and by setting it to "2", you double them. You can experiment and choose the values that suit you. In the default configuration, based on my tests, a value of "1" is ideal.

https://github.com/ysaroka/InediaInfectedAI/wiki/Description#playerslimbsbreakchancesmultiplier

Alternatively, you can disable the extended fracture for any body parts by setting the parameter _Players.#LIMB#BreakDurationSeconds_ to "0" (this same parameter can be used to change the fracture's active duration after it is sustained, with the default being 1000 seconds):

https://github.com/ysaroka/InediaInfectedAI/wiki/Description#playersheadbreakdurationseconds

### ☑️ 4) Now characters with arms pain receive shock damage during actions and emit pain sounds

When a character has pain in their hands, they will receive shock damage while performing various animated actions (crafting, reloading weapons, opening/closing doors, chopping wood, etc.), and they will also emit sounds of pain.

The shock damage depends on the pain in the hands, but generally will not lead to serious problems, except in cases where the character has a hand fracture, which multiplies the shock damage by "2". I thought for a long time about whether to add the option to remove the hand fracture debuffs by applying a splint and decided not to include this feature. In reality, a splint wouldn't restore hand functionality and would actually make it harder to perform any actions since a splint is not a bionic hand, after all. As for some form of treatment, codeine can slightly reduce the pain, thereby decreasing the shock from performing actions with a broken hand, essentially serving as a "way out" in situations where a broken hand prevents critical actions due to the player losing consciousness. And with morphine, you can perform any actions with a broken hand without consequences.

Additionally, a new parameter, _Players.ArmsPainShockDamageActions_, has been added, allowing you to configure shock damage for any Action.

More details here: https://github.com/ysaroka/InediaInfectedAI/wiki/Description#playersarmspainshockdamageactions

You can always find the default values for this parameter in the default configuration file: https://github.com/ysaroka/InediaInfectedAI/wiki/Default-configuration-file

### ☑️ 5) The parameter _Zombies.DamageToZombieHealthPoints_ has been added, allowing you to specify the HP for any infected

This parameter simplifies the global increase in infected durability, regardless of multipliers.
By default, the value of this parameter is set to "-1", meaning the HP are taken from the vanilla infected configuration.

https://github.com/ysaroka/InediaInfectedAI/wiki/Description#zombiesdamagetozombiehealthpoints

The parameter _Zombies.DamageToZombieHealthPointsLeg_ has also been added, allowing you to set the health of the infected's legs. When any leg loses all of its health, the infected will switch to crawling mode.

By default, the value of this parameter is set to "-1", meaning the leg health is equal to the global health value.

https://github.com/ysaroka/InediaInfectedAI/wiki/Description#zombiesdamagetozombiehealthpointsleg

The implementation of this change required a very significant overhaul of the damage control functionality, which took about 1/4 of the time spent on this update, especially in terms of compatibility with mods that track creature kills, such as "DayZ-Expansion-Quests".

Therefore, if you are using such mods, I recommend double-checking that all creature kill quests are functioning correctly. I tested a variety of possible test cases, such as kills in different body parts or backstab kills, and everything seems to be working fine, but I might have missed something.

Due to the overhaul of the damage reception system, "InediaInfectedAI" now tries to account for damage inflicted on the infected by other mods and adjusts it with multipliers. Therefore, "InediaInfectedAI" will now work correctly with "Syberia Project" with the _Zombies.DamageToZombieHandlerIsActive_ parameter enabled and take into account Syberia perks. As a result, the compatibility guide has been updated, and the recommendation to disable this parameter has been removed.

However, this will not work with PvZ, as it has its own HP control system.

Also a command **\idmgdebug** has been added, which allows you to enable the damage debugging mode for incoming damage to infected/animals/players.
When activated, administrators will receive chat messages with information about the damage received by the infected or players (source class, ammo, target class, damage zone, damage, shock damage, remaining HP).

### ☑️ 6) The mechanic of infected attacking unconscious players kept bothering me

If enabled, it became too hardcore, and if disabled, it was too easy and allowed for abuse in certain situations.
Thus, a middle ground was found, and the parameter _Zombies.AttackPlayersUnconsciousHitsLimit_ was introduced.
This parameter allows you to specify the number of hits that infected are allowed to make on the player while the player is unconscious.
This parameter prevents the infected from hitting the player more than the specified number of times.
It works as follows:
* The player has a counter that tracks the number of hits received while unconscious, which is global for all infected.
* When the player loses consciousness, this counter is reset.
* The infected checks the value of this parameter (which can be adjusted for any type of infected) against the counter, and if the parameter is greater, the infected hits the player and increases the counter until it reaches the parameter's value.

Thus, the player loses the ability to safely lose consciousness, as even when unconscious, they can be noticed by the infected and the counter will be completed.
Now, losing consciousness will always cost the player a certain number of hits, making them think twice about whether it's worth the risk. And at least in the behavior of the zombie, some logic appears. It hits the body for a while, after which it thinks the victim is dead and loses interest in them, as they cannot determine whether the victim is alive or not. There will also no longer be illogical behavior where a zombie immediately loses interest in the prey it's chasing if the prey loses consciousness. With this parameter, the infected will always hit a target a certain number of times before losing interest, preventing her from "hiding" in unconsciousness.

According to my tests, the ideal value for this parameter in the default configuration was "5" hits, which generally prevents the player from dying but leaves serious consequences from losing consciousness, often resulting in fractures. As a result, players will think twice before engaging in an unequal fight, hoping for a quick loss of consciousness if things go wrong.

With the new fracture mechanics, intentionally losing consciousness has become even easier, so I recommend enabling the _Zombies.AttackPlayersUnconscious_ parameter and setting the "Zombies.AttackPlayersUnconsciousHitsLimit" parameter to approximately "5" (depends on how your pain multipliers are configured).

More details:
https://github.com/ysaroka/InediaInfectedAI/wiki/Description#zombiesattackplayersunconscioushitslimit

⚠️ Please note that if you have enabled infected to finish off unconscious players (_Zombies.AttackPlayersUnconscious_ => 1), after this update they will stop doing so and will only strike up to 5 times, as the default value of this parameter is set to "5". To revert things back to how they were, set the value of this new parameter to "-1" and the infected will attack the unconscious player as before until they die.

⚠️⚠️⚠️ And note that if you are using the "DayZ-Bicycle" mod, you won't be able to activate the functionality of zombies attacking unconscious players, as this mod blocks that functionality. I contacted the author and he mentioned that this issue will be fixed in the next update. Therefore, if you are using "DayZ-Bicycle", the "Zombies.AttackPlayersUnconsciousHitsLimit" parameter will not work and is pointless until the "DayZ-Bicycle" update.

### ☑️ 7) Visual improvements to the bleeding mechanics

- Now, when an infected/animal/player is hit by a bullet, if the bullet passes through the body, the splatter is directed towards the wall in the direction the bullet exited. If the bullet stays inside the body, or if the creature takes damage from melee weapons, the blood splatters randomly within a 2-3-meter radius. If there are no walls within that radius, the blood splatters on the ground near the creature.
The amount and size of the splatters depend on the weapon and the blood damage it deals. For example, blunt weapons like bats or fists will result in fewer splatters, while knives will cause a lot more. Additionally, if the bullet passes through, pieces of flesh appear on the wall, some of which drip down. :)
Using the [Zombies.BloodSplatParticlesIsActive](https://github.com/ysaroka/InediaInfectedAI/wiki/Description#zombiesbloodsplatparticlesisactive) parameter, you can disable/enable this mechanic.
- Now infected/animals/players leave blood trails on the ground depending on the severity of bleeding. The size of the drops depends on the intensity of the bleeding.
Using the [Zombies.BloodTrailParticlesIsActive](https://github.com/ysaroka/InediaInfectedAI/wiki/Description#zombiesbloodtrailparticlesisactive) parameter, you can disable this mechanic.
- Now infected/animals/players leave blood pools on the ground when they die while actively bleeding. The size and spread of the pool depend on the intensity of the bleeding at the moment of death. Using the [Zombies.BloodPoolParticlesIsActive](https://github.com/ysaroka/InediaInfectedAI/wiki/Description#zombiesbloodpoolparticlesisactive) parameter, you can disable this mechanic.

By default, the blood particle remains unchanged for 400 seconds and then gradually fades over the course of 200 seconds. To prevent client performance drop from a large number of blood particles, a maximum limit of 1000 particles per client has been introduced. When this limit is exceeded, older particles are removed. That is, this will allow the player to enjoy the blood particles for a very long time without them disappearing while maintaining client performance. Ideally, these settings should have been moved to the client, but since I'm too lazy to create an interface, I didn't do that. However, on the server side, you can adjust these parameters globally for all clients using the [BloodParticlesLimit](https://github.com/ysaroka/InediaInfectedAI/wiki/Description#bloodparticleslimit) and [BloodParticleDurationSeconds](https://github.com/ysaroka/InediaInfectedAI/wiki/Description#bloodparticledurationseconds) settings.

⚠️ If the global parameter _BloodParticleDurationSeconds_ is set to a value greater than zero, the vanilla blood particle system, as well as possibly some modded systems, will be disabled. To restore them, you need to set _BloodParticleDurationSeconds_ to "0", which will disable the blood particle system of "InediaInfectedAI".

⚠️ Keep in mind that if you have bloodless creatures, it's better to disable the _Zombies.BloodSplatParticlesIsActive_ and _Zombies.BloodTrailParticlesIsActive_ parameters for them, so that these creatures don't leave blood splatters and trails.

Video showcasing the new visual effects:
https://www.youtube.com/watch?v=R4k9jgGgRBs

### ☑️ 8) The debuff from head pain has been slightly intensified, as it was not particularly dangerous compared to other debuffs

Now, with moderate head pain (orange icon), there is a chance that the player will vomit (0.1% per second).

With severe head pain (red icon), the chance increases to 0.3% per second.

The vomiting mechanic can be disabled by the _Players.VomitWithPainedHead_ parameter, which is enabled by default.

Additionally, the blur effect from head pain is now 3 times stronger than the same effect from pain in other limbs. And the blur effect from limb pain has been stretched out over time, thereby creating more difficulties for the player experiencing pain.

### ☑️ 9) A new mechanic and the parameters _Zombies.JumpAttackHandlerIsActive_, _Zombies.JumpAttackChance_, _Zombies.JumpAttackCooldownSeconds_ have been added

If it is active, then the infected will jump toward the player when approaching, attempting to stun and knock them down. This adds extra challenges in dealing with the infected, as they gain an attack that always stuns the player while bringing the infected right up close.

By default, it is enabled, the chance is set to 10%, and the cooldown is 60 seconds. To disable it, set the value of the _Zombies.JumpAttackHandlerIsActive_ parameter to "0".

More details: https://github.com/ysaroka/InediaInfectedAI/wiki/Description#zombiesjumpattackhandlerisactive

### ☑️ 10) Parameters _Zombies.DisarmToPlayer*ChancePercent_ have been added to configure the chance of knocking weapons out of a character's hands independently of the Inedia pain system

This allows you to create entities that will knock weapons out of a character’s hands upon hitting any part of the body, based solely on the chance you specified.

By default, the chances are set to 0%.

https://github.com/ysaroka/InediaInfectedAI/wiki/Description#zombiesdisarmtoplayerchancepercent

### ☑️ 11) Added the _Vehicles.CollisionsDamageSpeedThresholdKmH_ parameter

This parameter allows specifying the minimum speed (in km/h) for any vehicle at which the vehicle starts taking damage from collisions with creatures. By default, this parameter is set to 10 km/h for all vehicles except the bicycle.

https://github.com/ysaroka/InediaInfectedAI/wiki/Description#vehiclescollisionsdamagespeedthresholdkmh

### ☑️ 12) Parameters _Players.FallPainMultiplier_, _Players.VehicleCrashPainMultiplier_, _Players.ExplosionsPainMultiplier_ and _Players.VehicleCollisionsPainMultiplier_ have been added to specify the pain multipliers for the pain the character receives from falls, vehicle crashes, collisions with vehicles, and explosions

https://github.com/ysaroka/InediaInfectedAI/wiki/Description#playersvehiclecrashpainmultiplier

https://github.com/ysaroka/InediaInfectedAI/wiki/Description#playersfallpainmultiplier

### ☑️ 13) A parameter _Zombies.DamageToZombieAlwaysKillOnBackstab_ has been added to always kill the infected with a backstab regardless of their defense and HP (previously, infected with high defense or HP were not killed by a backstab)

By default, this parameter is enabled, meaning any infected that can be backstabbed will die from it regardless of their defense and HP.

https://github.com/ysaroka/InediaInfectedAI/wiki/Description#zombiesdamagetozombiealwayskillonbackstab

### ☑️ 14) The functionality for preventing clustering has been significantly improved

Now, instead of using raycasting, they detect infected on their path by scanning the surrounding scene objects.

They also no longer disable search mode if another infected is in the way, but instead try to bypass them. As a result, they have become slightly better at navigating enclosed spaces, but if there are too many of them, they still tend to get stuck.

Since the "PreventClustering" mechanic now works very well, it will always be used by default, and the _Zombies.PreventClustering_ parameter has been removed and is no longer relevant.

### ☑️ 15) Parameters _Zombies.NoiseMultiplierLadder*_ have been added to adjust the level of vanilla noise emitted by the player while climbing ladders, helping to resolve many issues with unrealistic player detection

This is done because, in the vanilla game, the player emits the same noise level while climbing a ladder as when running, which often causes issues, as the infected can hear players climbing ladders very well.

By default, the values of these new parameters are set very low, making it harder for the infected to hear the player on the ladder as effectively as before.

https://github.com/ysaroka/InediaInfectedAI/wiki/Description#playersnoisemultiplierladderday

### ☑️ 16) In the Inedia pain system, support for "Syberia Project" painkillers has been added

Level 1 and 2 painkillers act like vanilla painkillers, while the level 3 painkiller acts like morphine.

### ☑️ 17) A parameter _Players.OverrideGetHitComponentChances_ has been added, allowing you to completely disable the damage distribution system of infected by body parts and revert to the vanilla system

This is necessary in cases where you need to prevent infected from dealing **head** damage to the character.

More details here: https://github.com/ysaroka/InediaInfectedAI/wiki/Description#playersoverridegethitcomponentchances

### ☑️ 18) The parameter _Zombies.ResistContaminatedEffect_ now works not only on infected and animals but also on characters.
Accordingly, you now have the ability to make various bots and NPCs immune to chemical zones.

The functionality itself has also been improved: now, a creature becomes immune to the zone even if it spawns within it. Previously, if a creature spawned inside a zone, it would always die, and the parameter only worked if the creature entered the zone after spawning.

⚠️ Keep in mind that this parameter now also applies to players, and if for any reason you have set it to "1" for "all", it will now affect players as well. To prevent this, you will need to disable this parameter separately for "SurvivorBase".

### ☑️ 19) Many multipliers now apply not only to damage against the infected but also to damage against characters and animals, if the corresponding parameter _Zombies.DamageToPlayerHandlerIsActive_ and _Zombies.DamageToZombieHandlerIsActive_ are enabled

For example, a character with damaged arms will now hit not only the infected but also other characters with less force.

⚠️ Keep in mind that the modification now includes damage control from players to players and from players to animals, and if you are using mods that handle this damage, it's better to disable _Zombies.DamageToPlayerHandlerIsActive_ for "SurvivorBase" or _Zombies.DamageToZombieHandlerIsActive_ for "AnimalBase".

⚠️ Additionally, weapon damage multipliers (the _Zombies.DamageToZombieWeaponsMultipliers_ parameter) now work for animals and players. Keep in mind that if you, for any reason, have configured _Zombies.DamageToZombieWeaponsMultipliers_ multipliers for "all", they will now apply to both players and animals. To exclude players from "all", simply add a default empty weapons list for "SurvivorBase":

    "Zombies": {
        ...
        "DamageToZombieWeaponsMultipliers": {
            "all": {
                "all": 1.0,
                ... your weapons multipliers for infected ...
            },
            "SurvivorBase": {
                "all": 1.0
            },
        },
        ...
    },

### ☑️ 20) Several new administrator console commands have been added (\izmbs \izmbm \ideer \irepauto \ifgm)

https://github.com/ysaroka/InediaInfectedAI/wiki/Description#admin-privileges-and-commands

### ☑️ 21) Rebalance and config optimization

- Health/Shock/Pain/Stamina damage inflicted by infected on the player (parameters _Zombies.DamageToPlayer*HealthMultiplier_, _Zombies.DamageToPlayer*ShockMultiplier_, _Zombies.PainToPlayer*Multiplier_, _Zombies.DamageToPlayer*StaminaPercent_) has been slightly reduced, while the infected's resistance to close-range headshots has been slightly increased (parameter _Zombies.DamageToZombieHeadMeleeMultiplier_).
- The chance of scream activation and the attraction radius for the officer have been increased. Additionally, officers are no longer affected by the mechanic of scream deactivation by the screams of other infected (parameter _Zombies.ScreamNearbyInfectedSilenceSeconds_).
- The maximum jump height of the infected (parameter _Zombies.UpJumpHeightMax_) has been increased from "1.7" to "1.8" meters.
- The probability of an infected hitting the player's head has been increased from 15% to 19%.
- The fixed radius of some irritants has been increased:
  - Fireplace: from 40 to 50 meters during the day, and from 80 to 100 meters at night;
  - Hard mining: from 80 to 100 meters;
  - Light mining/Building/Saw planks: from 60 to 70 meters;
- For animals the recovery time for injured legs (parameter _Zombies.InjuryHandlerRestoreInjuredLegAfterSeconds_) is set to "900" seconds (15 minutes).
- The parameter _Players.DisableVanillaLegsDamageSystem_ has been removed due to redundancy, and the enabling/disabling of the vanilla leg damage system is now determined based on the _Players.PainSystemIsActive_ parameter.
- The _Players.BreakOverPainedLegsWhenReceivingHits_ parameter has been removed; instead, leg fractures can now be disabled using the _Players.LegsBreakDurationSeconds_ parameter.
- The parameter _Players.BreakOverPainedLegsWhenOtherFactors_ has been removed, and in its place, two parameters have been added: _Players.LimbsBreakFromFalls_ and _Players.LegsBreakFromTraps_.
- The logic for damage calculation from projectiles that do not have damage specified in their settings has been changed. Now, the damage is based on the vanilla game configuration for heavy attacks with this item. For more details, see the descriptions of the damage parameters for thrown projectiles: https://github.com/ysaroka/InediaInfectedAI/wiki/Description#parameterstargethealthdamage

You can always check what has changed in the default configuration file, which is updated after each modification update:
https://github.com/ysaroka/InediaInfectedAI/wiki/Default-configuration-file

### ☑️ 22) Fixes:

- Fixed a bug with a conflict between the search mode and vanilla VAULT animations, which caused the infected to sometimes go crazy, walk through walls, and generally behave strangely.
- Fixed a bug where the projectile parameter _AccuracySpread_ didn't work, causing them to always throw projectiles with 100% accuracy, which wasn't exactly what I intended.
- Now infected cannot break irritating items on the player's body (e.g., chemlights, flashlights) if the player is blocking.
However, this does not apply to items held in the player's hands, the infected can still destroy them regardless of blocking.
- Now, if the character tries to close a destroyed door, the appropriate sound will play. Additionally, the message about a failed door-opening attempt is now displayed as an informational pop-up instead of being shown in the game chat.
- Slightly adjusted the melee attacks dodge logic for infected, due to insufficient frequency of distance checks to the target, it sometimes triggered too late and was ineffective. Now everything should work correctly. Additionally, the time the infected pauses has been slightly randomized.
- I reverted to the old method of handling infected collision during jumps with players using my own handler, as the vanilla method _PlayerBase.EOnContact(...)_ did not register collisions when the player was on a ladder. Consequently, infected could no longer knock players off ladders with jumps. Now this ability has been restored.
- Improved the logic of infected interacting with doors. Slow animations have been removed, and the frequency of door hits has been increased. The delay that occurred when the infected was breaking down a door and the door opened (either by breaking or by a character) has also been eliminated. Due to this delay, the infected would freeze for a moment, waiting for the ability to move. Now, after the door opens, they start moving immediately.
- Slightly reduced the chances and severity of bleeding from melee weapons, as there were quite a few unrealistic situations where infected or animals would die from bleeding after being hit a few times with fists or a bat.
- Fixed an issue where the _Zombies.DamageToZombieShockToStunHandlerIsActive_ parameter being enabled caused the inability to knock back and stun infected upon collision with vehicles. Due to this, the infected often got inside the vehicle and dealt damage to the player. I noticed the problem completely by accident. It’s a shame that absolutely no one told me that the infected don’t get knocked back by cars. Isn’t that something that immediately stands out? 😂
- The functionality of jumping down has been slightly improved. Now, infected will much less frequently get stuck in building textures as a result of such jumps.
- In the car attack handler, the method for determining predators has been changed. Now, predatory animals that do not inherit from bears or wolves will also be able to attack the car and the player inside it.
- Fixed an issue where, after looting the corpse of an infected and relogging, the player could no longer loot the corpse or view its contents.
- Fixed a bug that caused loot to be duplicated multiple times when shooting the corpse of an infected. If you disabled the _Zombies.DamageToZombieShockToStunHandlerIsActive_ parameter due to this issue, you can enable it again.
- Fixed the pain damage to the character's head (due to a flaw, the damage was half as much). Now global shock is used to calculate the character's pain instead of "dmgZone" shock. As a result, shock damage to the head has doubled.
- Fixed the mismatch between the vanilla sound positions of the doors in the "Land_Tisy_Barracks" building and their actual positions, which caused infected to barely break down most of the doors in this building.
- A check for the existence of the _BleedingManager_ object in _PlayerBase_ class has been added before its usage, as it sometimes seems to be missing when using "InediaInfectedAI" with "DayZ-Expansion-AI", which causes a server crash.
