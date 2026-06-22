<div align="center">

# Premium Advancements

**A powerful custom advancement system with an intuitive in-game and web GUI editor, 44+ trigger types, Discord webhooks, progression tracking, and 7 reward types.**

[![Minecraft](https://img.shields.io/badge/Minecraft-1.21+-brightgreen)](https://papermc.io)
[![Java](https://img.shields.io/badge/Java-21-orange)](https://adoptium.net)
[![Version](https://img.shields.io/badge/version-1.70-blue)](https://github.com/XPaladiumyX/PremiumAdvancements-Releases)

[Features](#-key-features) • [Triggers](#-trigger-types) • [Installation](#-installation) • [Quick Start](#-quick-start) • [Web Editor](#-web-editor) • [Commands](#-commands--permissions) • [Wiki](https://wiki.skyxnetwork.net/advancements/)

---

</div>

## Overview

Premium Advancements lets you create **unlimited custom advancements** with a full in-game GUI editor and a **browser-based web editor** - no need to edit configuration files manually. Track player progression in real-time, reward completions with commands, items, money, permissions, or Discord webhooks, and chain advancements together for progression systems.

Works with **ItemsAdder/Oraxen** custom items, supports **SQLite and MySQL**, and integrates with **PlaceholderAPI**, **Vault**, **LuckPerms**, and **PlayerPoints**.

---

## Key Features

| Category | Features |
|----------|----------|
| **GUI Editor** | Create, edit, and delete advancements entirely in-game via `/padv gui` |
| **Web Editor** | Browser-based editor with live tree view, drag & drop positioning, undo/redo, import/export JSON |
| **44+ Triggers** | From basic (JOIN, BREAK_BLOCK) to advanced (GLIDE, RAID_WIN, TRADE, SLEEP, CHOP_TREE) |
| **Progression** | Counter-based tracking with persistent cross-session progress |
| **Rewards** | Console commands + Vault money + custom items + LuckPerms permissions + PlayerPoints + weighted loot pools + global broadcast |
| **Discord Webhook** | Send customizable Discord embeds on advancement completion, per-advancement toggle |
| **Notifications** | Toast popups, chat announcements, action bar progress, server broadcasts |
| **Dependencies** | Chain advancements - require completions before unlocking |
| **Hidden Advancements** | Secret advancements that stay hidden until all requirements are met |
| **Connection System** | Visually link advancements into tree structures with `connection.target` |
| **Multi-Material** | Specify multiple blocks, items, or entities in a single advancement |
| **World Restrictions** | Limit advancements to specific worlds |
| **Permission Gates** | Require permissions to unlock advancements |
| **Custom Items** | ItemsAdder/Oraxen support via Custom Model Data |
| **Database** | SQLite (default) or MySQL/MariaDB with HikariCP pooling |
| **PlaceholderAPI** | 8 placeholders: completion count, progress, ranking, latest, etc. |
| **Sounds** | Customizable sound effects per advancement |
| **Languages** | English and French included, easily add more |
| **bStats** | Anonymous usage statistics (configurable) |

---

## Trigger Types

### Basic

| Trigger | Description | Configurable Filters |
|---------|-------------|---------------------|
| `JOIN` | Player joins the server | - |
| `KILL` | Kill any entity | Entity type |
| `BREAK_BLOCK` | Break blocks | Block type, world cooldown |
| `CHOP_TREE` | Break any log (oak, spruce, birch, etc.) | - |
| `PLACE_BLOCK` | Place blocks | Block type, world cooldown |
| `OBTAIN_ITEM` | Obtain items (pickup, chests, crafting) | Item type, Custom Model Data |
| `CRAFT_ITEM` | Craft items | Item type, Custom Model Data |
| `SMELT_ITEM` | Smelt in furnace/blast furnace/smoker | Item type |
| `DROP_ITEM` | Drop items | Item type, Custom Model Data |

### Interaction

| Trigger | Description | Configurable Filters |
|---------|-------------|---------------------|
| `ANVIL_USE` | Use an anvil | - |
| `GRINDSTONE_USE` | Use a grindstone | - |
| `ENCHANT_ITEM` | Enchant at an enchantment table | Item type |
| `ENCHANT` | Enchant with specific enchantment | Enchantment type, minimum level |
| `COMPOSTER_USE` | Use a composter | - |
| `ARMOR_EQUIP` | Equip armor pieces | Armor type, Custom Model Data |
| `FILL_BUCKET` | Fill a bucket | Item type, Custom Model Data |
| `EMPTY_BUCKET` | Empty a bucket | Item type, Custom Model Data |

### Exploration & Movement

| Trigger | Description | Configurable Filters |
|---------|-------------|---------------------|
| `ENTER_DIMENSION` | Enter a dimension | NORMAL, NETHER, or THE_END |
| `TRAVEL_DISTANCE` | Travel a distance | Mode: TOTAL, WALKING, or BOAT |
| `JUMP` | Jump | - |
| `GLIDE` | Fly with elytra | - |
| `SWIM` | Swim in water | - |
| `CLIMB` | Climb ladders/vines | - |
| `RIPTIDE` | Use riptide trident | - |

### Entity & Interaction

| Trigger | Description | Configurable Filters |
|---------|-------------|---------------------|
| `FISH` | Catch fish | Item type |
| `BREED` | Breed animals | Entity type |
| `TAME` | Tame animals | Entity type |
| `SHEAR` | Shear entities | Entity type, sheep color |
| `MILK` | Milk cows/mooshrooms | Entity type |
| `TRADE` | Trade with villagers | Villager profession |

### Items & Status

| Trigger | Description | Configurable Filters |
|---------|-------------|---------------------|
| `CONSUME` | Drink potions/milk/honey | Item type, Custom Model Data |
| `EAT` | Eat food | Item type, Custom Model Data |
| `POTION_EFFECT` | Get a potion effect | Effect type, minimum amplifier |

### Combat & Events

| Trigger | Description | Configurable Filters |
|---------|-------------|---------------------|
| `DEATH` | Die (deferred to respawn) | Cause: FALL, LAVA, PVP, MOB |
| `DAMAGE_DEALT` | Deal damage | - |
| `DAMAGE_TAKEN` | Take damage | - |
| `RAID_WIN` | Win a raid | - |
| `TARGET_BLOCK` | Hit a target block | - |
| `BELL_RING` | Ring a bell | - |
| `CROSSBOW_SHOT` | Shoot a crossbow | - |
| `FIREWORK` | Launch fireworks | - |
| `SNIFF` | Brush suspicious sand/gravel | Block type |
| `SLEEP` | Sleep in a bed | Bed color |

---

## Screenshots

![Main GUI](https://i.imgur.com/IQKb13E.png)
*Main management GUI with pagination*

![Create Advancement](https://i.imgur.com/14Vvobg.png)
*In-game advancement creation*

![Edit Advancement](https://i.imgur.com/GSNHBLs.png)
*Edit existing advancements*

![In-Game View](https://i.imgur.com/C43RdS9.png)
*Advancement tab visible by pressing L*

![Rewards](https://i.imgur.com/K5ly78M.png)
*Rewards and conditions configuration*

![Discord Webhook](https://i.imgur.com/H1kcSHg.png)
*Discord webhook embed with rewards summary*

![Web Editor](https://i.imgur.com/b63bL7g.png)
*Web editor: full advancement creation wizard*

![Web Editor Tree](https://i.imgur.com/ATvyMvn.png)
*Web editor: live tree view with drag & drop positioning*

---

## Installation

1. **Install Paper 1.21.4+** (or a Paper fork like Purpur)
2. **Download** [UltimateAdvancementAPI](https://www.spigotmc.org/resources/95585/) v2.7.1+ (required)
3. *(Optional)* **Download** [Vault](https://www.spigotmc.org/resources/34315/) + an economy plugin for money rewards
4. **Place** PremiumAdvancements.jar and all dependencies in your `plugins/` folder
5. **Restart** your server
6. Run **`/padv gui`** to start creating advancements
7. Run **`/padv reload`** to apply changes without restarting

---

## Quick Start

1. **`/padv gui`** - Open the management GUI
2. Click **"Create Advancement"**
3. Set a **title**, **description**, and **icon**
4. Choose a **trigger** (e.g., `JOIN`)
5. *(Optional)* Add **reward commands** or **money**
6. Click **"Save"**
7. Run **`/padv reload`** to see advancements in-game immediately
8. Press **L** to open the advancement tab

> **Tip:** Use `/padv info <id>` to see advancement details and placeholder IDs.

---

## Web Editor

Premium Advancements includes a **browser-based web editor** accessible via `/padv editor` in-game.

### Features

- **Live Tree View** - Visual advancement hierarchy with connection lines, zoom/pan
- **Drag & Drop Positioning** - Toggle move mode, click to pick up an advancement, move the mouse to position it, click again to drop
- **Undo/Redo** - Ctrl+Z / Ctrl+Y, or use the top-right buttons
- **Arrow Key Nudge** - Fine-tune with arrow keys (Shift for 1.0 step)
- **Full Creation & Edit Wizard** - 5 tabs (Basic, Trigger, Display, Rewards, Advanced) with dropdowns, icon browser, tag inputs
- **Search & Filter** - Filter advancements by name or ID
- **Import / Export JSON** - Save and load advancement presets

### How to Use

1. Run **`/padv editor`** in-game to get your editor link
2. Open the link in your browser
3. If prompted, run **`/padv editor-trust <code>`** to authorize your browser
4. Edit advancements visually and click **SAVE** to upload changes
5. Run **`/padv apply <token>`** in-game to apply saved changes

---

## Commands & Permissions

| Command | Description | Permission |
|---------|-------------|------------|
| `/padv` | Show help menu | - |
| `/padv gui` | Open in-game management GUI | `premiumadvancements.admin` |
| `/padv editor` | Get web editor link | `premiumadvancements.admin` |
| `/padv editor-trust <code>` | Authorize a browser session | `premiumadvancements.admin` |
| `/padv info <id>` | Show advancement details | `premiumadvancements.admin` |
| `/padv give <player> <advancement>` | Grant an advancement | `premiumadvancements.give` |
| `/padv take <player> <advancement\|all>` | Revoke an advancement | `premiumadvancements.take` |
| `/padv list [player]` | List completed advancements | `premiumadvancements.list` (own) / `premiumadvancements.list.others` |
| `/padv stats [player]` | Open stats GUI | `premiumadvancements.stats` (own) / `premiumadvancements.stats.others` |
| `/padv reset <player> <id\|all>` | Reset player progress | `premiumadvancements.reset` |
| `/padv reload` | Reload configuration | `premiumadvancements.admin` |
| `/padv placeholders` | List all placeholders | `premiumadvancements.admin` |

**Alias:** `/premiumadvancements`

| Permission | Default | Description |
|------------|---------|-------------|
| `premiumadvancements.admin` | OP | Access GUI and admin commands |
| `premiumadvancements.give` | OP | Grant advancements |
| `premiumadvancements.take` | OP | Revoke advancements |
| `premiumadvancements.list` | **true** | List own advancements |
| `premiumadvancements.list.others` | OP | List others' advancements |
| `premiumadvancements.stats` | **true** | View own stats |
| `premiumadvancements.stats.others` | OP | View others' stats |
| `premiumadvancements.reset` | OP | Reset player advancements |

### Placeholders

| Placeholder | Description |
|-------------|-------------|
| `%premiumadvancements_completed%` | Total completed advancements |
| `%premiumadvancements_total%` | Total available advancements |
| `%premiumadvancements_progress_<id>%` | Progress (e.g., 45/100) |
| `%premiumadvancements_completed_<id>%` | Completed status (true/false) |
| `%premiumadvancements_percent%` | Overall completion % |
| `%premiumadvancements_percent_<id>%` | Per-advancement progress % |
| `%premiumadvancements_latest%` | Latest completed title |
| `%premiumadvancements_ranking%` | Player rank by completions |

---

## Requirements

| Dependency | Type | Version |
|------------|------|---------|
| [Paper](https://papermc.io) (or fork) | Server | 1.21.4+ |
| Java | Runtime | 21+ |
| [UltimateAdvancementAPI](https://www.spigotmc.org/resources/95585/) | Required | 2.7.1+ |
| [Vault](https://www.spigotmc.org/resources/34315/) | Optional | Latest |
| [PlaceholderAPI](https://www.spigotmc.org/resources/6245/) | Optional | 2.11.6+ |
| [LuckPerms](https://luckperms.net/) | Optional | Latest |
| [PlayerPoints](https://www.spigotmc.org/resources/80749/) | Optional | Latest |
| MySQL/MariaDB | Optional | 5.7+ / 10.2+ |

---

## Configuration

All configuration files are generated on first start in `plugins/PremiumAdvancements/`:

- **`config.yml`** - Language, database, progression, metrics
- **`advancements.yml`** - All custom advancements (edit via GUI or manually)
- **`adv-gui.yml`** - Tab appearance (namespace, icon, background)
- **`languages/en.yml`** - English messages
- **`languages/fr.yml`** - French messages

---

## Support

- **Discord:** [discord.gg/pTErYjTh5h](https://discord.gg/pTErYjTh5h)
- **Wiki:** [wiki.skyxnetwork.net/advancements](https://wiki.skyxnetwork.net/advancements/)
- **Website:** [skyxnetwork.net](https://skyxnetwork.net)
- **Issues:** [GitHub Issues](https://github.com/XPaladiumyX/PremiumAdvancements-Releases/issues)

---

<div align="center">Made by Sky X Network</div>
