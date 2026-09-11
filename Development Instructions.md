&nbsp;

# DEVELOPMENT INSTRUCTIONS — READ BEFORE MODIFYING THE PROJECT

This document is the master Product Requirements Specification for the game.

It describes the complete long-term vision of the game. It is NOT an instruction to implement every feature immediately.

Claude must treat this document as the authoritative design specification while developing the project.

## CRITICAL DEVELOPMENT RULE

DO NOT attempt to build the entire game at once.

The game must be developed incrementally through small, testable milestones.

Before making significant changes:

1. Inspect the existing Roblox Studio project.
2. Understand the existing architecture and scripts.
3. Identify what has already been implemented.
4. Determine the smallest next milestone that should be completed.
5. Explain the proposed implementation and affected systems.
6. Implement only that milestone.
7. Test it in Roblox Studio.
8. Inspect Studio output and errors.
9. Fix problems.
10. Retest.
11. Only proceed after the milestone is functioning correctly.

Never replace working systems simply because a different architecture would be preferable.

Never create large monolithic scripts containing unrelated systems.

Prefer modular, reusable, data-driven systems.

## PRIORITY ORDER

When deciding what to work on, prioritize:

1. Core gameplay functionality
2. Combat feel and responsiveness
3. Player progression
4. Equipment and visual progression
5. Persistence and data integrity
6. Security / server authority
7. UI / player experience
8. Performance
9. Original art and visual polish
10. Monetization
11. Long-term expansion systems

A feature described later in this document does NOT automatically have higher priority than a foundational system described earlier.

## VERTICAL SLICE FIRST

The first objective is to create a small but highly polished vertical slice proving the game's fundamental loop:

PLAYER  
→ FIGHT  
→ WIN  
→ RECEIVE REWARD  
→ EQUIP ITEM  
→ CHARACTER VISUALLY CHANGES  
→ PLAYER BECOMES STRONGER  
→ PLAYER WANTS TO FIGHT AGAIN

Do not begin building guilds, trading, housing, seasonal events, large collections, or extensive monetization before this loop is fun and stable.

## ASK BEFORE LARGE ARCHITECTURAL CHANGES

If implementation reveals that an important architectural decision needs to change, explain the issue and proposed solution before making a large destructive change.

Small implementation decisions may be made autonomously when they are clearly consistent with this specification.

## QUALITY OVER QUANTITY

A small number of polished systems and memorable assets is preferable to a large amount of unfinished content.

The goal is not to make the game appear large during development.

The goal is to make the game genuinely fun.

## MOST IMPORTANT DESIGN TEST

Whenever a feature is implemented, consider:

"Does this make the game more fun?"

"Does this give the player something meaningful to pursue?"

"Does this make the player's character more unique?"

"Does this reinforce the identity of the game?"

"Would a player want to show this to another player?"

If not, reconsider whether the feature belongs.

## DO NOT ASSUME EXAMPLES ARE FINAL

Names, weapons, bosses, worlds, classes, statistics, drop rates, and other examples in this document are design examples unless explicitly identified as requirements.

Claude should preserve the underlying design intent while improving specific implementations where appropriate.

## ORIGINALITY

The game must establish its own identity.

Do not reproduce recognizable characters, weapons, armor, UI, environments, terminology, or other distinctive intellectual property from existing games.

Genre inspiration is acceptable.

Direct imitation is not.

## WHEN UNCERTAIN

If a decision could materially affect:

- Core combat
- Player progression
- Save data
- Economy
- PvP balance
- Monetization
- Major architecture
- Asset pipeline

Claude should stop and explain the proposed approach before proceeding rather than making a large assumption.

**PRODUCT REQUIREMENTS SPECIFICATION**

**Working Title: ARENA: LEGENDS**

**Platform:** Roblox  
**Development Environment:** Roblox Studio  
**Development Assistant:** Claude Desktop connected to Roblox Studio through MCP  
**Genre:** Multiplayer PvP Arena Fighter + PvE RPG + Character Progression + Equipment Collection  
**Primary Gameplay:** Fast-paced arena combat  
**Secondary Gameplay:** PvE dungeons, bosses, loot collection, character progression, equipment customization, achievements, exploration  
**Target:** Roblox players who enjoy fighting games, RPG progression, collecting rare equipment, showing off achievements, and competitive PvP.

**1\. PRODUCT VISION**

Create a unique Roblox multiplayer game where **fighting is the primary gameplay activity**, but the player has a deep RPG progression system surrounding the combat.

The core player fantasy is:

**"I am building my own legendary warrior."**

Players should fight, improve their character, acquire increasingly rare equipment, unlock abilities, defeat bosses, win PvP matches, complete achievements, and visibly transform their character as they progress.

The player's character should tell a story.

A player walking through the central lobby should be able to look at another player's character and immediately understand that the player has accomplished something.

For example:

- A flaming helmet may indicate a difficult PvE boss achievement.
- A distinctive armor set may indicate a 10-win PvP streak.
- A rare weapon may have a very low boss drop rate.
- A special aura may indicate a prestigious achievement.
- A unique title may indicate a difficult accomplishment.

The game should make players think:

"I want that armor."

"How did he get that weapon?"

"I want to defeat that boss."

"I want that PvP title."

"I want my character to look like that."

The game should create a continuous progression loop:

**FIGHT → REWARD → EQUIP → IMPROVE → UNLOCK → FIGHT HARDER → ACQUIRE RARER ITEMS → SHOW OFF → REPEAT**

**2\. CORE DESIGN PRINCIPLE**

The game is NOT intended to be:

- A generic simulator
- A generic clicker
- A generic obby
- A simple sword fighting game
- A direct clone of Mortal Kombat
- A direct clone of Blox Fruits
- A direct clone of Pet Simulator
- A generic Roblox RPG using free marketplace assets

The game should combine familiar successful mechanics while developing its own identity.

The primary inspiration is:

**Arena fighting + RPG progression + equipment collection + achievement-based prestige.**

Fighting should always remain the heart of the game.

**3\. HIGH-LEVEL GAME LOOP**

The basic gameplay loop:

1. Enter the central lobby.
2. Customize/view character.
3. Select equipment and abilities.
4. Enter PvP, PvE, dungeon, or boss content.
5. Fight.
6. Earn XP, currency, equipment, materials, and achievements.
7. Return to the lobby.
8. Equip new items.
9. Character visually changes.
10. Improve stats/build.
11. Unlock harder content.
12. Repeat.

The player should almost always have something they are working toward.

**4\. CENTRAL LOBBY**

The lobby should be a large, visually impressive, social environment.

It should NOT feel like a menu.

Players should physically walk around the lobby.

The lobby should contain portals or entrances to different gameplay systems.

Initial areas:

**PVP ARENA**

Competitive player-vs-player combat.

**DUNGEONS**

PvE combat through progressively harder areas.

**BOSS RAIDS**

Large boss encounters.

**CHALLENGES**

Special objectives that reward unique equipment.

**ARMORY**

Equipment and inventory management.

**CHARACTER HALL**

Character sheet and visual customization.

**BLACKSMITH**

Equipment upgrading/crafting.

**ACHIEVEMENT HALL**

Display achievements and trophies.

Future:

**GUILD HALL**

Guilds/clans and social progression.

**5\. PLAYER CHARACTER**

The player should have a persistent RPG character.

The Roblox avatar should NOT simply remain in the default Roblox appearance.

Equipment should visibly modify the player's appearance.

Equipment categories should include:

- Helmet
- Chest Armor
- Shoulders
- Gloves
- Legs
- Boots
- Cape
- Weapon
- Off-hand
- Accessories
- Aura
- Cosmetic effects

The system should be modular so new equipment can be added without rewriting the character system.

**6\. EQUIPMENT VISUAL SYSTEM**

This is one of the MOST IMPORTANT systems in the game.

Equipment must have a visible effect on the player's character.

If a player equips:

**Dragonbone Helmet**

the helmet should visibly appear on the character.

If they equip:

**Dragonbone Chestplate**

the chest armor should visibly appear.

If they equip:

**Inferno Greatsword**

the weapon should appear attached to the character.

Equipment should not simply be an icon and a stat increase.

The player's appearance should communicate progression.

