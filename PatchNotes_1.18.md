### ☑️ 1) The chances of performing surgeries have been adjusted.
Now, the chance of a successful operation is 10% higher when one player performs surgery on another.
Accordingly, medical item configs now include parameters to configure the success chance for assist surgeries.

The information in the visual guides has been updated:
* EN: https://github.com/ysaroka/InediaInfectedAI/wiki/Inedia-Pain-System-Visual-Guide-EN
* RU: https://github.com/ysaroka/InediaInfectedAI/wiki/Inedia-Pain-System-Visual-Guide-RU

### ☑️ 2) Support for the DayZ-Horse modification has been added.
The wound treatment action will now also appear if the horse has Inedia bleeding.
After bandaging, the Inedia bleeding will stop accordingly.

### ☑️ 3) Added basic compatibility with _VPPAdminTools_ and _Community-Online-Tools_.
Now the healing function in these mods also removes all debuffs from the Inedia pain system.

Due to a lack of time, there are currently no plans to add interfaces for managing the Inedia pain system in these mods.

### ☑️ 4) Multiple surgical kits or splint kits can now be combined.

### ☑️ *) Fixes:
- Some improvements were made to the search script to reduce the frequency of infected clipping through walls in large groups. However, they still continue to clip through because, when colliding with other infected or even walls, the game engine can launch them like a ping-pong ball in random directions, as if the walls were made of rubber. Since this engine has almost no collision handling between infected and objects above knee height, they end up "flying" through walls. This behavior is observed even in vanilla mechanics and is most common when a player is inside a hunting cabin with more than 30 infected outside. However, in this modification, it occurs much more frequently because the infected are forced to move towards doors, increasing the likelihood of collisions.
Honestly, I’m tired of trying to improve this aspect of the modification, so it’s left as is. You can either use it with the current engine limitations, send me your own fixes to improve this mechanic, or simply not use the mod. However, don't write to me anymore about this issue.
- The item "Vodka" was replaced with "GlassBottle" during the config generation because this item was replaced in the vanilla game.
- A vanilla issue has been fixed where, for some reason, the EEKilled() method would return the entity of the killed creature itself as the killer. Because of this, mods that track the deaths of infected and players (DayZ-Expansion-Hardline, DayZ-Expansion-Quests) sometimes failed to register deaths.
- Now, the EEHitBy() function of this mod does not trigger if the "damageResult" or "source" is empty. They are usually not empty, but some mods might call EEHitBy() with empty "damageResult", like PVZ, which could lead to errors in crash logs. There will be no more such errors.
- Fixed an issue with the pain system layout that caused many custom chats to function incorrectly.
- Minor compatibility fixes with Terje mods.
- Fixed an issue where thrown projectiles could cause deep wounds while ignoring the player's equipment protection.
