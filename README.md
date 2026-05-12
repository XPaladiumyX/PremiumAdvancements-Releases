<div align="center">

# Premium Advancements

**A powerful custom advancement system with an intuitive GUI editor, 43+ trigger types, progression tracking, and rewards.**

[![Minecraft](https://img.shields.io/badge/Minecraft-1.21+-brightgreen)](https://papermc.io)
[![Java](https://img.shields.io/badge/Java-21-orange)](https://adoptium.net)
[![Version](https://img.shields.io/badge/version-1.50-blue)]()

[Features](#-key-features) • [Triggers](#-trigger-types) • [Installation](#-installation) • [Quick Start](#-quick-start) • [Commands](#-commands--permissions)

---

</div>

## Overview

Premium Advancements lets you create **unlimited custom advancements** with a full in-game GUI editor — no need to edit configuration files manually. Track player progression in real-time, reward completions with commands or economy money, and chain advancements together for progression systems.

Works with **ItemsAdder/Oraxen** custom items, supports **SQLite and MySQL**, and integrates with **PlaceholderAPI** and **Vault**.

---

## Key Features

| Category | Features |
|----------|----------|
| **GUI Editor** | Create, edit, and delete advancements entirely in-game via `/padv gui` |
| **43+ Triggers** | From basic (JOIN, BREAK_BLOCK) to advanced (GLIDE, RAID_WIN, TRADE, SLEEP) |
| **Progression** | Counter-based tracking with persistent cross-session progress |
| **Rewards** | Console commands + Vault economy money on completion |
| **Notifications** | Toast popups, chat announcements, action bar progress |
| **Dependencies** | Chain advancements — require completions before unlocking |
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
| `JOIN` | Player joins the server | — |
| `KILL` | Kill any entity | Entity type |
| `BREAK_BLOCK` | Break blocks | Block type, world cooldown |
| `PLACE_BLOCK` | Place blocks | Block type, world cooldown |
| `OBTAIN_ITEM` | Obtain items (pickup, chests, crafting) | Item type, Custom Model Data |
| `CRAFT_ITEM` | Craft items | Item type, Custom Model Data |
| `SMELT_ITEM` | Smelt in furnace/blast furnace/smoker | Item type |
| `DROP_ITEM` | Drop items | Item type, Custom Model Data |

### Interaction

| Trigger | Description | Configurable Filters |
|---------|-------------|---------------------|
| `ANVIL_USE` | Use an anvil | — |
| `GRINDSTONE_USE` | Use a grindstone | — |
| `ENCHANT_ITEM` | Enchant at an enchantment table | Item type |
| `ENCHANT` | Enchant with specific enchantment | Enchantment type, minimum level |
| `COMPOSTER_USE` | Use a composter | — |
| `ARMOR_EQUIP` | Equip armor pieces | Armor type, Custom Model Data |
| `FILL_BUCKET` | Fill a bucket | Item type, Custom Model Data |
| `EMPTY_BUCKET` | Empty a bucket | Item type, Custom Model Data |

### Exploration & Movement

| Trigger | Description | Configurable Filters |
|---------|-------------|---------------------|
| `ENTER_DIMENSION` | Enter a dimension | NORMAL, NETHER, or THE_END |
| `TRAVEL_DISTANCE` | Travel a distance | Mode: TOTAL, WALKING, or BOAT |
| `JUMP` | Jump | — |
| `GLIDE` | Fly with elytra | — |
| `SWIM` | Swim in water | — |
| `CLIMB` | Climb ladders/vines | — |
| `RIPTIDE` | Use riptide trident | — |

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
| `DAMAGE_DEALT` | Deal damage | — |
| `DAMAGE_TAKEN` | Take damage | — |
| `RAID_WIN` | Win a raid | — |
| `TARGET_BLOCK` | Hit a target block | — |
| `BELL_RING` | Ring a bell | — |
| `CROSSBOW_SHOT` | Shoot a crossbow | — |
| `FIREWORK` | Launch fireworks | — |
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

---

## Installation

1. **Install Paper 1.21.4+** (or a Paper fork like Purpur)
2. **Download** [UltimateAdvancementAPI](https://www.spigotmc.org/resources/95585/) v2.7.1+ (required)
3. *(Optional)* **Download** [Vault](https://www.spigotmc.org/resources/34315/) + an economy plugin for money rewards
4. **Place** PremiumAdvancements.jar and all dependencies in your `plugins/` folder
5. **Restart** your server
6. Run **`/padv gui`** to start creating advancements

---

## Quick Start

1. **`/padv gui`** — Open the management GUI
2. Click **"Create Advancement"**
3. Set a **title**, **description**, and **icon**
4. Choose a **trigger** (e.g., `JOIN`)
5. *(Optional)* Add **reward commands** or **money**
6. Click **"Save"**
7. **Restart** the server to see advancements in-game
8. Press **L** to open the advancement tab

> **Tip:** Use `/padv info <id>` to see advancement details and placeholder IDs.

---

## Commands & Permissions

| Command | Description | Permission |
|---------|-------------|------------|
| `/padv` | Show help menu | — |
| `/padv gui` | Open management GUI | `premiumadvancements.admin` |
| `/padv info <id>` | Show advancement details | `premiumadvancements.admin` |
| `/padv reload` | Reload configuration | `premiumadvancements.admin` |
| `/padv placeholders` | List all placeholders | `premiumadvancements.admin` |
| `/padv reset <player> <id\|all>` | Reset player progress | `premiumadvancements.reset` |

**Alias:** `/premiumadvancements`

| Permission | Default | Description |
|------------|---------|-------------|
| `premiumadvancements.admin` | OP | Access GUI and admin commands |
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
| MySQL/MariaDB | Optional | 5.7+ / 10.2+ |

---

## Configuration

All configuration files are generated on first start in `plugins/PremiumAdvancements/`:

- **`config.yml`** — Language, database, progression, metrics
- **`advancements.yml`** — All custom advancements (edit via GUI or manually)
- **`adv-gui.yml`** — Tab appearance (namespace, icon, background)
- **`languages/en.yml`** — English messages
- **`languages/fr.yml`** — French messages

---

## Support

- **Discord:** [discord.gg/pTErYjTh5h](https://discord.gg/pTErYjTh5h)
- **Website:** [skyxnetwork.net](https://skyxnetwork.net)
- **Issues:** [GitHub Issues](https://github.com/XPaladiumyX/PremiumAdvancements-Releases/issues)

---

<div align="center">Made by Sky X Network</div>