**7\. EQUIPMENT PROVENANCE**

Every important equipment item should have an origin.

Example:

**Dragonbone Greatsword**

**Rarity:** Legendary  
**Power:** 92  
**Source:** Ancient Dragon  
**Drop Rate:** 2%  
**Set:** Dragonbone  
**Special Effect:** Fire damage  
**Visual Effect:** Subtle flame particles

Another example:

**Blood Champion Armor**

**Rarity:** Mythic  
**Source:** Win 10 consecutive PvP matches  
**Special:** Crimson aura  
**Prestige:** Extremely High

The game should distinguish between:

**POWER**

How strong the item is.

and

**PRESTIGE**

How difficult or impressive it is to obtain.

A prestigious item does not necessarily need to be the strongest item.

This is important because players should have reasons to pursue equipment for status, appearance, and achievement rather than only raw stats.

**8\. EQUIPMENT RARITY**

Initial rarity system:

- Common
- Uncommon
- Rare
- Epic
- Legendary
- Mythic
- Unique

The visual presentation should clearly communicate rarity.

Examples:

Common:  
Simple appearance.

Rare:  
More elaborate design.

Epic:  
Distinctive design and effects.

Legendary:  
Highly recognizable visual design and moderate VFX.

Mythic:  
Extremely distinctive design and effects.

Unique:  
Reserved for exceptional accomplishments.

Avoid excessive particle effects.

The highest rarity should feel special.

**9\. EQUIPMENT SETS**

Some equipment should belong to sets.

Example:

**DRAGONBONE SET**

- Dragonbone Helmet
- Dragonbone Chest
- Dragonbone Gloves
- Dragonbone Legs
- Dragonbone Boots
- Dragonbone Greatsword

Equipping multiple pieces could provide set bonuses.

Example:

2 pieces:  
+5% health

4 pieces:  
+10% fire resistance

6 pieces:  
Dragonfire visual effect

The final set bonus should be meaningful but not game-breaking.

**10\. CHARACTER SHEET**

The player should have a full RPG-style character sheet.

Example:

```
CHARACTER
NAME
TITLE
LEVEL 27
HEALTH
1,240
STRENGTH
86
DEFENSE
71
SPEED
64
POWER
52
PVP WINS
147
PVP LOSSES
63
BOSSES DEFEATED
32
DUNGEONS COMPLETED
86
```

The character sheet should also show:

- Equipped weapon
- Equipped armor
- Abilities
- Current build
- Level
- XP
- PvP rank
- Titles
- Achievements
- Equipment score
- Statistics

**11\. INVENTORY**

Create a real RPG inventory system.

The player should be able to:

- View equipment
- Equip equipment
- Unequip equipment
- Compare equipment
- Lock equipment
- Sell equipment
- Sort equipment
- Filter by rarity
- Filter by category
- View item origin
- View item statistics
- View item description

Items should be visually represented.

Example:

```
DRAGONBONE GREATSWORD
LEGENDARY
POWER: 92
SOURCE:
Ancient Dragon
DROP RATE:
2%
SPECIAL:
Dragonfire
[ EQUIP ]
[ LOCK ]
[ SELL ]
```

**12\. LOADOUT SYSTEM**

Players should be able to save complete builds.

Example:

**LOADOUT 1**

BERSERKER

Dragonbone Armor  
Inferno Greatsword  
Flame Dash  
Berserk

**LOADOUT 2**

ASSASSIN

Shadow Armor  
Twin Daggers  
Shadow Step  
Execution

**LOADOUT 3**

TANK

Warlord Armor  
Warhammer  
Shield Bash  
Iron Fortress

Players should eventually be able to maintain multiple builds.

Additional loadout slots may eventually be monetized.

**13\. COMBAT SYSTEM**

Combat is the most important gameplay system.

The initial combat system should be relatively simple but feel responsive.

Potential controls:

**Left Mouse:** Light Attack

**Right Mouse:** Heavy Attack

**Q:** Ability 1

**E:** Ability 2

**R:** Ultimate

**F:** Block

**Space:** Dodge

The exact control scheme may be refined during implementation.

Combat should include:

- Attack animations
- Hit reactions
- Damage numbers
- Hit effects
- Sound effects
- Blocking
- Dodging
- Cooldowns
- Stamina or another combat resource
- Ability effects
- Knockback
- Death
- Respawn

Combat should feel responsive.

Avoid excessive delays between input and result.

**14\. COMBAT PHILOSOPHY**

Character statistics should matter.

However:

**STATS MUST NOT COMPLETELY DETERMINE PVP OUTCOMES.**

A skilled lower-level player should be able to defeat a stronger player.

Skill should matter.

Combat should reward:

- Timing
- Dodging
- Blocking
- Ability selection
- Positioning
- Combos
- Knowing opponent abilities

Do not create a system where the player with the most expensive equipment automatically wins.

**15\. INITIAL CLASSES / BUILDS**

The first release may begin with a small number of archetypes.

**BERSERKER**

High damage.

Low defense.

Abilities:

- Rage
- Whirlwind
- Execution

**PALADIN**

High defense.

Healing.

Abilities:

- Shield Bash
- Holy Ground
- Divine Shield

**ASSASSIN**

Fast movement.

High burst damage.

Low health.

Abilities:

- Shadow Step
- Backstab
- Smoke Bomb

**MAGE**

Ranged combat.

Lower defense.

Abilities:

- Fireball
- Meteor
- Teleport

The class system should be designed so additional classes can be added later.

**16\. PVP SYSTEM**

PvP should be the primary competitive gameplay system.

Initial modes:

**1v1**

Single combat.

**2v2**

Team combat.

**Free-for-All**

Multiple players in an arena.

Future:

- Ranked
- Tournaments
- Team battles
- Seasonal competitions
- Special event modes

Players should earn:

- XP
- Currency
- PvP rating
- Titles
- Achievements
- Equipment
- Cosmetic rewards

**17\. PVP PRESTIGE REWARDS**

PvP should provide equipment that cannot simply be purchased.

Examples:

**10 PvP Wins**

Champion Gloves

**25 PvP Wins**

Champion Boots

**50 PvP Wins**

Champion Chestplate

**100 PvP Wins**

Champion Armor Set

**10 Win Streak**

Blood Champion Helmet

**25 Win Streak**

Blood Champion Weapon

**100 Ranked Wins**

Warlord Title

This creates prestige.

**18\. PVE SYSTEM**

PvE should provide a second progression path.

Players fight:

- Wolves
- Goblins
- Skeletons
- Orcs
- Demons
- Dragons
- Golems
- Undead
- Elemental creatures
- Other unique enemies

Each area should have its own visual identity.

**19\. WORLDS**

Initial example:

**WORLD 1 — THE GRASSLANDS**

Enemies:

- Wolves
- Goblins
- Bandits

Boss:

**Goblin King**

**WORLD 2 — THE VOLCANIC REALM**

Enemies:

- Fire Goblins
- Lava Monsters
- Fire Elementals

Boss:

**Volcanic Dragon**

**WORLD 3 — THE FROZEN KINGDOM**

Enemies:

- Ice Wolves
- Ice Golems
- Frost Knights

Boss:

**Frost King**

**WORLD 4 — THE SHADOW REALM**

Enemies:

- Demons
- Skeletons
- Vampires

Boss:

**Shadow Lord**

These are examples only.

The actual final game should develop its own original lore, names, creatures, and visual identity.

**20\. BOSS SYSTEM**

Bosses should be memorable.

A boss should not simply be a larger normal enemy.

Bosses should have:

- Unique model
- Unique animations
- Multiple attacks
- Phases
- Unique abilities
- Unique sound
- Unique arena
- Unique loot
- Unique equipment

Example:

**ANCIENT DRAGON**

Phase 1:  
Ground combat.

Phase 2:  
Flying attacks.

Phase 3:  
Firestorm.

Phase 4:  
Enraged.

Possible drops:

Dragonbone Helmet  
Dragonbone Chest  
Dragonbone Greatsword  
Dragonfire Aura

Rare drops should be genuinely exciting.

**21\. ACHIEVEMENT SYSTEM**

Achievements are extremely important.

Examples:

**PVP**

First Blood

10 Wins

50 Wins

100 Wins

