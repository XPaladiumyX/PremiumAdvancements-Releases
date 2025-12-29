# 🌟 Premium Advancements - Documentation

[![Minecraft Version](https://img.shields.io/badge/Minecraft-1.21+-brightgreen.svg)](https://papermc.io/)
[![Java Version](https://img.shields.io/badge/Java-21-orange.svg)](https://adoptium.net/)

> **A powerful custom advancement system for Minecraft servers with progression tracking, rewards, and advanced conditions**

---

## 📋 Table of Contents

- [Installation](#-installation)
- [Quick Start](#-quick-start)
- [Creating Advancements](#-creating-advancements)
- [Trigger Types](#-trigger-types)
- [Advanced Features](#-advanced-features)
- [Configuration Files](#-configuration-files)
- [Commands & Permissions](#-commands--permissions)
- [Troubleshooting](#-troubleshooting)

---

## 📥 Installation

### Requirements

1. **Server:** Paper 1.21.4+ (or any Paper fork)
2. **Java:** Version 21 or higher
3. **Dependencies:**
   - [UltimateAdvancementAPI](https://www.spigotmc.org/resources/95585/) v2.7.1+ (Required)
   - [Vault](https://www.spigotmc.org/resources/34315/) (Optional, for money rewards)

### Installation Steps

1. Download and install UltimateAdvancementAPI
2. (Optional) Download and install Vault + an economy plugin
3. Download Premium Advancements
4. Place all plugins in your `plugins/` folder
5. Start your server
6. Configure advancements in `plugins/PremiumAdvancements/advancements.yml`
7. Restart the server to apply changes

---

## 🚀 Quick Start

### Opening the GUI

Use `/padv gui` to open the management interface where you can:
- View all custom advancements
- Create new advancements
- Edit existing advancements
- Delete advancements

### Your First Advancement

1. Open the GUI with `/padv gui`
2. Click "Create Advancement"
3. Set the **Title** and **Description**
4. Choose an **Icon** (any Minecraft material)
5. Select a **Trigger** (e.g., JOIN, BREAK_BLOCK, OBTAIN_ITEM)
6. Configure **Display Options** (position, frame type, notifications)
7. (Optional) Add **Rewards** or **Money**
8. Click "Save"
9. **Restart the server** for changes to take effect

---

## 🎯 Creating Advancements

### Basic Settings

| Setting | Description | Example |
|---------|-------------|---------|
| **Title** | Name of the advancement | "First Steps" |
| **Description** | What the player needs to do | "Join the server" |
| **Icon** | Material displayed in menu | DIAMOND |
| **Icon Custom Model Data** | For custom textures (ItemsAdder/Oraxen) | 1001 |
| **Trigger** | How it's unlocked | JOIN, BREAK_BLOCK, etc. |

### Display Options

- **Position (X/Y):** Where it appears in the advancement menu (press L)
- **Frame Type:**
  - `TASK` - Square frame (lime)
  - `GOAL` - Rounded frame (lime)
  - `CHALLENGE` - Star frame (purple)
- **Show Toast:** Popup notification when unlocked
- **Announce in Chat:** Broadcast to all players
- **Action Bar:** Show progress bar (for counter-based)

### Sound Options

- **Enabled:** Play sound on unlock
- **Type:** Sound name (e.g., `UI_TOAST_CHALLENGE_COMPLETE`)
- **Volume:** 0.0 to 1.0
- **Pitch:** 0.5 to 2.0

---

## ⚡ Trigger Types

### 1. JOIN
Triggered when a player joins the server.

```yaml
first_join:
  title: "Welcome!"
  description: "Join the server for the first time"
  icon: NETHER_STAR
  trigger: JOIN
```

### 2. BREAK_BLOCK
Triggered when breaking specific blocks (or any block).

```yaml
stone_breaker:
  title: "Stone Breaker"
  description: "Break 100 stone blocks"
  icon: STONE
  trigger: BREAK_BLOCK
  block: STONE        # Optional: specific block type
  amount: 100         # Number required
```

### 3. PLACE_BLOCK
Triggered when placing specific blocks (or any block).

```yaml
builder:
  title: "Builder"
  description: "Place 500 blocks"
  icon: BRICKS
  trigger: PLACE_BLOCK
  amount: 500
```

### 4. KILL
Triggered when killing entities.

```yaml
monster_slayer:
  title: "Monster Slayer"
  description: "Kill 50 mobs"
  icon: DIAMOND_SWORD
  trigger: KILL
  amount: 50
```

### 5. OBTAIN_ITEM ⭐ New in v1.2
Triggered when obtaining items (pickup, crafting, or from containers).

```yaml
diamond_hunter:
  title: "Diamond Hunter"
  description: "Obtain your first diamond"
  icon: DIAMOND
  trigger: OBTAIN_ITEM
  item: DIAMOND              # Required item type
  amount: 1                  # Number required
  customModelData: -1        # Optional: for ItemsAdder/Oraxen
```

**Important Notes:**
- Works with pickup, crafting, smelting, and container looting
- Supports Custom Model Data for custom items
- Checks player inventory on join for existing items
- Progress is saved across sessions

---

## 🔥 Advanced Features

### 1. Dependencies (Requirements) ⭐ New in v1.3

Make advancements unlock in order by requiring previous completions.

```yaml
advanced_miner:
  title: "Advanced Miner"
  description: "Break 500 stone blocks"
  icon: DIAMOND_PICKAXE
  trigger: BREAK_BLOCK
  block: STONE
  amount: 500
  requires:                  # Must complete these first
    - first_join
    - stone_breaker
```

**How it works:**
- Players must complete ALL required advancements first
- If not met, they receive a message explaining what's needed
- Perfect for creating progression chains

### 2. World Restrictions ⭐ New in v1.3

Limit advancements to specific worlds.

```yaml
nether_explorer:
  title: "Nether Explorer"
  description: "Obtain 16 netherrack"
  icon: NETHERRACK
  trigger: OBTAIN_ITEM
  item: NETHERRACK
  amount: 16
  conditions:
    worlds:                  # Only works in these worlds
      - world_nether
      - nether_custom
```

**How it works:**
- Only triggers in specified worlds
- Players entering allowed worlds get progress checked
- Empty list = works in all worlds

### 3. Permission Requirements ⭐ New in v1.3

Restrict advancements to players with specific permissions.

```yaml
vip_reward:
  title: "VIP Member"
  description: "Join as a VIP member"
  icon: GOLD_BLOCK
  trigger: JOIN
  conditions:
    permission: "premiumadvancements.vip"
```

**How it works:**
- Only players with the permission can unlock it
- Others won't trigger it (no error message)
- Perfect for rank-based rewards

### 4. Custom Icons (ItemsAdder/Oraxen) ⭐ Enhanced in v1.3

Use custom textures for advancement icons.

```yaml
custom_sword:
  title: "Legendary Sword"
  description: "Obtain the legendary sword"
  icon: DIAMOND_SWORD
  iconCustomModelData: 1001  # Custom texture for icon
  trigger: OBTAIN_ITEM
  item: DIAMOND_SWORD
  customModelData: 1001      # Match custom item
```

**Two Custom Model Data fields:**
- `iconCustomModelData` - For the advancement icon (visual only)
- `customModelData` - For matching the actual item (OBTAIN_ITEM trigger)

### 5. Rewards System

#### Command Rewards
Execute console commands when unlocked:

```yaml
rewards:
  - "give %player% diamond 5"
  - "say %player% completed an achievement!"
```

#### Money Rewards (Requires Vault)
Give economy money:

```yaml
money:
  enabled: true
  amount: 1000.0
```

---

## ⚙️ Configuration Files

### config.yml

```yaml
# Language: en (English) or fr (French)
language: 'en'

# Database
database:
  type: 'sqlite'           # or 'mysql'/'mariadb'
  # MySQL settings (if type is mysql):
  host: 'localhost'
  port: 3306
  database: 'premiumadvancements'
  username: 'root'
  password: ''

# Progression
progression:
  show-actionbar: true     # Global action bar toggle

# Metrics
metrics:
  enabled: true            # bStats statistics
```

### advancements.yml

All your custom advancements are stored here. Edit via GUI or manually.

**Structure:**
```yaml
advancements:
  advancement_id:
    title: "Title"
    description: "Description"
    icon: MATERIAL_NAME
    iconCustomModelData: -1        # -1 = disabled
    trigger: TRIGGER_TYPE
    # Trigger-specific options
    amount: 1
    # Display options
    display:
      x: 1.0
      y: 0.0
      frame: TASK
      showToast: true
      announceChat: false
      showActionBar: true
    # Sound options
    sound:
      enabled: true
      type: UI_TOAST_CHALLENGE_COMPLETE
      volume: 1.0
      pitch: 1.0
    # Rewards
    hasReward: true
    rewards:
      - "command here"
    money:
      enabled: false
      amount: 0.0
    # Advanced conditions (v1.3)
    requires:
      - other_advancement_id
    conditions:
      worlds:
        - world_name
      permission: "permission.node"
```

### adv-gui.yml

Controls the advancement tab appearance (press L in-game):

```yaml
tab:
  namespace: "premium_advancements"

root:
  icon: "NETHER_STAR"
  title: "Premium Advancements"
  description: "Custom server advancements"
  background: "textures/block/gold_block.png"
```

---

## 🎮 Commands & Permissions

### Commands

| Command | Description | Permission |
|---------|-------------|------------|
| `/padv` | Show help menu | - |
| `/padv gui` | Open management GUI | `premiumadvancements.admin` |
| `/padv reset <player> <adv\|all>` | Reset player progress | `premiumadvancements.reset` |
| `/padv reload` | Reload configuration | `premiumadvancements.admin` |

**Aliases:** `/premiumadvancements`, `/padv`

### Permissions

| Permission | Description | Default |
|------------|-------------|---------|
| `premiumadvancements.admin` | Access GUI and admin commands | OP |
| `premiumadvancements.reset` | Reset player advancements | OP |

---

## 🔧 Troubleshooting

### Advancements don't appear in-game

**Solution:** You must **restart the server** (not just reload) after creating/editing advancements.

### Players can't see custom advancements

1. Check that UltimateAdvancementAPI is installed and running
2. Verify `adv-gui.yml` is properly configured
3. Make sure players have unlocked the root advancement (automatic on join)
4. Restart the server

### OBTAIN_ITEM not triggering

1. Verify the item material name is correct (e.g., `DIAMOND`, not `diamond`)
2. If using Custom Model Data, ensure it matches exactly
3. Check world restrictions - advancement may not work in current world
4. Check permission requirements - player may lack required permission
5. Check dependencies - player may need to complete other advancements first

### Action bar not showing

1. Check `config.yml` → `progression.show-actionbar: true`
2. Verify advancement has `showActionBar: true` in display options
3. Some advancements (JOIN, KILL without counter) don't use action bar

### Rewards not working

1. **Commands:** Verify syntax (no `/` prefix, use `%player%` placeholder)
2. **Money:** Install Vault + an economy plugin (EssentialsX, etc.)
3. Check console for error messages

### Database connection fails (MySQL)

1. Verify MySQL server is running
2. Check credentials in `config.yml`
3. Ensure database exists: `CREATE DATABASE premiumadvancements;`
4. Check firewall allows connection on port 3306

### Dependencies not working

1. Verify required advancement IDs exist and are spelled correctly
2. Check that players have actually completed the required advancements
3. Use `/padv reset <player> <advancement>` to test progression

---

## 📊 Database Options

### SQLite (Default)
- **Best for:** Small servers (<50 players)
- **Pros:** No setup required, automatic
- **Cons:** Slower with many players
- **Location:** `plugins/PremiumAdvancements/data.db`

### MySQL/MariaDB (Recommended)
- **Best for:** Medium-large servers (50+ players), networks
- **Pros:** Better performance, network support
- **Cons:** Requires external database
- **Setup:** Configure in `config.yml`, then restart

---

## 🌐 Multi-Language Support

### Available Languages
- **English** (en.yml) - Default
- **French** (fr.yml)

### Creating Custom Languages

1. Go to `plugins/PremiumAdvancements/languages/`
2. Copy `en.yml` as a template
3. Rename to your language code (e.g., `es.yml`)
4. Translate all messages
5. Set `language: 'es'` in `config.yml`
6. Reload: `/padv reload`

---

## 💡 Tips & Best Practices

1. **Always restart the server** after creating/editing advancements
2. Use **dependencies** to create logical progression chains
3. Use **world restrictions** for dimension-specific achievements
4. Use **Custom Model Data** for ItemsAdder/Oraxen integration
5. Test advancements in creative mode first
6. Use `/padv reset` to test player progression
7. For production servers, use **MySQL instead of SQLite**
8. Keep advancement IDs short and descriptive (e.g., `first_join`, `stone_breaker`)

---

## 🆘 Support

Need help? Join our community:

- **Discord:** [discord.gg/pTErYjTh5h](https://discord.gg/pTErYjTh5h)
- **Website:** [skyxnetwork.net](https://skyxnetwork.net)
- **GitHub Issues:** [Report bugs & request features](https://github.com/XPaladiumyX/PremiumAdvancements-Releases/issues)

---

**Made with ❤️ by Sky X Network**
