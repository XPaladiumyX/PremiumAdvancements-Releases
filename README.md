# 🌟 Premium Advancements

[![Minecraft Version](https://img.shields.io/badge/Minecraft-1.21+-brightgreen.svg)](https://papermc.io/)
[![Java Version](https://img.shields.io/badge/Java-21-orange.svg)](https://adoptium.net/)
[![bStats](https://img.shields.io/badge/bStats-Enabled-blue.svg)](https://bstats.org/)

> **A powerful and feature-rich custom advancement system for Minecraft servers**

Create fully customizable advancements with a user-friendly GUI, complete progression tracking, rewards system, and
extensive configuration options!

---

## 📖 Table of Contents

- [Features](#-features)
- [Requirements](#-requirements)
- [Installation](#-installation)
- [Configuration](#-configuration)
- [Usage](#-usage)
- [Permissions](#-permissions)
- [Commands](#-commands)
- [API Integration](#-api-integration)
- [Database Support](#-database-support)
- [Credits](#-credits)
- [Support](#-support)
- [License](#-license)

---

## ✨ Features

### 🎯 Core Features

- **✅ Fully Custom Advancements** - Create unlimited custom advancements with unique triggers
- **🖼️ Visual GUI Editor** - Easy-to-use in-game interface for managing advancements
- **📊 Progress Tracking** - Track player progression with counter-based advancements
- **🎁 Reward System** - Execute commands and give money rewards upon completion
- **🔊 Sound Effects** - Play custom sounds when players unlock advancements
- **💬 Action Bar Progress** - Show real-time progression in the action bar (configurable)
- **🗄️ Database Support** - Choose between SQLite (easy) or MySQL/MariaDB (production)

### 🎨 Display Customization

- **Position Control** - Place advancements anywhere in the GUI (X/Y coordinates)
- **Frame Types** - Choose between TASK, GOAL, or CHALLENGE frames
- **Toast Notifications** - Enable/disable popup notifications
- **Chat Announcements** - Announce unlocks to all players or keep them private
- **Custom Icons** - Use any Minecraft material as the advancement icon
- **Background Themes** - Customize the advancement tab background texture

### 🔧 Advanced Features

- **Multiple Trigger Types:**
    - `JOIN` - Triggered when player joins the server
    - `BREAK_BLOCK` - Triggered when breaking specific blocks
    - `PLACE_BLOCK` - Triggered when placing specific blocks
    - `KILL` - Triggered when killing entities
    - `OBTAIN_ITEM` - Triggered when obtaining specifics items

- **Counter System:**
    - Set required amounts (e.g., "Break 100 stone blocks")
    - Real-time progress display in action bar
    - Persistent progression across sessions

- **Reward System:**
    - Execute multiple console commands
    - Give money via Vault integration
    - Placeholder support (`%player%`)

- **Admin Tools:**
    - Reset individual player advancements
    - Reset all advancements for a player
    - Real-time config reload

---

## 📋 Requirements

### Essential

- **Minecraft Server:** Paper 1.21.4+ (or any Paper fork)
- **Java:** 21 or higher
- **Required Plugin:** [UltimateAdvancementAPI](https://www.spigotmc.org/resources/95585/) v2.7.1+

### Optional

- **Vault** - For economy/money rewards (recommended)
- **MySQL/MariaDB** - For better performance on larger servers

---

## 📥 Installation

1. **Download Requirements:**
    - Download [UltimateAdvancementAPI](https://www.spigotmc.org/resources/95585/)
    - Download [Vault](https://www.spigotmc.org/resources/34315/) (optional, for money rewards)
    - Download **Premium Advancements** (this plugin)

2. **Install Plugins:**
   ```
   server/
   └── plugins/
       ├── UltimateAdvancementAPI.jar
       ├── Vault.jar (optional)
       └── PremiumAdvancements.jar
   ```

3. **Start Server:**
    - Start your server to generate default configuration files
    - The plugin will automatically create:
        - `config.yml` - Main configuration
        - `advancements.yml` - Custom advancements storage
        - `adv-gui.yml` - GUI appearance settings
        - `data.db` - SQLite database (if using SQLite)

4. **Configure:**
    - Edit configuration files to your liking
    - Restart the server for changes to take effect

---

## ⚙️ Configuration

### `config.yml`

```yaml
# Database Configuration
database:
  type: 'sqlite'  # or 'mysql'/'mariadb'
  host: 'localhost'
  port: 3306
  database: 'premiumadvancements'
  username: 'root'
  password: ''

# Progression Display
progression:
  show-actionbar: true  # Global action bar toggle

# Metrics
metrics:
  enabled: true  # bStats metrics
```

### `advancements.yml`

```yaml
advancements:
  example_advancement:
    title: "Achievement Title"
    description: "Achievement description"
    icon: DIAMOND
    trigger: BREAK_BLOCK
    block: STONE
    amount: 10
    hasReward: true
    rewards:
      - "give %player% diamond 5"

    # Display options
    display:
      x: 1.0
      y: 0.0
      frame: TASK  # TASK, GOAL, or CHALLENGE
      showToast: true
      announceChat: false
      showActionBar: true  # Override global setting

    # Sound options
    sound:
      enabled: true
      type: UI_TOAST_CHALLENGE_COMPLETE
      volume: 1.0
      pitch: 1.0

    # Money reward (requires Vault)
    money:
      enabled: false
      amount: 100.0
```

### `adv-gui.yml`

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

## 🎮 Usage

### For Administrators

#### Opening the GUI

```
/padv gui
```

- Access the main management interface
- View all created advancements
- Create, edit, or delete advancements

#### Creating an Advancement

1. Open the GUI with `/padv gui`
2. Click the "Create Advancement" button
3. Fill in the details:
    - **Title** - The advancement name
    - **Description** - What it's about
    - **Icon** - Visual representation
    - **Trigger** - How it's unlocked
    - **Display Options** - Position, frame type, notifications
    - **Sound Options** - Sound effect settings
    - **Rewards** - Commands and money rewards

4. Click "Save" to create

#### Resetting Progress

```
/padv reset <player> <advancement_id>
/padv reset <player> all
```

### For Players

- Press **L** in-game to open the advancements menu
- View your custom advancement tab
- Track your progression
- Unlock advancements by completing their requirements

---

## 🔐 Permissions

| Permission                  | Description                      | Default |
|-----------------------------|----------------------------------|---------|
| `premiumadvancements.admin` | Access to GUI and admin commands | OP      |
| `premiumadvancements.reset` | Reset player advancements        | OP      |

---

## 📜 Commands

| Command                           | Description           | Permission                  |
|-----------------------------------|-----------------------|-----------------------------|
| `/padv`                           | Show help menu        | -                           |
| `/padv help`                      | Show help menu        | -                           |
| `/padv gui`                       | Open management GUI   | `premiumadvancements.admin` |
| `/padv reset <player> <adv\|all>` | Reset player progress | `premiumadvancements.reset` |
| `/padv reload`                    | Reload configuration  | `premiumadvancements.admin` |

**Aliases:** `/premiumadvancements`, `/padv`

---

## 🔌 API Integration

### UltimateAdvancementAPI

This plugin is built on top of [UltimateAdvancementAPI](https://github.com/frengor/UltimateAdvancementAPI) by frengor.

- Handles the core advancement system
- Manages player data persistence
- Provides the advancement GUI framework

### Vault (Optional)

When Vault is installed, you can:

- Give money rewards for completing advancements
- Use any economy plugin compatible with Vault
- Configure money amounts per advancement

### bStats

Anonymous usage statistics are collected via bStats to help improve the plugin.

- **Completely anonymous** - No personal data collected
- **Opt-out available** - Set `metrics.enabled: false` in config.yml
- **View statistics:** [bStats Page](https://bstats.org/)

---

## 🗄️ Database Support

### SQLite (Default)

**Best for:** Small servers (<50 players)

**Pros:**

- No setup required
- Automatic file creation
- Easy to backup

**Cons:**

- Slower with many players
- Not suitable for networks

### MySQL/MariaDB (Recommended)

**Best for:** Medium to large servers (50+ players) or networks

**Pros:**

- Better performance
- Network support (BungeeCord/Velocity)
- Concurrent access handling
- Professional-grade reliability

**Cons:**

- Requires external database server
- Additional setup needed

**Setup:**

1. Create a MySQL/MariaDB database
2. Update `config.yml`:
   ```yaml
   database:
     type: 'mysql'
     host: 'localhost'
     port: 3306
     database: 'premiumadvancements'
     username: 'your_username'
     password: 'your_password'
   ```
3. Restart the server

---

## 🙏 Credits

### Plugin Author

- **XPaladiumyX** - Lead Developer
- **Sky X Network** - Development Team

### Dependencies & APIs

- **[UltimateAdvancementAPI](https://github.com/frengor/UltimateAdvancementAPI)** by frengor
    - Core advancement system
    - Version: 2.7.1+

- **[PaperMC](https://papermc.io/)**
    - Minecraft server software
    - Version: 1.21.4

- **[Vault](https://github.com/MilkBowl/VaultAPI)** by **MilkBowl** (Optional)
    - Economy API integration
    - Version: 1.7+

- **[HikariCP](https://github.com/brettwooldridge/HikariCP)** by **brettwooldridge**
    - High-performance connection pooling
    - Version: 5.1.0

- **[bStats](https://bstats.org/)** by **Bastian Oppermann**
    - Plugin metrics
    - Version: 3.1.0

### Special Thanks

- **frengor** for creating UltimateAdvancementAPI
- The **PaperMC** team for their excellent server software
- The **Minecraft** modding community
- All users and testers who provided feedback

---

## 💬 Support

### Need Help?

- **Discord:** [Join our Discord](https://discord.gg/pTErYjTh5h)
- **Website:** [skyxnetwork.net](https://skyxnetwork.net)
- **Issues:** [GitHub Issues](https://github.com/XPaladiumyX/PremiumAdvancements/issues)

### Reporting Bugs

When reporting bugs, please include:

1. Server version (Paper/Spigot/etc.)
2. Plugin version
3. UltimateAdvancementAPI version
4. Console error logs (if any)
5. Steps to reproduce

### Feature Requests

We love hearing your ideas! Open a GitHub issue with the `enhancement` label.

---

## 📊 Statistics

This plugin uses **bStats** to collect anonymous usage statistics.

**What is collected:**

- Server version
- Plugin version
- Number of players
- Server location (country)
- Java version
- Database type used

**What is NOT collected:**

- Player names
- Server IP
- Server name
- Any personal data

You can opt-out by setting `metrics.enabled: false` in `config.yml`.

View our statistics: https://bstats.org/plugin/bukkit/PremiumAdvancements

---

## 📄 License

This project is licensed under the **Sky X Network License** - see the LICENSE file for details.

```
Proprietary License

Copyright (c) 2025-2026 Sky X Network. All rights reserved.

Terms and Conditions
1. Grant of License
This software ("Premium Advancements") is provided free of charge for use, but the source code remains proprietary and confidential. By using this software, you agree to the following terms:

2. Permitted Use
You are permitted to:
- Use the compiled plugin (JAR file) on your Minecraft server(s) free of charge
- Download and install the plugin from official sources
- Configure the plugin according to the provided documentation

3....
```

---

## 🌟 Star History

If you find this plugin useful, please consider giving it a ⭐ on GitHub!

---

## 📝 Changelog

### Version 1.1-SNAPSHOT

- ✨ Initial release
- ✅ Custom advancement creation via GUI
- 🗄️ SQLite and MySQL support
- 🎁 Command-based rewards
- 💰 Vault money rewards
- 🔊 Custom sound effects
- 📊 Action bar progression display
- 📈 bStats integration
- 🎨 Full display customization

---

<div align="center">

**Made with ❤️ by Sky X Network**

[Website](https://skyxnetwork.net) • [Discord](https://discord.gg/pTErYjTh5h) • [Donate](https://www.paypal.me/skyxnetwork)


</div>