10 Kill Streak

25 Kill Streak

100 Ranked Wins

**PVE**

Kill 100 Wolves

Kill 1,000 Monsters

Defeat Ancient Dragon

Defeat Ancient Dragon Solo

Complete Dungeon Without Dying

**EXPLORATION**

Discover Forest

Discover Volcano

Discover Frozen Kingdom

Discover Shadow Realm

**SKILL**

Win Without Taking Damage

Defeat Boss Using Basic Attacks Only

Win PvP With No Abilities

Complete Dungeon Under Time Limit

Achievements can reward:

- Titles
- Equipment
- Cosmetics
- Auras
- Currency
- Special effects

**22\. TITLES**

Players should be able to display titles.

Examples:

**Novice**

**Monster Hunter**

**Dungeon Master**

**Champion**

**Warlord**

**Dragon Slayer**

**Blood Champion**

**Arena Legend**

Titles should appear above or near the player's character.

**23\. VISUAL PRESTIGE**

The lobby should function as a showcase.

Players should be able to see:

- Armor
- Weapons
- Auras
- Titles
- Effects
- Pets/companions if eventually implemented
- Level
- Rank

Players should be able to inspect another player.

Example:

```
BLOOD CHAMPION
Level 47
PvP Wins: 317
[INSPECT]
```

Inspection should show their character and selected equipment.

**24\. ART DIRECTION**

THIS IS A HIGH PRIORITY REQUIREMENT.

The game must develop a recognizable visual identity.

Do NOT build the entire game from generic Roblox Creator Store models.

We want the game to look like it belongs to its own universe.

The preferred hierarchy is:

**1\. ORIGINAL ASSETS**

Create original models, textures, icons, VFX, UI elements, weapons, armor, enemies, etc.

**2\. PROCEDURALLY/PROGRAMMATICALLY CREATED ASSETS**

When practical, generate assets through Blender Python, Roblox Studio scripting, procedural geometry, textures, or other tools.

**3\. FREE CREATOR STORE ASSETS**

Free assets may be used when necessary, particularly for:

- Temporary prototypes
- Generic environment components
- Development placeholders
- Infrastructure
- Assets that would be unreasonable to recreate

However, Creator Store assets should NOT define the visual identity of the final game.

**4\. PAID THIRD-PARTY ASSETS**

Do not purchase assets without explicit approval.

**25\. ORIGINAL ART REQUIREMENT**

Whenever possible, create unique:

- Weapons
- Armor
- Helmets
- Shields
- Bosses
- Monsters
- UI icons
- Item icons
- Ability icons
- VFX
- Auras
- Environment props
- Portals
- Signs
- Emblems
- Logos
- Achievement badges

Avoid recognizable copies of existing Roblox games.

Do not copy:

- Existing game's characters
- Existing game's logos
- Existing game's weapons
- Existing game's armor
- Existing game's UI
- Existing game's names
- Existing game's distinctive visual designs

The game should be inspired by the genre, not copied from another game.

**26\. IMAGE / SPRITE REQUIREMENT**

The game should use unique artwork for:

- Inventory icons
- Equipment icons
- Ability icons
- Achievement icons
- Class icons
- Currency icons
- UI decorations
- Loading screens
- Promotional graphics
- Item thumbnails

If a suitable original asset cannot be created directly in Roblox, create a custom image/sprite/texture rather than immediately searching for an existing asset.

All custom artwork should maintain a consistent art direction.

The same visual language should be used across:

- UI
- Weapons
- Armor
- Icons
- Enemies
- Environments
- VFX

**27\. ART ASSET PIPELINE**

Create an organized asset system.

Example:

```
ReplicatedStorage
    Assets
        Weapons
        Armor
        Characters
        Enemies
        Effects
        UI
        Icons
        Sounds
```

Use consistent naming.

Example:

```
Weapon_InfernoGreatsword
Armor_DragonboneHelmet
Armor_DragonboneChest
Effect_DragonFire
Icon_DragonboneGreatsword
Ability_FlameDash
```

Do not create hundreds of randomly named objects.

**28\. UNIQUE VISUAL IDENTITY**

Before creating large quantities of assets, establish a visual style guide.

Define:

- Color philosophy
- Material philosophy
- Armor design philosophy
- Weapon design philosophy
- UI style
- Icon style
- VFX style
- Enemy design philosophy
- Environment style

The goal is for a screenshot of the game to be recognizable as this game.

**29\. UI DESIGN**

The UI should feel like an RPG rather than a generic Roblox menu.

Important screens:

**Character**

3D character preview + stats.

**Inventory**

Grid-based RPG inventory.

**Equipment**

Equipment slots surrounding character.

**Abilities**

Ability cards and cooldowns.

**Achievements**

Achievement collection.

**Map**

World/dungeon selection.

**Shop**

Game purchases.

**Settings**

Controls, audio, graphics, etc.

UI should be clean and readable.

Do not overwhelm new players.

**30\. ECONOMY**

The game should have an in-game currency.

Possible currency:

**Gold**

Gold is earned through:

- PvP
- PvE
- Dungeons
- Quests
- Bosses
- Achievements

Potential secondary currency later:

**Crystals**

Used for special systems.

The economy must be designed to prevent runaway inflation.

**31\. ROBUX MONETIZATION**

Monetization should support the game without destroying fairness.

Potential purchases:

**GAME PASSES**

VIP

Extra Inventory Slots

Extra Loadout Slots

2x XP

2x Gold

Special Emotes

Special Cosmetic Effects

**DEVELOPER PRODUCTS**

Temporary XP boost

Temporary Gold boost

Temporary Luck boost

Dungeon ticket

Boss summon

Revive

Consumable cosmetic effects

The monetization system should NEVER require players to spend Robux to participate.

The strongest prestige equipment should remain obtainable through gameplay.

**32\. PAY-TO-WIN POLICY**

Avoid extreme pay-to-win mechanics.

A player should never be able to purchase:

"Guaranteed PvP victory."

Robux should primarily provide:

- Convenience
- Cosmetics
- Accelerated progression
- Additional customization
- Optional temporary boosts
- Additional loadouts
- Additional inventory capacity

Competitive skill must remain important.

**33\. SOCIAL SYSTEM**

Players should naturally interact.

Potential features:

- Player inspection
- Titles
- Leaderboards
- PvP rankings
- Guilds
- Trading
- Party system
- Friend bonuses
- Group dungeons

Trading should be considered carefully and only implemented after the core economy is stable.

**34\. LEADERBOARDS**

Potential leaderboards:

**MOST PVP WINS**

**HIGHEST PVP RATING**

**MOST BOSSES DEFEATED**

**MOST DUNGEONS COMPLETED**

**HIGHEST LEVEL**

**RAREST EQUIPMENT**

Leaderboards should encourage competition without making the game feel impossible for new players.

**35\. PLAYER DATA**

Player progression must persist.

Save:

- Level
- XP
- Gold
- Equipment
- Inventory
- Equipment upgrades
- Achievements
- Titles
- PvP statistics
- PvE statistics
- Loadouts
- Unlocked worlds
- Settings where appropriate

DataStore handling must be robust.

Do not create systems that can easily duplicate or destroy player items.

**36\. SECURITY / ANTI-EXPLOIT**

Important game logic must be server authoritative.

Never trust the client for:

- Damage
- Currency
- Item ownership
- Item creation
- XP
- PvP results
- Rewards

The client may request an action.

The server validates the action.

Example:

Client:

"Player attacked enemy."

Server:

"Is this player close enough?"

"Is the ability off cooldown?"

"Is the player alive?"

"Is the target valid?"

"Calculate damage."

"Apply damage."

"Give rewards."

**37\. PERFORMANCE**

The game must support Roblox's broad range of devices.

Avoid unnecessarily expensive:

- Particle systems
- Physics objects
- Loops
- RemoteEvents
- High-poly assets
- Constant server calculations

Combat must remain responsive.

Optimize before adding unnecessary visual complexity.

**38\. AUDIO**

Audio should also be unique.

Create or source appropriately licensed/custom:

- Sword sounds
- Hit sounds
- Block sounds
- Ability sounds
- Boss sounds
- UI sounds
- Victory sounds
- Defeat sounds
- Ambient music
- Lobby music

