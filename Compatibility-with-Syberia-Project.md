# Compatibility with Syberia Project (Syberia 1.0)

If you know of any additional compatibility details not covered in this guide, please write about them in Discord, and I will update the guide.

### Information on compatibility with Syberia Project received from other players

Please note that the dot in the Inedia parameter indicates JSON nesting.

That is, for example, the parameter _Zombies.ParameterName_ means:

    "Zombies": {
        "ParameterName": ...
    }

### ☑️ 1) _Zombies.SearchBodyToViewCargo_ parameter

"Syberia Project" has its own system for searching corpses, so it can be disabled in "InediaInfectedAI" mod (_Zombies.SearchBodyToViewCargo_ => 0).

### ☑️ 2) _Zombies.CanBeButchered_ parameter

"Syberia Project" doesn't allow modifying "ActionSkinning", or more precisely, the completion of this action, so dropping items after butchering a zombie's body won't work.

Therefore, the _Zombies.CanBeButchered_ parameter is meaningless in combination with the "Syberia Project" mod and should be disabled (_Zombies.CanBeButchered_ => 0).

### ☑️ 3) Disabling "Syberia Project" door-breaking mechanics

You need to disable doors breaking handler in "Syberia Project" (parameter _CfgSyberia.ZombieSystem.zombieOpenDoorEnable_), because there it does not have functionality that is required for "InediaInfectedAI" mod to work correctly, i.e. functionality that switches zombie search mode if he cannot knock down a door. In this case - zombie will simply get stuck in door until the search mode ends, which is a very long time.

### ☑️ 4) Inedia Pain System

The "InediaInfectedAI" modification includes a fully-fledged [limb pain debuff system](Inedia-Pain-system-guide).

The "Syberia Project" also has its own pain system.

While you can use both systems simultaneously, it may create some confusion in understanding what has happened to the character, because the Inedia pain system does not affect the Syberia pain system in any way. For example, it will be unclear why a Inedia fracture or wound doesn't cause Syberia pain.

I also noticed that some debuffs reducing shock work strangely in Syberia, it feels like the shock from injured arms is reduced in a way that doesn't match the intended design. Moreover, I believe this is just the tip of the iceberg, so I strongly advise against using the Inedia pain system alongside Syberia. Using two pain systems is illogical and could lead to odd issues.

Therefore, you need to completely disable the Inedia pain system:

    "Players": {
        ...
        "PainSystemIsActive": 0,
        ...
    },

However, if you still want to use Inedia pain debuffs in some form, I recommend keeping only the pain system, disabling fractures, deep wounds, bullet wounds, internal bleeding, and increasing the pain reduction speed, thus making Inedia pain debuffs something temporary and short-lived, but still capable of causing problems in a fight with an infected:

    "Players": {
        ...
        "PainSystemIsActive": 1,
        "PainHealingRatePerSecondPercent": 0.5,
        "LimbsBreakSystemIsActive": 0,
        "LimbsDeepWoundSystemIsActive": 0,
        "LimbsBulletSystemIsActive": 0,
        "InternalBleedingSystemIsActive": 0,
        ...
    },

### ☑️ 5) _Players.NoiseMultiplier*_ parameters

"Syberia Project" has its own increased multipliers of noise produced by the player, which are multiplied by the multipliers of this mod, and infected start hearing the player too well.

To prevent this, it is necessary to set all the noise multipliers of "InediaInfectedAI" to "1":

    "Players": {
        ...
        "NoiseMultiplierDay": 1,
        "NoiseMultiplierNight": 1,
        "NoiseMultiplierCrouchDay": 1,
        "NoiseMultiplierCrouchNight": 1,
        ...
    },

### ☑️ 6) Transmission of disease agents

The "InediaInfectedAI" supports transmitting disease agents to the player when taking damage from infected.

By default, the mod is configured to transmit vanilla sepsis when the player gets a cut.

"Syberia Project" has its own sepsis and its own status transmission mechanics.

Essentially, this mechanic is fully compatible with "Syberia Project", and you can use it to transmit any custom diseases to the player.

However, the default parameters are not suitable for "Syberia Project", and if you do not need to transmit any custom diseases to the player, simply disable it in "InediaInfectedAI":

    Zombies.DiseasesToPlayerHandlerIsActive = 0

### ☑️ 7) Mechanics of attacking unconscious players

Both mods have a mechanic that allows infected to attack unconscious players.

Therefore, if you need to disable this mechanic, you must disable it in both mods: the _CfgSyberia.ZombieSystem.zombieAttackPlayersInUnconscious_ parameter for "Syberia Project" and the _Zombies.AttackPlayersUnconscious_ parameter for "InediaInfectedAI".

In case you need to enable finishing off unconscious players, keep in mind that in "InediaInfectedAI" there is a parameter _Zombies.AttackPlayersUnconsciousHitsLimit_ that allows infected to deliver a limited number of blows while the character is unconscious. If you want the finishing off of infected in "Syberia Project" to work correctly, you need to set this parameter's value to "-1".

### ☑️ 8) _Zombies.VisionRangeMultiplier*_ parameters

"Syberia Project" completely overrides the vanilla method `AITargetCallbacksPlayer.GetMaxVisionRangeModifier(...)`, without calling the parent, and consequently, no other mods can affect the visibility range multiplier for the infected.

Therefore, the parameters "InediaInfectedAI" _Zombies.VisionRangeMultiplier*_ will not work and are meaningless.
