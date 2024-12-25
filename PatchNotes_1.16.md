### ☑️ 1) A medication has been added to increase the healing speed of broken limbs: "Calcium hydroxyapatite caps", item class - "InediaInfectedAI_Calcium".
Parameters [Players.LimbsBreakCalciumDurationSeconds](Description#playerslimbsbreakcalciumdurationseconds) for setting the medication duration and [Players.LimbsBreakCalciumHealingMultiplier](Description#playerslimbsbreakcalciumhealingmultiplier) for adjusting the fracture healing speed multiplier have also been added.

Please note that the medication also affects the healing speed of vanilla leg breaks.

Since one capsule heals breaks over its duration, the medication's spawn rate has been made quite rare. You can find the _types.xml_ for this medication in the root of the modification add-on, directory "types".

### ☑️ 2) A parameter _Zombies.DamageToZombieBodyPartsPiercingIsActive_ has been added, allowing you to disable penetrating bullet damage to multiple body parts of the infected.
https://github.com/ysaroka/InediaInfectedAI/wiki/Description#zombiesdamagetozombiebodypartspiercingisactive

### ☑️ 3) Now, when attempting to escape from handcuffs or other restraining items, the character will take pain damage to their arms with a chance of sustaining a break.
Using the parameter [Players.ArmsPainUnrestrainItems](Description#playersarmspainunrestrainitems), you can adjust the amount of pain damage per second for any item from which the character attempts to break free (e.g., handcuffs).

Keep in mind that for this functionality to work correctly, you need to add the action "ActionUnrestrainSelf" with a value of "1" to the _Players.ArmsPainShockDamageActions_ parameter, otherwise, the character will lose consciousness from shock damage when performing the unrestraining action. You can always check what has changed in the default configuration file, which is updated after each modification update: https://github.com/ysaroka/InediaInfectedAI/wiki/Default-configuration-file

### ☑️ 4) Added the option to configure the type of notification message the player receives when attempting to open destroyed door.
This can be done using the [Players.DestroyedDoorNotificationType](Description#playersdestroyeddoornotificationtype) parameter.

### ☑️ 5) The logic for dealing melee damage with heavy attacks when the arms are injured has been changed.
Now, a character with heavily injured arms can perform a heavy attack on the infected, however, this attack will not be able to heavily stun the infected.

### ☑️ 6) The vanilla mechanics allow for a nearly 90% chance of lightly stunning a zombie with a regular melee attack, such as when using a sledgehammer, which enables a constant stun-lock on the zombie.
Therefore, in this mod, a limit has been introduced on the chance of lightly stunning a zombie with a regular melee attack - no more than 50%, regardless of damage settings or weapon type. This helps prevent zombies from being put into a permanent stun-lock.

Naturally, this restriction will only work if the "InediaInfectedAI" processes the stun mechanics, meaning that the parameter _Zombies.DamageToZombieShockToStunHandlerIsActive_ is enabled.

### ☑️ 7) In the default configuration, the blood volume for horses from the "DayZ Horse" mod is manually set to 30 liters.
This is done because, by default, the blood volume in "InediaInfectedAI" is determined based on the animal's weight, and these horses weigh ~3.5 tons, which ultimately results in 240 liters of blood in one animal 😂.

The blood volume for cows has also been set to 30 liters.

The parameter that was changed for this is _Zombies.BloodVolumeMl_. You can always check what has changed in the default configuration file, which is updated after each modification update: https://github.com/ysaroka/InediaInfectedAI/wiki/Default-configuration-file

### ☑️ 8) Rebalance:
- The default duration of breaks (parameters _Players.#LIMB#BreakDurationSeconds_) has been changed from "900" to "1000" seconds to match the vanilla leg break, which lasts "1000" seconds under the effect of a splint.

### ☑️ *) Fixes:
- The issue where the player's death was logged multiple times by KillFeed mods has been fixed. Also the bug that caused KillFeed mods to register player headshots as suicides has been fixed. If you disabled the _Zombies.DamageToPlayerHandlerIsActive_ parameter for "SurvivorBase" for this reason, you can enable it back now.
- Fixed a bug that caused _Players.SearchBodyToViewCargo*_ and some other configuration parameters to not work.
- The synchronization of boolean variables has been reworked using a bitmask to reduce the number of variables individually registered via _RegisterNetSyncVariable*()_ and to avoid potential issues, as the number of variables registered through _RegisterNetSyncVariable*()_ is limited.
- The bug where painkillers always reduced the speed debuff regardless of the limb pain level after use has been fixed. Now, after taking painkillers, the speed debuff will correspond to the limb pain level after their use.
- The speed debuff for the orange level of leg pain has been changed, it is now slightly weaker, and the character at this level of leg pain now has the ability to sprint lightly.