The game should eventually have its own audio identity.

Do not simply fill the game with random Creator Store audio.

**39\. FIRST PLAYABLE VERSION**

DO NOT attempt to build the entire game immediately.

The first milestone should be a vertical slice.

The first playable version should contain ONLY:

**Lobby**

One small but polished lobby.

**Character**

Basic customizable character.

**Combat**

One weapon.

Basic attack.

Heavy attack.

Block.

Dodge.

**PvP**

One arena.

1v1 combat.

**PvE**

Three enemy types.

**Boss**

One boss.

**Equipment**

Approximately 5–10 pieces of equipment.

**Inventory**

Basic inventory.

**Character Sheet**

Basic stats.

**Equipment Visuals**

At least helmet, chest, weapon.

**Progression**

Level + XP.

**Saving**

Basic persistent player data.

The goal is to prove:

**Fighting → Reward → Equipment → Character Changes → Progression**

before building the rest.

**40\. DEVELOPMENT PHASES**

**PHASE 1 — FOUNDATION**

- Project architecture
- Folder structure
- Player data
- Server/client architecture
- Basic player character
- Basic UI framework

**PHASE 2 — COMBAT**

- Basic attacks
- Heavy attack
- Block
- Dodge
- Damage
- Hit detection
- Health
- Death
- Respawn
- Combat effects

**PHASE 3 — FIRST ARENA**

- Arena map
- Match system
- 1v1
- Countdown
- Victory
- Defeat
- Rewards

**PHASE 4 — RPG**

- XP
- Levels
- Gold
- Character sheet
- Stats

**PHASE 5 — EQUIPMENT**

- Inventory
- Equipment slots
- Weapons
- Armor
- Equipment stats
- Visible equipment

**PHASE 6 — PVE**

- Enemy framework
- Multiple enemies
- Loot
- Dungeon
- Boss

**PHASE 7 — ACHIEVEMENTS**

- Achievement framework
- Titles
- PvP achievements
- PvE achievements
- Equipment rewards

**PHASE 8 — POLISH**

- Original art
- VFX
- Sound
- UI
- Animations
- Lobby
- Effects

**PHASE 9 — MONETIZATION**

Only after the game is fun without monetization:

- Game passes
- Developer products
- Shop
- VIP
- Boosts
- Cosmetics

**PHASE 10 — LIVE GAME**

- Analytics
- Balancing
- Bug fixes
- New equipment
- New bosses
- New maps
- New PvP modes
- Seasonal content

**41\. DEVELOPMENT RULE FOR CLAUDE**

Claude must NOT attempt to implement every feature at once.

Work incrementally.

For each feature:

1. Explain the intended architecture.
2. Implement the smallest functional version.
3. Test it.
4. Inspect for errors.
5. Fix errors.
6. Test again.
7. Only then move to the next feature.

Do not create enormous scripts containing unrelated systems.

Prefer modular systems.

Use one logical responsibility per module/script where practical.

**42\. MCP DEVELOPMENT WORKFLOW**

Claude is connected to Roblox Studio through MCP.

Claude should use the MCP connection to:

- Inspect the current Roblox project
- Create required folders
- Create scripts
- Modify scripts
- Create models where practical
- Inspect output/errors
- Test systems
- Iterate
- Verify objects exist
- Verify scripts are connected correctly

Claude should inspect the existing project before modifying it.

Do not blindly overwrite existing work.

Before significant changes, understand the existing architecture.

**43\. SELF-TESTING REQUIREMENT**

Every major system should have a test procedure.

Examples:

**COMBAT TEST**

- Spawn two players/test dummies.
- Attack.
- Confirm damage.
- Confirm cooldown.
- Confirm block.
- Confirm dodge.
- Confirm death.

**INVENTORY TEST**

- Obtain item.
- Confirm item appears.
- Equip item.
- Confirm character visually changes.
- Unequip.
- Confirm appearance changes back.

**SAVE TEST**

- Obtain item.
- Leave.
- Rejoin.
- Confirm item remains.

**BOSS TEST**

- Enter boss area.
- Fight boss.
- Kill boss.
- Confirm rewards.
- Confirm rare drop logic.

**44\. ERROR HANDLING**

Claude should actively monitor Roblox Studio output/errors during development.

Do not assume code works simply because it was written.

After implementing a system:

- Run it.
- Inspect errors.
- Test expected behavior.
- Fix issues.
- Retest.

If MCP provides access to Studio output, use it.

**45\. EXPANSION PHILOSOPHY**

The architecture must make future content easy to add.

Adding a new weapon should ideally require:

1. Create weapon definition.
2. Create model.
3. Define stats.
4. Define abilities/effects.
5. Add acquisition source.

Adding a new armor piece should ideally require:

1. Create armor model.
2. Define stats.
3. Define rarity.
4. Define acquisition source.
5. Add equipment definition.

Adding a new boss should ideally require:

1. Boss model.
2. Boss behavior.
3. Boss abilities.
4. Loot table.
5. Arena.
6. Rewards.

Do not hard-code every item individually into unrelated scripts.

**46\. CONTENT DATABASE**

Where practical, item definitions should be data-driven.

For example:

```
ItemId
Name
Type
Rarity
Power
Defense
Source
DropChance
SetId
VisualAsset
IconAsset
SpecialEffect
Description
```

This allows hundreds of items to eventually exist without rewriting the inventory system.

**47\. ITEM INSPECTION**

When a player clicks an item, show:

**NAME**

**RARITY**

**POWER**

**STATS**

**SOURCE**

**DROP RATE**

**SET**

**SPECIAL EFFECT**

**DESCRIPTION**

Example:

```
╔══════════════════════════════════╗
        DRAGONBONE HELMET
             MYTHIC
Defense: +42
Health: +120
Source:
Ancient Dragon
Drop Rate:
1.5%
Set:
Dragonbone
Special:
Dragon's Fury
"Forged from the bones
of an ancient dragon."
╚══════════════════════════════════╝
```

**48\. ITEM HISTORY / PRESTIGE**

For particularly rare equipment, consider showing additional information.

Example:

```
OBTAINED BY:
KyleTheDestroyer
September 11, 2026
Ancient Dragon
Drop #381
```

This is optional and should only be implemented if it can be done efficiently.

The overall goal is to make rare equipment feel meaningful.

**49\. NO GENERIC ASSET DUMP**

Do NOT populate the game with hundreds of random assets simply to make the game look complete.

Quality > quantity.

It is preferable to have:

**5 amazing weapons**

rather than:

**50 generic weapons.**

It is preferable to have:

**3 unique bosses**

rather than:

**20 recolored enemies.**

**50\. ORIGINALITY REQUIREMENT**

The final game should have its own:

- Lore
- Names
- Characters
- Equipment
- Monsters
- Bosses
- Visual style
- UI
- Icons
- Effects
- Maps
- Sound design
- Progression system

Do not simply rename existing game mechanics and assets.

The objective is to create a game that players recognize as its own IP.

**51\. SUCCESS CRITERIA**

The game is successful if a new player can enter and within the first several minutes think:

"I want better gear."

Then:

"I want to see what the next area has."

Then:

"I want to beat that boss."

Then:

"I want that armor."

Then:

"I want to get good enough to beat other players."

And eventually:

"I need to get that legendary item."

The game should continuously create short-term, medium-term, and long-term goals.

**52\. THE MOST IMPORTANT DESIGN TEST**

Whenever adding a feature, ask:

**Does this make fighting more fun?**

**Does this give the player something to work toward?**

**Does this create meaningful progression?**

**Does this make the player's character more unique?**

**Does this create a reason to return?**

**Does this create something worth showing other players?**

If the answer to all of these is "no", the feature may not belong in the game.

**53\. FINAL DEVELOPMENT GOAL**

The finished experience should feel like:

**A competitive fantasy arena fighter wrapped inside a collectible RPG.**

Players don't simply level up.

They build an identity.

They develop a fighting style.

They collect equipment.

They earn prestige.

They become recognizable.

They show off their accomplishments.

The ultimate objective is for players to look at another character and immediately think:

**"I want to become that guy."**

**54\. ASSET FACTORY & ORIGINAL CONTENT GENERATION SYSTEM**

