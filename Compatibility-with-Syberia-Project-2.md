# Compatibility with TerjeMods (Syberia 2.0)

If you know of any additional compatibility details not covered in this guide, please write about them in Discord, and I will update the guide.

### Information on compatibility with TerjeMods received from other players

Please note that the dot in the Inedia parameter indicates JSON nesting.

That is, for example, the parameter _Zombies.ParameterName_ means:

    "Zombies": {
        "ParameterName": ...
    }

### ☑️ 1) Inedia Pain System

The "InediaInfectedAI" modification includes a fully-fledged [limb pain debuff system](Inedia-Pain-system-guide).

The "TerjeMedicine" also has its own pain system.

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

### ☑️ 2) _Players.NoiseMultiplier*_ parameters

"TerjeSkills" has its own increased multipliers of noise produced by the player, which are multiplied by the multipliers of this mod, and infected start hearing the player too well.

To prevent this, it is necessary to set all the noise multipliers of "InediaInfectedAI" to "1":

    "Players": {
        ...
        "NoiseMultiplierDay": 1,
        "NoiseMultiplierNight": 1,
        "NoiseMultiplierCrouchDay": 1,
        "NoiseMultiplierCrouchNight": 1,
        ...
    },

### ☑️ 3) Transmission of disease agents

The "InediaInfectedAI" supports transmitting disease agents to the player when taking damage from infected.

By default, the mod is configured to transmit vanilla sepsis when the player gets a cut.

"TerjeMedicine" has its own sepsis and its own status transmission mechanics.

Essentially, this mechanic is fully compatible with "TerjeMedicine", and you can use it to transmit any custom diseases to the player.

However, the default parameters are not suitable for "TerjeMedicine", and if you do not need to transmit any custom diseases to the player, simply disable it in "InediaInfectedAI":

    Zombies.DiseasesToPlayerHandlerIsActive = 0

### ☑️ 4) Mechanics of attacking unconscious players

If you are using "TerjeSkills", disable the "InediaInfectedAI" parameter _Zombies.AttackPlayersUnconsciousHandlerIsActive_, allowing "TerjeSkills" to fully manage infected attacks on unconscious players.

If you do not do this, the perk "TerjeSkills" that allows the player to disable these attacks will not work.
