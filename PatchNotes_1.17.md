### ☑️ 1) New types of injuries have been added to the pain system.
The pain system now includes new types of injuries - deep wounds, bullet wounds, and internal bleeding. Additionally, existing mechanics have been significantly updated. Information about the new pain system is available [here](Inedia-Pain-system-guide).

In addition to the pain system, this modification introduces a [medical system](Inedia-Medicine-guide) that includes a range of medications and medical tools to counteract debuffs and injuries from the pain system, and also allows you to equip any vanilla or custom items and liquids with these properties.

[Mini-demo (youtube)](https://www.youtube.com/watch?v=h186RQrb39g)

Links to visual guide of the updated Inedia Pain System:
* [EN](Inedia-Pain-System-Visual-Guide-EN)
* [RU](Inedia-Pain-System-Visual-Guide-RU)

**Information that should also be noted:**
* Since many countermeasures for fractures and deep wounds have been introduced, the duration of fractures has been set to 1800 seconds. I strongly advise against changing this duration for fractures and deep wounds without also adjusting the medications, as it will break the balance. For those using old configurations and planning to add new medications, I recommend setting the duration of fractures to 1800 seconds (parameters _Players.#LIMB#BreakDurationSeconds_).
    * Examples of the current balance between the duration of injuries and medical items:
        * Having a high-quality "Splint Kit" (bone regeneration: x3) and calcium tablets (bone regeneration: x2), you get a bone regeneration factor of x6. As a result, the break will heal in 300 seconds, which matches the duration of one calcium tablet.
        * When consuming Vikasol (wounds regen: x2), the recovery time of a deep wound will be halved, which, in combination with a Hemostatic Dressing (wounds regen : x3), will give a recovery multiplier of 6 times, and the deep wound will heal in 1800 / 6 = 300 seconds, which is the duration of one Vikasol tablet.
        * When treating a deep wound with vanilla bandages, which last for 600 seconds and have a limb regeneration rate of 1.5, you will heal the limb with exactly 1 bandage and 2 Vikasol tablets, i.e., 1800 / (1.5 * 2) = 600 seconds (the duration of one bandage and two tablets).
* Fixed an issue where performing actions with pain in the arm caused excessive shock damage when a leg fracture was active. Additionally, now actions affecting shock damage from arm pain (parameter _Players.ArmsPainShockDamageActions_) can be configured through base classes. Actions of eating and taking pills are excluded from those causing shock to injured arms, as it is not very logical. To achieve this, these actions were added to the _Players.ArmsPainShockDamageActions_ parameter. Therefore, for this update to work with old configurations, you need to manually update the parameter _Players.ArmsPainShockDamageActions_. The current value of the parameter can be found in the default configuration file, which is always available [here](Default-configuration-file).
* A major refactoring was made in the update, with the entire pain system being moved from _PlayerBase_ to a separate class. This is one of the largest updates to this modification, so if you have overridden any pain system methods, it is likely that they will stop working. The entire pain system is now contained in the _PainManager_ class. Additionally, if anyone has modified the layout or interacted with the HUD through scripts, be aware that the layout have changed, and the HUD rendering scripts have undergone significant changes.
* The parameter _Players.LegsBreakDurationSeconds_ now affects the duration of vanilla leg fractures, so keep this in mind if you have modified this duration using scripts, as conflicts may arise. Additionally, the duration of leg fractures is influenced by all the new medicine related to fractures.
* Parameters have been added to influence the chance of receiving a fracture or deep wound for each type of creature separately:
    * [Zombies.PainToPlayerLimbsBreakChancesMultiplier](Description#zombiespaintoplayerlimbsbreakchancesmultiplier)
    * [Zombies.PainToPlayerLimbsDeepWoundChancesMultiplier](Description#zombiespaintoplayerlimbsdeepwoundchancesmultiplier)
* Parameters have been added for thrown projectiles, allowing you to influence the chance of causing fractures and deep wounds.
    * [Parameters.TargetBreakChanceMultiplier](Description#parameterstargetbreakchancemultiplier)
    * [Parameters.TargetDeepWoundChanceMultiplier](Description#parameterstargetdeepwoundchancemultiplier)
* The algorithm for generating pain-induced hand tremors has been updated, making them smoother but also making aiming more difficult, as the front sight now moves outside the rear sight. Additionally, pain-induced tremors are now intensified by fractures or a bullet wound in the hand, making it nearly impossible to hit a target from more than a few meters away in such a condition.
* Any NPCs and bots cannot suffer deep wounds or gunshot wounds, as they cannot treat them and will simply die from them. At the same time, they can still receive pain debuffs and fractures.

### ☑️ 2) To give players a way to counteract the new debuffs, a medical system has been added.
The medical system includes a range of medications and medical tools that counteract both new and existing debuffs.

It also allows you to assign the properties of any new medical item to any vanilla or custom item with flexible configuration options.

A description of the new medical system is available [here](Inedia-Medicine-guide).

**Information that should also be noted:**
* Painkillers now regenerate HP while they are active, depending on the level of the painkiller.
    * Morphine (20 times, 60 seconds)
    * Tramadol (4 times, 180 seconds)
    * Codeine (2 times, 300 seconds)
* Since a new medical system has been introduced, the parameters _Players.LimbsBreakCalciumDurationSeconds_ and _Players.LimbsBreakCalciumHealingMultiplier_ have been removed and are no longer used. The effect of calcium is now configured through `config.cpp`, just like the effect of any other medications and medical tools.
* Since the pain system was moved to a separate modification called "InediaPain", the prefixes of medications have been changed. For example, Calcium is now named _InediaPain_Calcium_ instead of _InediaInfectedAI_Calcium_. However, the item _InediaInfectedAI_Calcium_ has been retained for backward compatibility.
* If you were using the old `types.xml`, I recommend updating it, as many new medications have been added, the balance has been reviewed, and the chances and quantity of items in the spawn have been changed. The `types.xml` file and other server settings for all medical items are available in the `types` directory at the root of the addon.
* When the fracture system is active, all vanilla actions related to applying the splint are removed from the vanilla _Splint_ item. However, the Inedia limb stabilization actions are added, which include the ability to adjust the regeneration multiplier and shock reduction for any item. This information is provided in case the vanilla splint actions have been modified on your server in some way.

### ☑️ 3) Support for Syberia Project and TerjeMods (Syberia 2.0).
The config that modified head damage for the infected was removed from config.cpp because it created conflicts with some mods that changed the same parameters, such as the "Syberia Project".

Now, the increase in head damage to the infected is handled through scripts, rather than through the game configuration.

⚠️⚠️⚠️ As a result, the server mod "InediaInfectedAI_SyberiaProject_Compatibility" is no longer needed and will be removed from the workshop. Also, those who have this mod installed ⚠️must delete it⚠️, otherwise the head damage to the infected will be increased by 4 times, as it will be amplified both by the scripts and the compatibility mod.

Added compatibility with "TerjeSkills" and "TerjeMedicine" (Syberia 2.0):

Now the perks Stealth->QuietStep, Stealth->Ninja, Stealth->ShadowTracker affect the noise of footsteps in "InediaInfectedAI".

It was decided to abandon the compatibility of the Inedia pain system with the Syberia medicine system, as their simultaneous operation is quite illogical and also leads to strange issues. Therefore, if you are using "Syberia Project" (Syberia 1.0) or "TerjeMedicine" (Syberia 2.0), it is highly recommended to completely disable the Inedia pain system:

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

Accordingly, the compatibility guides have been updated with this information. There, you can also find more detailed information about the issues with the simultaneous operation of the two pain systems.

Initial guide for compatibility with Syberia 2.0 (will probably be expanded over time):
https://github.com/ysaroka/InediaInfectedAI/wiki/Compatibility-with-Syberia-Project-2

### ☑️ 4) A new parameter _Players.LimbsBreakSystemIsActive_ has been added, allowing you to completely disable the limbs break system.
Previously, this was done using the parameter _Players.LimbsBreakChancesMultiplier_, and I did not like this method. The parameter _Players.LimbsBreakChancesMultiplier_ has now been removed and is no longer used. Instead, the parameter _Zombies.PainToPlayerLimbsBreakChancesMultiplier_ is now used, which can be configured for any type of zombie.

### ☑️ 5) A new parameter _Zombies.AttackPlayersUnconsciousHandlerIsActive_ has been added, allowing the disabling of the infected attack handler for unconscious players.
This is necessary because some mods manage this mechanic themselves, and a mechanism for fully disabling it was required. For example, in the new Syberia 2.0, there is a separate perk that controls this mechanic.

The _Zombies.AttackPlayersUnconscious_ parameter has been removed due to redundancy.

### ☑️ *) Fixes/Rebalance:
- Excessive blood glow at night has been reduced. It hasn't been completely removed to keep the blood visible, but it has been significantly minimized so that the blood doesn't appear too unrealistic.
- Changed the effect of limb pain on movement speed: it now has a much smaller impact. However, fractures/bullet wounds/internal bleeding significantly increase this effect.
- The parameter _Players.BleedingChanceMultiplierWhenOverPainedLimbReceivingHits_ has been removed. Firstly, it was illogical that pain increased the chance of bleeding, and secondly, a new mechanic for deep wounds has been introduced, where the chance of receiving a deep wound depends on the chance of bleeding. Therefore, this parameter caused an imbalance in the deep wound mechanics.
- The parameter _Players.ArmsLowerWhenAimingWithInjuredArms_ has been renamed to _Players.ArmsLowerWhenAimingWithPainedArms_.
- Fixed an issue where infected could sometimes pass through closed doors. The problem occurred because the vanilla game engine, when handling collisions, would push the infected upwards. When they were in this "floating" state, they lost collision with doors. The "InediaInfectedAI" continued to lead them through the doors, but due to the lack of collision at height, they were able to pass through them. Now, I disable the Inedia-script when an infected is airborne, thereby preventing passage through walls in such states.
- Fixed a bug where the shock damage multipliers _Zombies.DamageToPlayerShockMultiplier_ affected the pain damage received by the player. Now, only the multipliers _Zombies.PainToPlayer*Multiplier_ affect pain damage.
- A flaw has been fixed that caused infected to perform downward jumps from dangerous heights when trying to exit a stuck state, regardless of the player's position. This allowed players to abuse the mechanic in certain buildings by standing in a safe spot and waiting for the infected to break their legs. Now, when attempting to exit a stuck state, the infected will not perform a downward jump if it could harm them.
- The issue has been fixed where headshot damage to animals was not increasing and remained the same as body damage. Additionally, the issue has been fixed where animals did not die from headshots with any weapon when the _Zombies.DamageToZombieHandlerIsActive_ parameter was disabled.
- Fixed an issue where vanilla speed buffs from morphine and codeine did not affect vanilla speed debuffs, such as those triggered by low health levels.
- The hand shake algorithm has been updated: now the hands shake more smoothly, but hitting the target has become more difficult.
- Fixed an issue where the Chinese Simplified language was not activated.
- The _Playrs.SearchBodyToViewCargo_ parameter is now enabled by default in the vanilla configuration.