The game should not rely on manually creating every weapon, armor piece, enemy, icon, or cosmetic individually.

Instead, develop a reusable **Asset Factory** architecture that allows new game content to be generated consistently while maintaining a unique visual identity.

The Asset Factory should become one of the core development tools for the project.

**54.1 ASSET FACTORY PHILOSOPHY**

The goal is:

**Create a system that can continuously produce unique, high-quality game content without requiring the entire game to be redesigned every time a new item is added.**

Do not create:

"Generic Sword #47"

Instead, every important item should have:

- A unique name
- A unique visual concept
- A reason for existing
- A unique acquisition method
- Appropriate rarity
- Appropriate statistics
- A visual identity
- A relationship to the game's world/lore where appropriate

Examples:

**Goblin Cleaver**

Crude, chipped, ugly weapon.

**Source:** Goblin Chieftain

**Knight's Oath**

Elegant ceremonial longsword.

**Source:** Knight's Trial

**Inferno Greatsword**

Massive black blade with glowing cracks.

**Source:** Volcanic Dragon

**Bloodfang**

Demonic curved weapon.

**Source:** PvP achievement

**Warlord's Executioner**

Large ceremonial execution weapon.

**Source:** 100 ranked PvP victories

The player should be able to recognize an item's origin from its appearance.

**54.2 ASSET FACTORY COMPONENTS**

Create reusable systems such as:

```
AssetFactory
    WeaponFactory
    ArmorFactory
    HelmetFactory
    ChestArmorFactory
    ShoulderFactory
    GloveFactory
    LegArmorFactory
    BootFactory
    ShieldFactory
    AccessoryFactory
    BossFactory
    EnemyFactory
    VFXFactory
    IconFactory
    UIAssetFactory
```

The exact architecture may differ if a better approach is discovered.

The important requirement is that the system remains modular and expandable.

**54.3 MODULAR ARMOR SYSTEM**

Where practical, armor should be constructed from reusable components.

Example:

```
Helmet
    Base
    Visor
    Horns
    Crest
    SideArmor
    DecorativeElements
Chest
    Base
    ShoulderLeft
    ShoulderRight
    ChestPlate
    BackPlate
    DecorativeElements
Legs
    UpperArmor
    KneeArmor
    LowerArmor
Boots
    Base
    ShinArmor
    DecorativeElements
```

Components should be designed so they can be combined into different equipment sets.

For example:

**Blood Warlord**

Heavy helmet  
Curved horns  
Crimson crest  
Skull visor  
Large shoulder armor

**Demon King**

Crown helmet  
Enormous horns  
Glowing eyes  
Demonic shoulder armor  
Spiked chest armor

These should look like genuinely different designs, not simple recolors.

**54.4 PROCEDURAL / PROGRAMMATIC GENERATION**

Whenever practical, use procedural or programmatic generation to create assets.

Potential technologies include:

- Roblox Studio procedural modeling
- Roblox mesh generation where appropriate
- Blender
- Blender Python
- Procedural geometry
- Material generation
- Texture generation
- Automated export/import pipelines

Claude should determine which method is most appropriate for each asset.

Do not force everything through one technology if another produces a substantially better result.

**54.5 BLENDER ASSET PIPELINE**

When Blender is the appropriate tool, Claude should be capable of creating Blender Python scripts that generate assets.

For example:

```
GenerateDragonboneHelmet.py
GenerateInfernoGreatsword.py
GenerateBloodWarlordArmor.py
GenerateGoblinCleaver.py
```

A Blender generation script should ideally:

1. Clear or create the appropriate scene.
2. Generate the model.
3. Create materials.
4. Apply appropriate proportions.
5. Create attachment points where required.
6. Set object names.
7. Organize objects.
8. Optimize geometry.
9. Prepare the asset for Roblox.
10. Export the appropriate file.
11. Preserve a reproducible source script.

The source Python script should be retained so the asset can be regenerated or modified later.

**54.6 ASSET NAMING**

Every generated asset must use consistent names.

Examples:

```
Weapon_InfernoGreatsword
Weapon_GoblinCleaver
Weapon_Bloodfang
Armor_DragonboneHelmet
Armor_DragonboneChest
Armor_DragonboneShoulders
Armor_BloodWarlordHelmet
Armor_BloodWarlordChest
Boss_AncientDragon
Boss_VolcanicDragon
Enemy_GoblinWarrior
Enemy_FireElemental
```

Do not use names such as:

```
Part
MeshPart
MeshPart2
Thing
SwordNew
SwordNew2
FinalSword
FinalSwordFinal
```

**54.7 ASSET QUALITY CHECKS**

Generated assets must go through automated and/or manual quality checks.

At minimum check:

**Geometry**

- Valid geometry
- No obvious broken geometry
- Reasonable polygon count
- No unnecessary geometry
- Appropriate scale
- Appropriate proportions

**Naming**

- Correct object names
- Correct hierarchy
- No accidental duplicate names

**Materials**

- Materials exist
- Materials are assigned correctly
- No missing references

**Character Compatibility**

For armor:

- Fits the player character
- Does not excessively intersect the body
- Does not float away from the body
- Does not interfere with animations
- Has correct attachment points

**Weapons**

- Correct grip position
- Correct orientation
- Correct scale
- Can be attached to the player
- Does not intersect the character excessively

**Roblox Compatibility**

- Correct import format
- Appropriate triangle count
- Appropriate texture resolution
- No unnecessary objects
- No missing dependencies

An asset should not be considered finished simply because it successfully imported into Roblox.

**54.8 ASSET VARIATION**

The Asset Factory should support controlled variation.

For example:

```
Helmet Shape
+ Horn Type
+ Crest
+ Material
+ Decorative Elements
+ Color Scheme
+ VFX
```

could produce multiple visually distinct helmets.

However:

**DO NOT generate meaningless random variations.**

Variations should make thematic sense.

A fire-themed helmet should look like fire-themed equipment.

An undead-themed helmet should look undead.

A PvP champion helmet should look prestigious and competitive.

**54.9 RARITY SHOULD AFFECT VISUAL DESIGN**

Rarity should not only change a text label.

Higher rarity should generally have:

- More elaborate geometry
- More distinctive silhouettes
- Better materials
- More unique details
- More interesting VFX
- More memorable designs

For example:

**COMMON**

Simple iron sword.

**RARE**

Decorated steel sword.

**EPIC**

Ornate magical sword.

**LEGENDARY**

Extremely distinctive weapon with unique materials and subtle VFX.

**MYTHIC**

Visually exceptional weapon with unique geometry, materials, and effects.

**UNIQUE**

Reserved for extremely difficult or prestigious accomplishments.

Avoid simply making Common → Rare → Epic by changing the color.

**54.10 SOURCE SHOULD INFLUENCE DESIGN**

The method of obtaining an item should influence its appearance.

**PVE BOSS ITEM**

Should visually relate to the boss.

Example:

Ancient Dragon:

- Scales
- Horns
- Bones
- Fire
- Ancient markings

**PVP REWARD**

Should visually communicate prestige.

Example:

Blood Champion:

- Arena-inspired design
- Distinctive silhouette
- Crimson effects
- Champion insignia

**EXPLORATION REWARD**

Should communicate discovery.

Example:

Lost Temple:

- Ancient stone
- Runes
- Archaeological details
- Ancient metals

**SECRET ITEM**

Should look unusual and mysterious.

**54.11 WEAPON FAMILIES**

Create recognizable weapon families.

Initial examples:

- Sword
- Greatsword
- Axe
- Great Axe
- Mace
- Hammer
- Spear
- Staff
- Daggers
- Dual Blades
- Bow

Each weapon family should have its own combat identity.

For example:

**Greatsword**

Slow.

High damage.

Large hitbox.

**Daggers**

Fast.

Low individual damage.

High mobility.

**Hammer**

Slow.

High stun potential.

**Spear**

Long reach.

Moderate damage.

The Asset Factory should allow new weapons to inherit from these categories.

**54.12 ARMOR FAMILIES**

Create thematic armor families.

Examples:

**Knight**

Heavy medieval armor.

**Berserker**

Large, aggressive, intimidating armor.

**Assassin**

Lightweight, dark, agile appearance.

**Paladin**

Bright, noble, defensive appearance.

**Demon**

Organic, corrupted, intimidating.

**Dragon**

Scales, horns, bones, fire motifs.

**Shadow**

Dark materials, subtle glowing effects.

These are starting concepts only.

The final game should create its own unique designs.

**54.13 VISUAL SILHOUETTE**

Important equipment should have a recognizable silhouette.

A player should be able to recognize:

"That's the Dragonbone Helmet."

even from a distance.

Avoid creating equipment where the only difference is:

- Color
- Small texture change
- Minor decoration

Major equipment should have meaningful visual differences.

**54.14 ICON FACTORY**

The Asset Factory should also generate inventory icons.

Whenever a new item is created, the system should ideally create:

1. 3D asset
2. Inventory icon
3. Item thumbnail
4. UI representation
5. Appropriate rarity presentation

The icon should visually match the actual equipment.

Do not use unrelated placeholder icons in the final game.

**54.15 VFX FACTORY**

Create reusable VFX components.

Examples:

```
Fire
Ice
Lightning
Shadow
Holy
Blood
Poison
Arcane
Earth
Wind
```

These can be combined with equipment and abilities.

Example:

```
Inferno Greatsword
    + Fire Trail
    + Ember Particles
    + Heat Distortion
Shadow Dagger
    + Dark Trail
    + Smoke
    + Shadow Burst
```

VFX should be visually impressive but performance-conscious.

**54.16 ORIGINAL ART PRIORITY**

The default assumption should be:

**Create it ourselves.**

Use Roblox Creator Store assets only when:

- They are generic infrastructure
- They are appropriate placeholders
- Creating the asset ourselves would provide little value
- There is a legitimate reason to use the asset
- Licensing allows the intended use

Important gameplay-defining assets should preferably be original.

This includes:

- Main weapons
- Major armor sets
- Bosses
- Important enemies
- Unique VFX
- UI
- Logos
- Item icons
- Achievement artwork

**54.17 NO ASSET CLONING**

Do not intentionally reproduce recognizable assets from:

- Mortal Kombat
- Blox Fruits
- Roblox BedWars
- Adopt Me
- Pet Simulator
- Other Roblox games
- Existing commercial games
- Movies
- Anime
- Other copyrighted IP

Genre inspiration is acceptable.

Direct visual copying is not.

The final game should have its own intellectual property and visual identity.

**54.18 CONTENT GENERATION WORKFLOW**

When a new item is requested, use this workflow:

**STEP 1**

Define the item concept.

**STEP 2**

Define:

- Name
- Rarity
- Source
- Stats
- Abilities
- Lore
- Visual theme

**STEP 3**

Create the visual design.

**STEP 4**

Generate the 3D asset.

**STEP 5**

Generate materials/textures.

**STEP 6**

Generate VFX if appropriate.

**STEP 7**

Generate inventory icon.

**STEP 8**

Import into Roblox.

**STEP 9**

Connect the item to the item database.

**STEP 10**

Connect acquisition/drop logic.

**STEP 11**

Connect equipment visuals.

**STEP 12**

Test the item.

**STEP 13**

Run asset quality checks.

**STEP 14**

Only then consider the item complete.

**54.19 EXAMPLE COMPLETE ITEM**

**INFERNO GREATSWORD**

**Item ID:**

```
weapon_inferno_greatsword
```

**Rarity:**

LEGENDARY

**Source:**

Volcanic Dragon

**Drop Rate:**

2%

**Weapon Type:**

Greatsword

**Power:**

92

**Special Effect:**

Dragonfire

**Visual Design:**

Massive blackened steel blade.

Glowing cracks run through the blade.

Large volcanic-metal guard.

Dark leather grip.

Subtle embers continuously fall from the blade.

When attacking, a brief fire trail follows the sword.

**Lore:**

"Forged in the heart of the volcanic realm from metal hardened by dragonfire."

**Prestige:**

High

The item should then be generated through the Asset Factory rather than manually assembled from random Roblox parts.

**54.20 LONG-TERM ASSET GOAL**

The ultimate goal is to create an internal content pipeline capable of producing:

- Hundreds of weapons
- Hundreds of armor pieces
- Dozens of bosses
- Dozens of enemy types
- Hundreds of icons
- Dozens of VFX types
- Multiple environments
- Seasonal equipment
- PvP reward sets
- PvE reward sets
- Achievement reward sets

while maintaining a consistent art style.

The system should make adding new content progressively easier.

**54.21 THE "WOULD I WANT THAT?" TEST**

Every major item should pass this test:

**If I saw another player wearing this item in the lobby, would I immediately want to know how they got it?**

If the answer is no, reconsider the design.

The best equipment should create desire.

Players should see another character and think:

"Holy shit, what armor is that?"

Then inspect the player and discover:

**Blood Warlord Armor**

Obtained by winning 25 consecutive ranked matches.

That should create a new goal for the player.

This is one of the primary progression mechanisms of the game.

**54.22 FINAL ASSET PRINCIPLE**

The game should never depend on having thousands of items.

It depends on having **memorable items**.

Five incredible weapons are better than fifty generic weapons.

Ten memorable armor sets are better than one hundred recolored armor sets.

Every major piece of equipment should contribute to the identity of the game.

The player should remember:

"The Inferno Greatsword."

"The Blood Warlord Armor."

"The Dragonbone Set."

"The Shadow King's Daggers."

These should become recognizable pieces of the game's world.

**CREATE ITEMS THAT PLAYERS WANT TO SHOW OFF.**

**55\. POLISH, PLAYER EXPERIENCE & GAME FEEL**

**55.1 The Game Must Feel Good Before It Feels Big**

The game should prioritize:

- Responsive controls
- Fast UI
- Clear feedback
- Smooth animations
- Good sound effects
- Impactful attacks
- Clear rewards
- Minimal unnecessary waiting
- Consistent visual language
- Intuitive navigation
- No confusing menus
- No unnecessary loading screens
- No repetitive clicking

A smaller game that feels extremely polished is preferable to a massive game that feels unfinished.

The first 10 minutes should feel like a professionally designed game, not a prototype.

**56\. SIGNATURE GAMEPLAY MECHANIC**

The game should have at least **one major gameplay mechanic that makes it immediately recognizable as its own game.**

It should not simply be:

Roblox + RPG + PvP

or

Roblox + dungeon crawler.

The game needs a recognizable identity.

Possible direction:

**Combat Mastery**

Players should become better at their chosen fighting style through actual gameplay.

For example:

- Perfect blocks
- Perfect dodges
- Attack chains
- Counter attacks
- Ability combinations
- Weapon-specific techniques
- Executions
- Parries
- Stagger mechanics
- Air attacks
- Charged attacks
- Environmental interactions

The goal is:

**A highly skilled player with mediocre equipment should still be dangerous.**

Equipment should make the player stronger, but **player skill should matter significantly in combat.**

This prevents the game from becoming a simple:

Bigger number = automatic winner.

**57\. COMBAT FEEL**

Combat should receive extremely high development priority.

Every attack should have:

- Startup animation
- Attack animation
- Hit detection
- Hit reaction
- Impact sound
- Visual impact effect
- Damage number
- Knockback/stagger where appropriate
- Recovery time
- Cooldown where appropriate

Weapons should feel different.

A sword should not simply be:

Sword = different mesh

A greatsword could have:

- Slower attacks
- Larger hitbox
- Higher damage
- Stronger stagger

Daggers:

- Extremely fast
- Short range
- High mobility
- Backstab potential

Hammer:

- Slow
- Extremely powerful
- Armor breaking
- Large stagger

Spear:

- Long range
- Precise attacks
- Strong defensive spacing

etc.

**Weapons should change how the player plays.**

**58\. COMBAT CAMERA SYSTEM**

The camera should be treated as part of combat.

Include:

- Soft camera tracking
- Target lock where appropriate
- Camera shake
- Impact camera effects
- Smooth transitions
- Adjustable camera sensitivity
- Mobile-friendly controls
- Controller support
- No excessive camera movement
- No camera clipping through walls

Camera effects should be subtle enough that they do not become annoying.

**59\. HIT FEEDBACK SYSTEM**

Players should immediately understand what happened.

Different events should have visually and audibly different feedback.

Examples:

**Normal hit**

- Small impact
- Normal sound
- Normal damage number

**Critical hit**

- Larger impact
- Distinct sound
- Larger damage number
- Brief visual effect

**Perfect block**

- Strong metallic impact
- Flash
- Unique sound
- Brief slow-motion or impact effect

**Perfect dodge**

- Distinct effect
- Short audio cue
- Optional brief time dilation

**Boss stagger**

- Major visual/audio cue
- Boss-specific animation

Players should never wonder:

"Did that actually hit?"

**60\. PLAYER FLOW**

Every major action should follow an intuitive flow.

Example:

**Lobby**

→ Choose activity

→ Matchmaking/loading

→ Fight

→ Victory/defeat

→ Rewards

→ Equipment screen

→ Equip new item

→ Character visually changes

→ Return to lobby

→ See other players

→ Decide what to pursue next

The player should always know:

1. What am I doing?
2. Why am I doing it?
3. What will I get?
4. What can I do next?

**61\. FIRST 15 MINUTES**

The first-time player experience should be deliberately designed.

The player should quickly:

1. Spawn into the lobby
2. See impressive players/equipment
3. Receive a short tutorial
4. Obtain their first weapon
5. Fight an enemy
6. Level up
7. Receive their first equipment drop
8. Equip it
9. See their character change
10. Discover another activity
11. See a high-level player with impressive equipment
12. Understand how to obtain something they want

Do **not** force the player through a long tutorial.

The game should teach by letting them play.

**62\. INSPECTION SYSTEM**

This could become one of the strongest social features.

Players should be able to inspect another player.

Inspection should show:

- Character
- Level
- Class/build
- Equipped weapon
- Armor
- Titles
- Achievements
- PvP wins
- Bosses defeated
- Ranks
- Rare equipment
- Equipment source

Example:

**Blood Warlord**

Level 87  
143 PvP Wins  
27 Bosses Defeated  
Warlord Title

Blood Champion Armor  
Obtained: 50 PvP Wins

Dragonbone Greatsword  
Obtained: Ancient Dragon — 2% Drop

This creates:

**"How the hell did he get that?"**

That feeling is extremely valuable.

**63\. EQUIPMENT HISTORY**

Rare equipment should contain history.

For example:

**Dragonbone Greatsword**

Obtained by:

Kyle  
September 11, 2026  
Ancient Dragon  
2% Drop

Or:

First obtained by: Player123  
Current owner: Player456

Potentially even:

- Number of bosses killed using it
- Number of PvP victories
- Number of players who have obtained it
- Original owner

This makes rare items feel like **artifacts**, rather than disposable stat objects.

**64\. ITEM DISCOVERY SYSTEM**

Do not reveal everything immediately.

Players should discover:

- Hidden bosses
- Secret areas
- Unknown weapons
- Secret achievements
- Hidden titles
- Rare drops
- Secret quests
- Special combinations
- Easter eggs

The game should occasionally make players think:

"Wait... how do you get THAT?"

Some content should intentionally be mysterious.

**65\. COLLECTION SYSTEM**

Give players reasons to collect beyond raw power.

Examples:

**Weapon Collection**

```
12 / 87 discovered
```

**Armor Collection**

```
24 / 140 discovered
```

**Boss Collection**

```
8 / 25 defeated
```

**Achievement Collection**

```
63 / 200 completed
```

**Title Collection**

```
17 / 48 unlocked
```

**World Collection**

```
4 / 10 discovered
```

Completionists should always have another goal.

**66\. ITEM FAVORITES / LOCKING**

Inventory should support:

- Favorite
- Lock
- Compare
- Equip
- Unequip
- Sell
- Salvage
- Sort
- Filter
- Search

Locked items should never accidentally be sold.

**67\. SALVAGE / CRAFTING SYSTEM**

Eventually allow unwanted equipment to become useful.

Example:

**Salvage**

Common Sword → Iron Shards

Rare Sword → Rare Materials

Legendary Sword → Legendary Material

Materials can be used to:

- Upgrade equipment
- Craft equipment
- Re-roll certain attributes
- Create cosmetics
- Create enhancement materials

This prevents inventory from becoming a pile of useless items.

**68\. BAD-LUCK PROTECTION**

Rare drops should remain rare, but players should not feel completely hopeless.

Example:

A boss has a 2% drop chance.

Every unsuccessful kill could slightly increase a hidden **luck meter**.

Eventually:

"Your next 25 kills are guaranteed to award a boss-exclusive item."

This should be carefully designed so that rare items remain prestigious.

The player should feel:

"I might get lucky."

rather than:

"I'll probably never get this."

**69\. DAILY / WEEKLY OBJECTIVES**

Add lightweight objectives.

Examples:

**Daily**

- Defeat 25 enemies
- Complete 2 dungeons
- Win 1 PvP match
- Defeat a boss

**Weekly**

- Win 10 PvP matches
- Defeat 5 bosses
- Complete 10 dungeons
- Discover 3 locations

Rewards:

- XP
- Gold
- Materials
- Cosmetics
- Titles
- Tickets
- Limited rewards

Avoid making the game feel like a job.

**70\. LIVE EVENTS**

The game should be designed so new content can be added without rebuilding the entire game.

Examples:

**Dragon Invasion**

A dragon appears in the lobby/world for one week.

**Blood Moon**

PvE enemies become stronger and drop special equipment.

**Arena Tournament**

Players compete for a temporary title.

**Ancient Relic Event**

A secret item becomes discoverable.

Events should create reasons for players to return.

**71\. ROTATING CONTENT**

Not everything needs to be available constantly.

Potential rotating systems:

- Daily dungeon
- Weekly boss
- Rotating challenge
- PvP modifier
- Special world event
- Rare merchant
- Limited cosmetic shop

This gives the world a feeling that it is alive.

**72\. NPC PERSONALITY**

Important NPCs should have personality.

Avoid:

"Hello adventurer. Click button."

Instead, NPCs should have:

- Names
- Distinct personalities
- Short dialogue
- Opinions
- Reactions
- Small stories
- Visual identities

The blacksmith should feel different from the dungeon master.

**73\. WORLD STORY**

The story does not need to become a giant cinematic RPG.

Instead, build **environmental storytelling**.

Players should discover:

- Ancient ruins
- Broken weapons
- Statues
- Graveyards
- Forgotten kingdoms
- Boss arenas
- Hidden chambers
- NPC conversations
- Lore books

Players who care about lore can explore it.

Players who don't can simply fight.

**74\. UI DESIGN LANGUAGE**

Every interface should feel like it belongs to the same game.

Establish consistent rules for:

- Fonts
- Buttons
- Panels
- Borders
- Icons
- Rarity colors
- Animations
- Sounds
- Notifications
- Tooltips

The UI should feel like:

**one game**, not 15 different Roblox systems glued together.

**75\. UI ANIMATION**

UI should have subtle animation.

Examples:

Inventory:

Open → slide/fade

Item:

Hover → slight highlight

Rare item:

Inspect → special reveal animation

Legendary drop:

Screen notification → item reveal → sound → particles

Level up:

Character glow → level animation → reward

Avoid excessive animations that slow the player down.

**76\. REWARD PRESENTATION**

Rewards should feel exciting.

Do not simply display:

+50 Gold  
+100 XP

Major rewards should have a presentation.

Example:

**LEGENDARY ITEM DISCOVERED**

DRAGONBONE GREATSWORD

Then:

- 3D rotating model
- Rarity effect
- Item stats
- Source
- Special ability
- Equip button

Rare items should feel like events.

**77\. AUDIO IDENTITY**

The game should have its own audio identity.

Create different sound categories:

- Sword impacts
- Heavy impacts
- Blocks
- Dodges
- Critical hits
- Level ups
- Item discoveries
- Legendary drops
- Boss introductions
- Boss phases
- Victory
- Defeat
- Menu interactions

Important items should have recognizable audio.

Players should eventually hear:

**That sound**

and know someone just obtained something extremely rare.

**78\. LOADING & SERVER TRANSITIONS**

Hide technical limitations behind polished transitions.

Avoid:

"Teleporting..."  
"Loading..."  
blank screen.

Instead use:

- Artwork
- Lore
- Weapon tips
- Enemy information
- Boss information
- Short animations

Example:

**ANCIENT DRAGON**

"The Dragon's scales become vulnerable after its third attack."

This also teaches players while they wait.

**79\. RECONNECT / DISCONNECT PROTECTION**

If a player disconnects unexpectedly:

- Save frequently
- Preserve inventory
- Preserve rewards
- Preserve progression
- Prevent item duplication
- Prevent lost purchases
- Handle server transfers safely

Never allow:

"I got a legendary and then Roblox disconnected me and it disappeared."

**80\. ECONOMY HEALTH**

The economy should have:

**Currency Sources**

- Fighting
- Dungeons
- Bosses
- PvP
- Quests
- Achievements

**Currency Sinks**

- Crafting
- Upgrades
- Cosmetic purchases
- Reforging
- Repairs if appropriate
- Customization
- Housing/guild features later

The economy should continuously remove currency so inflation does not destroy its value.

**81\. NO POWER CREEP**

New updates should not simply make every new weapon:

2× stronger than the previous one.

Instead, new equipment should introduce:

- Different builds
- Different abilities
- Different playstyles
- New set bonuses
- New effects
- Different strengths/weaknesses

Older legendary equipment should remain relevant.

**82\. PLAYER CHOICE**

Avoid forcing every player into the same progression path.

A player might become:

**The Gladiator**

PvP specialist.

**The Dragon Slayer**

Boss/PvE specialist.

**The Collector**

Equipment completionist.

**The Explorer**

Secret-area specialist.

**The Blacksmith**

Crafting specialist.

**The Speedrunner**

Challenge specialist.

**The Fashion Warrior**

Cosmetics/appearance specialist.

The game should support different types of players.

**83\. PRESTIGE WITHOUT POWER**

This is especially important.

Some of the coolest things in the game should **not** necessarily make the player stronger.

Examples:

- Titles
- Auras
- Kill effects
- Victory animations
- Armor appearances
- Weapon effects
- Mounts
- Lobby statues
- Achievement displays
- Player banners
- Rare emotes

This gives players reasons to chase accomplishments without destroying PvP balance.

**84\. SOCIAL SHOWCASE AREAS**

Eventually add places specifically designed to show accomplishments.

Examples:

**Hall of Champions**

Top PvP players.

**Hall of Legends**

Players with rare achievements.

**Boss Trophy Room**

Players display boss trophies.

**Armory**

Display rare weapons.

**Achievement Hall**

Display completed achievements.

This turns accomplishments into physical objects in the game world.

**85\. PLAYER HOUSING — LATER**

Do **not** build this initially.

Eventually players could have:

- Small personal armory
- Weapon racks
- Armor stands
- Trophy displays
- Boss trophies
- Achievement banners
- Custom decorations

This gives all those rare items another purpose.

**86\. MOBILE / CONTROLLER / PC PARITY**

The game must be designed for:

- PC
- Mobile
- Xbox/controller
- Touchscreen

Combat cannot depend on six keyboard keys being available.

Controls should automatically adapt.

UI should dynamically scale.

**87\. ACCESSIBILITY**

Include:

- Adjustable UI scale
- Camera sensitivity
- Volume controls
- Music/effects sliders
- Screen shake toggle
- Damage-number toggle
- Color-friendly rarity indicators
- Reduced visual effects option

The game should remain playable without excessive visual effects.

**88\. PERFORMANCE BUDGET**

Every system should have a performance budget.

Especially:

- VFX
- Particles
- NPCs
- Bosses
- Physics
- UI
- Lighting
- Mesh complexity

Rare equipment should look impressive **without destroying performance when 20 players stand together in the lobby.**

**89\. DEBUG / DEVELOPER TOOLS**

This is something I would absolutely add because you're having Claude build this.

Create a developer/admin system capable of:

- Spawn item
- Spawn enemy
- Spawn boss
- Teleport
- Set level
- Give XP
- Give currency
- Reset player
- Test abilities
- Test drops
- Test equipment
- Test achievements
- Test PvP
- View player data
- View server errors
- Force events
- Test matchmaking

Developer tools should be restricted to authorized accounts.

This will make development **dramatically faster.**

**90\. AUTOMATED QA SYSTEM**

Claude should continuously test the game.

The development process should include automated checks for:

- Missing assets
- Broken references
- Invalid item IDs
- Duplicate item IDs
- Missing icons
- Missing rarity definitions
- Missing stats
- Invalid equipment slots
- Broken scripts
- Remote-event errors
- DataStore errors
- Duplicate rewards
- Impossible item values
- NPCs without animations
- Weapons without grips
- Armor without attachments
- Missing UI elements

The game should have a:

**Development Validation / QA System**

that can be run before publishing.

**91\. CONTENT DATABASE**

This is another **very important architecture requirement**.

Items should NOT be hardcoded throughout dozens of scripts.

Instead use centralized data.

For example:

```
ItemId
Name
Type
Rarity
Power
Defense
Speed
Source
DropChance
World
Boss
Abilities
SetId
VisualAsset
IconAsset
VFX
Lore
Tradeable
Salvageable
```

Then adding:

"Inferno Greatsword"

should primarily mean adding a new item definition rather than rewriting combat systems.

This is what will make the Asset Factory actually useful.

**92\. DATA-DRIVEN ENEMIES**

Enemies should similarly be data-driven.

Example:

```
EnemyId
Name
Health
Damage
Defense
MovementSpeed
AttackPatterns
Abilities
AIType
World
LootTable
XP
Gold
Model
Animations
```

Adding a new enemy should not require rewriting the enemy system.

**93\. DATA-DRIVEN BOSSES**

Same principle.

A boss definition should contain:

```
BossId
Name
Health
Phases
Attacks
Abilities
Arena
Music
Animations
LootTable
Achievements
Titles
VisualEffects
```

This allows the game to eventually have dozens of bosses without creating an architectural nightmare.

**94\. VERSIONED SAVE DATA**

Player data should be versioned.

Example:

```
DataVersion = 1
```

When the game changes its save structure:

```
DataVersion = 2
```

The game should automatically migrate old player data.

This is extremely important if the game becomes successful.

**95\. GRACEFUL FAILURE**

If something goes wrong, the player should receive a useful response.

Never leave the player staring at a broken UI.

Examples:

Instead of:

Error

Use:

"We couldn't load your inventory. Your saved data is safe. Please try again."

Instead of silently failing a reward:

"Reward processing failed. We've preserved your match result and will retry."

The game should fail safely.

**96\. THE MOST IMPORTANT ADDITION: THE "I WANT THAT" SYSTEM**

Every major piece of content should pass this test:

**If another player walks past me wearing this, do I immediately want to know how they got it?**

If the answer is no, the item may need a better design.

This applies to:

- Weapons
- Armor
- Boss drops
- Titles
- Auras
- Mounts
- Effects
- Achievements
- Rare cosmetics

The game should constantly create:

**"I want that."**

moments.

**97\. FINAL DESIGN PRINCIPLE**

The game should not attempt to win players through endless grinding alone.

It should create a constant chain of:

**SEE SOMETHING AMAZING**

↓

**WANT IT**

↓

**DISCOVER HOW TO GET IT**

↓

**FIGHT FOR IT**

↓

**EARN IT**

↓

**EQUIP IT**

↓

**BECOME VISIBLY DIFFERENT**

↓

**OTHER PLAYERS SEE IT**

↓

**THEY WANT IT**

↓

**REPEAT**

That is the foundation of the game's long-term social progression.

**One thing I'd add above almost everything else**

I would make **"visual progression" a first-class system**, not merely an outcome of the RPG system.

When a player goes from Level 1 → Level 20 → Level 50 → Level 100, I want somebody looking at that player in the lobby to be able to roughly understand:

**"That guy has been playing for a long time."**

Not because there's a giant LEVEL 100 floating over his head—but because of his **armor silhouette, weapon, aura, title, animations, trophies, effects, and overall presence.**

That could become the game's real identity:

**Your character is your résumé.**

And that ties almost everything we've designed together: combat, RPG progression, bosses, PvP, achievements, the Asset Factory, rare drops, the social lobby, monetization, and the "I want that" psychology.