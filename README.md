<p align="center">
  <img src="https://img.shields.io/badge/version-3.92-blue?style=for-the-badge" alt="Version">
  <img src="https://img.shields.io/badge/license-permanent%20all--servers-success?style=for-the-badge" alt="License">
  <a href="https://discord.gg/YOUR_REAL_INVITE_CODE"><img src="https://img.shields.io/badge/support-24%2F7%20discord-5865F2?style=for-the-badge&logo=discord&logoColor=white" alt="Discord"></a>
  <a href="https://mc.hypeland.org"><img src="https://img.shields.io/badge/demo-mc.hypeland.org-orange?style=for-the-badge" alt="Demo Server"></a>
</p>

<h1 align="center">System</h1>

<p align="center"><strong>The last server management plugin you will ever need.</strong></p>

# System

**Production-grade server management for Minecraft 1.8.8 (Spigot / Paper).**
Engineered for networks that demand zero-downtime operations, modular architecture, and uncompromising stability.
A single JAR replaces dozens of lobby plugins — daily restart scheduling, backup management, world protection, a complete economy with MongoDB + Redis, 20 modular addons, 33 decorative animations, a built-in Vault service layer, and full PlaceholderAPI integration. Every system, every configuration value, and every optimisation exists because real server owners demanded it.

---

## Table of Contents

- [Test Server – Try Before You Buy](#test-server--try-before-you-buy)
- [Why System?](#why-system)
- [Competitive Comparison](#competitive-comparison)
- [Why Exclusively 1.8.8?](#why-exclusively-188)
- [Zero Hard Dependencies](#zero-hard-dependencies)
- [Core Features – Expanded](#core-features--expanded)
- [20 Modular Addons](#20-modular-addons)
- [Built-in Vault Service Layer](#built-in-vault-service-layer)
- [Economy – MongoDB + Redis](#economy--mongodb--redis)
- [33 Decorative Animations](#33-decorative-animations)
- [Commands & Permissions](#commands--permissions)
- [PlaceholderAPI Integration](#placeholderapi-integration)
- [Full Configuration](#full-configuration)
- [Storage Backends](#storage-backends)
- [Frequently Asked Questions](#frequently-asked-questions)
- [Support & Purchasing](#support--purchasing)

---

## Test Server – Try Before You Buy

A live, fully functional demo network is available so you can evaluate System before making any commitment.

```
IP: mc.hypeland.org
```

The test server runs the latest stable build with every addon enabled. You can experience the restart scheduler, economy, animations, world protection, chat emojis, and every other system exactly as your players would. **No registration, no whitelist — connect and play immediately.**

---

## Why System?

System is not a collection of loosely coupled plugins held together by third-party dependencies. It is a single, monolithic solution engineered from the ground up for networks that cannot afford downtime, version incompatibilities, or incomplete lobby management.

### The Only Plugin That Truly Replaces Everything
Every system you need — from restart scheduling and backup management, to world protection and chat filtering, to a complete economy with Vault integration, to 33 decorative animations and interactive books — lives inside **one JAR**. You never install extra plugins for permissions, chat formatting, economy, or lobby cosmetics. System ships with **20 modular addons** that share the same configuration system and can be enabled or disabled independently. When an addon is disabled, it consumes zero CPU.

### Zero Hard Dependencies
Starting from version 3.11, System has zero hard dependencies. Drop the JAR into `plugins/`, start the server, and the plugin loads. Vault, PlaceholderAPI, GroupManager, PermissionsEx, and Essentials are all optional. If an optional dependency is missing, the plugin still loads and runs — the features that require that dependency are disabled with a clear log message. Since v3.90, the Vault API classes ship inside the System JAR itself, so the economy, permission service layer, and emoji chat replacement all work on a completely vanilla plugin setup without any external JAR.

### Built-in Vault Means Zero External Plugins
System includes a native port of the essential Vault service functionality — Permission, Chat, and Economy services — built directly into the JAR. No external Vault plugin is required. System registers itself under the name `Vault` in the plugin manager lookup table, so every runtime `Bukkit.getPluginManager().getPlugin("Vault")` check performed by other plugins resolves to System. Plugins that declare `depend: [Vault]` in their `plugin.yml` still require the original Vault jar (a Bukkit limitation), but the vast majority of plugins that use Vault services work without any external Vault installation.

### Extreme Performance, Not an Afterthought
Performance is treated as a first-class feature. All database operations (MongoDB writes, Redis cache reads) run asynchronously. Animation updates pause automatically when no players are online. The scoreboard refreshes on a configurable interval only when data changes. The log watcher trims logs without blocking the main thread. The backup system compresses archives in the background. The result is a plugin that adds near-zero overhead to your server's tick loop.

### Modular Architecture for Any Topology
Every addon is a self-contained module with its own configuration file under `plugins/System/addons/<addon-name>/config.yml`. Disable what you don't need, enable what you do. A single boolean per addon in the main `config.yml` controls whether it loads. This makes System equally suited for a single lobby server and a 50-server BungeeCord network where each server enables only the addons it needs.

### Zero Recurring Costs, True Unlimited License
One payment grants you a permanent license that covers **all servers you own** — whether you run a single lobby or a 50-server BungeeCord network. There are no monthly fees, no per-server add-ons, and no hidden costs. You receive all future updates for the current major version free of charge.

### Direct Access to the Developer
When your server has an issue at peak time, you do not file a ticket and wait. You speak directly to the person who wrote the code. Support is available **24/7** through Discord or Bale, and every report is treated with the urgency that a live production network demands.

---

## Competitive Comparison

| Criteria | **System** | EssentialX + Vault + LuckPerms | Other "Premium" Lobby Plugins |
|----------|-----------|-------------------------------|------------------------------|
| **Built-in addons** | 20 modular addons (economy, vault, animations, chat emojis, world protection, etc.) | Requires 3-5 separate plugins | Usually 5-10, many paid separately |
| **Built-in Vault services** | Yes — Permission, Chat, and Economy registered natively | Requires external Vault | Rare |
| **Zero hard dependencies** | Yes — loads on vanilla Spigot 1.8.8 | Requires Vault, Essentials | Usually requires Vault + others |
| **Economy backend** | MongoDB + Redis (shaded, no external drivers) | Flat file / MySQL | Usually flat file or MySQL |
| **Animations** | 33 built-in types (block, particle, item, special) | Not available | Rare |
| **Chat emojis** | 39 default emojis, full PlaceholderAPI support | Not available | Rare |
| **Daily restart scheduler** | Fixed wall-clock time with configurable warnings | Not available (needs external) | Varies |
| **Backup management** | Boot, pre-shutdown, and manual with auto-pruning | Not available | Rare |
| **Server login lock** | Pre-restart, startup, and resource-threshold locking | Not available | Not available |
| **World protection** | Per-world with per-player build mode and door toggle | Needs WorldGuard | Varies |
| **Anti-swear filter** | 6,122-word list with command argument filtering | Not available | Basic |
| **AFK detection** | 4-stage countdown warnings with title and sound | Not available | Basic |
| **Interactive books** | Config-driven with placeholders, join behaviors, aliases | Not available | Rare |
| **ItemJoin** | Config-driven join items with protection flags | Separate plugin | Rare |
| **PlaceholderAPI** | Full `vault` expansion + built-in placeholders | Varies | Varies |
| **License model** | Permanent, all servers | Free (but needs many plugins) | Often per-server or recurring |

**Key takeaway:** System is the only option that replaces an entire lobby plugin stack — permissions, chat, economy, protection, cosmetics, and server management — in a single JAR with a single purchase that covers every server you run.

---

## Why Exclusively 1.8.8?

Targeting a single version is an intentional engineering choice that guarantees stability and maximum speed.

1. **Performance that newer versions cannot match.** The 1.8.8 server tick loop is leaner, the entity count is lower, and the block model is simpler. This allows System to employ precise block manipulation for the door toggle system, reflective ProtocolLib integration for the login lock, and version-specific event handling — all written directly against the 1.8.8 API.
2. **No compromises in version-specific integration.** The door toggle system uses hardcoded `EnumSet` lookups for 1.8 door, trapdoor, and fence gate materials. The animation system uses verified 1.8.8 sound enum names with legacy fallbacks. Supporting multiple versions would mean removing these precise, version-critical hooks.
3. **Stability through predictability.** One version means one test environment. Every feature is verified on clean 1.8.8 Spigot and Paper builds. There are no surprises from API changes or edge cases introduced by newer mechanics.
4. **The competitive PvP standard.** The largest networks built their foundations on 1.8.8. The combat mechanics, knockback calculations, and block-hitting behaviour that competitive players expect are tied to this version. System is built for the version those players demand.

If future versions are supported, they will be delivered as separate, equally optimised branches — never as a bloated, one-size-fits-all JAR.

---

## Zero Hard Dependencies

System starts without any external plugins. The dependency manager checks for optional dependencies at startup and logs clear messages about what is available and what is missing.

| Dependency | Required For | Behavior if Missing |
|-----------|-------------|-------------------|
| **Vault** | Nothing — the built-in Vault addon provides all services | Plugin loads normally. The built-in Vault addon handles everything. |
| **PlaceholderAPI** | Join messages, scoreboard, emoji value placeholders | Built-in placeholders used as fallback. PAPI-specific features skipped. |
| **GroupManager** | Higher priority Vault Permission and Chat providers | SystemPerms fallback answers through the Bukkit permission API. |
| **PermissionsEx** | Higher priority Vault Permission and Chat providers | Same fallback as GroupManager. |
| **Essentials** | Emoji parsing inside private messages | Emojis still parsed in chat, on signs, in books and anvil renames. |
| **MongoDB 4.0+** | Economy persistent storage | Economy addon fails to enable if configured but unreachable. |
| **Redis 5.0+** | Economy read-through cache | Economy operates without cache if configured but unreachable. |

---

## Core Features – Expanded

### Daily Restart Scheduler

The server restarts automatically once per day at a fixed wall-clock time. The schedule is driven entirely by a single daily scheduler — the legacy interval-based auto-restart logic has been removed to eliminate unannounced sudden restarts. The restart sequence broadcasts warnings at configurable minute and second thresholds, activates a pre-restart protocol that locks chest and ender chest access, and finally runs the configured restart commands (typically `save-all` followed by `stop`).

Key configuration:

- `restart-time` (HH:mm, default `04:00`) with configurable timezone.
- Warning thresholds at configurable minute and second intervals.
- Pre-restart protocol with server login lock.
- Manual restart via `/system restart` with configurable delay.

### Backup Management

The backup system produces compressed archives of configured folders (typically `world` and `plugins`). Backups are taken in three scenarios: automatically on server start (if the previous shutdown was longer than a configured threshold), before a scheduled daily restart, and manually via `/system backup`. Old backups beyond a configurable maximum are pruned automatically. The boot counter is persisted in an embedded H2 database that handles concurrent access gracefully.

### Server Login Lock

When the pre-restart protocol activates, the login lock prevents new players from joining. This guarantees no data duplication or inconsistent state during the final seconds before a restart. The login lock also activates during server startup and when CPU or memory usage exceeds configurable thresholds.

### Protocol Listener

Handles protocol-level events not exposed through the standard Bukkit API. Used to enforce pre-restart protocol restrictions (chest access, chat, inventory open) at a layer that bypasses most client-side workarounds.

### Spawn System

Configurable spawn points per world, stored in `spawn.yml`. The `SpawnRegionRegistry` tracks protected regions around spawn points where build and interact events are restricted. Set via `/system setspawn`.

### Door Toggle

Allows players to open doors, trapdoors, and fence gates in protected lobby worlds with automatic closure after a configurable delay. Uses a pre-toggle state detection approach that eliminates timing-related race conditions. Includes a dual-path write strategy with physics verification for reliable trapdoor closure even under redstone power. On chunk load, any open door-like blocks in configured worlds are force-closed. When a player disconnects, any doors they opened are closed immediately.

### Scoreboard Manager

A lightweight scoreboard rendered to every online player. Content is driven by `scoreboard.yml` and supports PlaceholderAPI placeholders when installed. Refreshes on a configurable interval to avoid unnecessary tick load.

### OP Listener & Log Watcher

The OP listener monitors operator state changes and can take configurable action when OP status is granted outside of explicit admin actions. The log watcher periodically inspects the server log and trims it when it grows beyond a configured size, while capturing `WARNING` and `SEVERE` records into a separate rotating file.

---

## 20 Modular Addons

All addons are self-contained, independently configurable, and toggled in the main `config.yml`. When disabled they consume zero performance.

| Addon | Function |
|-------|----------|
| **AntiCaps** | Detects and rewrites chat messages with excessive uppercase letters |
| **AntiSwear** | Filters bad words from chat (6,122-word list) and command arguments |
| **AntiAfk** | 4-stage countdown AFK detection with persistent title and sound |
| **ChatBlocker** | Filters chat messages by pattern and word list |
| **ChatEmojis** | 39 emoji shortcodes with color restore, sign/book/anvil support |
| **WorldProtection** | Per-world block placement/break protection with per-player build mode |
| **Economy** | Full economy with MongoDB + Redis, Vault integration, `/balance`, `/pay`, `/money` |
| **Vault** | Built-in Permission, Chat, and Economy service registration — replaces external Vault |
| **AutoFly** | Automatic flight enable on join with per-world exclusion |
| **DoubleJump** | Forward-and-upward double jump with per-player opt-in and cooldown |
| **Stairs** | Sit on stairs and slabs with real-time yaw tracking |
| **PotionEffect** | Configurable potion effects per world on enter/reside |
| **LobbyFireworks** | Configurable fireworks with cooldown and world blacklist |
| **JoinMessage** | Per-player custom join messages with PlaceholderAPI support |
| **Kaboom** | Launch players into the air with configurable velocity |
| **ItemJoin** | Config-driven custom join items with protection flags and triggers |
| **InteractiveBooks** | Config-driven books with placeholders, join behaviors, and aliases |
| **DoorToggle** | Auto-close doors, trapdoors, and fence gates in protected worlds |
| **Animations** | 33 decorative animation types with crash recovery |
| **Loggers** | Log size watcher and warning/error rotating file capture |

---

## Built-in Vault Service Layer

A native port of the essential Vault plugin functionality — no commands, no configuration folder, no update checker. The Vault addon registers the `Permission`, `Chat`, and `Economy` services directly with the Bukkit `ServicesManager`.

### How It Works

- When the Vault addon is enabled and no external Vault jar is present, System registers itself under the name `Vault` in the plugin manager lookup table. Every `Bukkit.getPluginManager().getPlugin("Vault")` check resolves to System.
- Since v3.90, the Vault API classes ship inside the System JAR without relocation, providing the full `net.milkbowl.vault` API surface to every other plugin through the shared plugin class registry.
- The Economy addon registers the Vault `Economy` service directly — no external Vault plugin needed.
- A `ServiceRegisterEvent` listener watches for provider changes and re-resolves priorities dynamically, fixing the upstream problem where late-registering providers were never re-evaluated.
- Plugin enable and disable events hook and unhook GroupManager and PermissionsEx dynamically, so load order does not matter.
- The `SystemPerms` fallback resolves player groups from standard `group.` and `groups.` permission nodes, so consumers like TAB receive real group data even without a dedicated permission plugin.

### Registered Providers

| Service | Provider | Priority | Notes |
|---------|----------|----------|-------|
| `Permission` | PermissionsEx | Highest | Hooked reflectively when present. |
| `Permission` | GroupManager | High | Hooked reflectively when present. |
| `Permission` | SystemPerms | Lowest | Always registered. Resolves groups from permission nodes. |
| `Chat` | PermissionsEx_Chat | Highest | Hooked reflectively when present. |
| `Chat` | GroupManager_Chat | Normal | Hooked reflectively when present. |
| `Economy` | System Economy | Normal | Registered by the Economy addon. |

---

## Economy – MongoDB + Redis

A complete economy subsystem with five components working together.

### Architecture

- **EconomyCore** — the central balance API used by commands and the Vault hook. Thread-safe with a shared `MoneyFormat` renderer (Locale.US comma grouping, two fraction digits, trailing zeros stripped).
- **MongoStorage** — persistent storage backed by MongoDB 4.11.1 (shaded). All balances survive server crashes and restarts.
- **RedisCache** — read-through cache backed by Redis 5.1.0 (shaded). Hot balances served from Redis to avoid round-trips to Mongo on every command.
- **PlayerManager** — warms the cache on player join, flushes dirty balances to Mongo on player quit and on a configurable tick interval.
- **Commands** — `/balance`, `/pay`, `/money give|take|set|help`.

### Vault Integration

The Economy addon registers the Vault `Economy` service directly with the Bukkit `ServicesManager`. Any plugin that uses the Vault Economy API reads and writes balances through System's economy subsystem. The `fractionalDigits` capability reports two digits so external consumers format consistently. The formatter is thread-local so asynchronous consumers like TAB never share one `DecimalFormat` instance.

---

## 33 Decorative Animations

A decorative animations subsystem with 33 built-in types across four categories. Every animation runs on a configurable tick interval and continues until explicitly stopped. Block-based animations only modify existing blocks and restore the original state on stop. Item-based animations use unique hidden identities to prevent vanilla item merging, with micro gravity-compensation for smooth floating.

### Block-based (11)

| Type | Name | Behavior |
|------|------|----------|
| `blockpulse` | Block Pulse | Cycles existing blocks beneath the player through glowing materials |
| `blockwave` | Block Wave | Outward wave of colored blocks in expanding rings |
| `blockrotate` | Block Rotate | Rotates existing blocks through material cycles |
| `blockspiral` | Block Spiral | Tight spiral of cycling blocks around the player |
| `blockrain` | Block Rain | Falling blocks from overhead, auto-cleaned on landing |
| `blockfloor` | Block Floor | Pulsing floor grid of colored materials |
| `blockchecker` | Block Checker | Alternating checkerboard pattern on existing blocks |
| `blockline` | Block Line | Moving line of cycling materials |
| `blockcross` | Block Cross | Pulsing cross pattern outward |
| `blockdiamond` | Block Diamond | Rotating colors on a diamond pattern |
| `blockmine` | Block Mine | Crack-stage mining animation with random block change |

### Particle-based (13)

| Type | Name | Type | Name |
|------|------|------|------|
| `particlering` | Particle Ring | `particleshockwave` | Particle Shockwave |
| `particlehelix` | Particle Helix | `particlefire` | Particle Fire |
| `particletornado` | Particle Tornado | `particlewings` | Particle Wings |
| `particlefountain` | Particle Fountain | `particlevillagerhurt` | Villager Hurt |
| `particledome` | Particle Dome | `particlegreenmagic` | Green Magic |
| `particlespiral` | Particle Spiral | `particlerain` | Particle Rain |
| `particleaura` | Particle Aura | | |

### Item-based (6)

| Type | Name | Type | Name |
|------|------|------|------|
| `itemorbit` | Item Orbit | `itemhelix` | Item Helix |
| `itemfountain` | Item Fountain | `itemtornado` | Item Tornado |
| `itemsphere` | Item Sphere | | |
| `itemvortex` | Item Vortex | | |

### Special (3)

| Type | Name | Behavior |
|------|------|----------|
| `lightningfire` | Lightning Fire | Effect-only lightning with tracked, self-extinguishing fire |
| `colorfulsheep` | Colorful Sheep | Invincible colorful sheep; right-click to launch |
| `armorstandfight` | Armor Stand Fight | Cinematic choreographed duel with grapples, throws, and execution |

### Crash Recovery

The animation system keeps a world-state recovery snapshot so an unclean shutdown never leaves orphaned entities behind. Every entity is tracked by UUID in `animations-recovery.yml`. On startup, a recovery sweep removes every tracked entity and extinguishes every tracked fire across all loaded worlds. A chunk-load watcher then keeps removing tracked entities the moment their chunk loads. The shutdown path is fault-isolated: every addon disable call is wrapped in its own error handler, so one addon failing to disable can never skip animation cleanup.

---

## Commands & Permissions

### Main Command: `/system` (alias `/sys`)

| Subcommand | Purpose | Permission | Console |
|-----------|---------|------------|---------|
| `/system reload` | Reload all configuration | `system.reload` | Yes |
| `/system status` | Show restart schedule and backup state | `system.status` | Yes |
| `/system backup` | Trigger manual backup | `system.backup` | Yes |
| `/system restart` | Schedule manual restart | `system.restart` | Yes |
| `/system stop` | Cancel scheduled restart | `system.stop` | Yes |
| `/system setspawn` | Set spawn point for current world | `system.setspawn` | No |
| `/system build` | Toggle build mode (per-player) | `system.build` | No |
| `/system help` | Print help screen | `system.help` | Yes |

### Economy Commands

| Command | Purpose | Permission |
|---------|---------|------------|
| `/balance` (`/bal`) | Check balance | `economy.command.balance` |
| `/pay <player> <amount>` | Transfer money | `economy.command.pay` |
| `/money give <player> <amount>` | Give money | `economy.command.give` |
| `/money take <player> <amount>` | Take money | `economy.command.take` |
| `/money set <player> <amount>` | Set balance | `economy.command.set` |

### Player Commands

| Command | Purpose | Permission |
|---------|---------|------------|
| `/doublejump` | Toggle double jump (per-player opt-in) | `system.doublejump` |
| `/emoji [page]` | List loaded emojis | `chatemojis.list` |
| `/book <id>` | Open a configured book | `interactivebooks.open` |
| `/fw` (`/firework`) | Launch a firework | `firework.launch` |
| `/kaboom <player>` / `/kaboom all` | Launch player(s) into the air | `kaboom.command.use` |
| `/joinmessage set/clear/reload` | Manage per-player join messages | `joinmessage.admin` |

### Animation Commands

| Command | Purpose | Permission |
|---------|---------|------------|
| `/system animations list` | List active animations | `system.animations.use` |
| `/system animations create <type> [radius]` | Create animation | `system.animations.admin` |
| `/system animations delete <id>` | Remove animation | `system.animations.admin` |
| `/system animations tp <id>` | Teleport to animation | `system.animations.admin` |
| `/system animations info <id>` | Show animation details | `system.animations.use` |
| `/system animations stop` | Stop all animations | `system.animations.admin` |

---

## PlaceholderAPI Integration

System registers an automatic `vault` PlaceholderAPI expansion and supports built-in placeholders across multiple scopes.

### Vault Economy Placeholders

```
%vault_eco_balance%           # Grouped balance, trailing zeros stripped
%vault_eco_balance_formatted% # Same uniform grouped format
%vault_eco_balance_commas%    # Same uniform grouped format
```

All variants use Locale.US comma grouping, at most two fraction digits, trailing zeros stripped.

### Vault Permission and Chat Placeholders

```
%vault_rank%            # Primary group
%vault_prefix%          # Player prefix
%vault_suffix%          # Player suffix
%vault_rankprefix%      # Prefix of primary group
%vault_ranksuffix%      # Suffix of primary group
%vault_chatprefix%      # Group prefix via chat provider
%vault_chatsuffix%      # Group suffix via chat provider
%vault_groups%          # All parent groups
%vault_rankprefix_N%    # Prefix of Nth parent group (0-based)
```

### Join Message Placeholders

```
%player%       # Exact player name
%displayname%  # Display name
%online%       # Players currently online
```

If PlaceholderAPI is not installed, built-in placeholders are used as fallback and the plugin still works.

---

## Full Configuration

Every value is editable in the `plugins/System/` directory. Nothing is hard-coded.

| File | Purpose |
|------|---------|
| `config.yml` | Core: restart schedule, backup, addon toggles |
| `messages.yml` | All user-facing messages |
| `scoreboard.yml` | Scoreboard layout and refresh interval |
| `spawn.yml` | Spawn points and protected regions |
| `addons/autofly/config.yml` | AutoFly settings |
| `addons/economy/config.yml` | Economy: MongoDB, Redis, currency |
| `addons/joinmessage/config.yml` | Join message formats |
| `addons/kaboom/config.yml` | Kaboom velocity and cooldown |
| `addons/lobbyfireworks/config.yml` | Firework colors, types, blacklist |
| `addons/doublejump/config.yml` | Double jump boost and cooldown |
| `addons/antiswear/config.yml` | Bad word list and filter settings |
| `addons/antiafk/config.yml` | AFK threshold, warnings, title |
| `addons/animations/config.yml` | Animation settings and messages |
| `addons/chatemojis/config.yml` | Emoji definitions and settings |
| `addons/itemjoin/config.yml` | Custom join items |
| `addons/interactivebooks/config.yml` | Book definitions and join behaviors |
| `addons/anticaps/config.yml` | AntiCaps ratio and threshold |
| `addons/chatblocker/config.yml` | Chat filter patterns |
| `addons/worldprotection/config.yml` | Protected worlds list |
| `addons/stairs/config.yml` | Stair seat settings |
| `addons/potioneffect/config.yml` | Potion effect per world |
| `addons/doortoggle/config.yml` | Door auto-close settings |

---

## Storage Backends

### MongoDB (Economy Persistence)

- Driver: `mongodb-driver-sync` 4.11.1 (shaded under `com.nerotek01.lib`).
- Database and collection names are configurable.
- Balances stored as documents keyed by player UUID.
- Authentication optional, uses configured `auth-database`.

### Redis (Economy Cache)

- Driver: `jedis` 5.1.0 (shaded under `com.nerotek01.lib`).
- Cache entries have a configurable TTL.
- Dirty balances written through to Mongo on configurable interval and on player quit.
- If Redis is unreachable, the economy operates without cache — no data is lost.

### H2 (Boot Counter)

- Embedded H2 2.2.224 for backup boot counter persistence.
- Opens in auto-server mode for concurrent access safety.
- Automatic legacy format migration from H2 1.4.x.

---

## Frequently Asked Questions

### Pre-purchase Questions

**Q: Is this a single plugin or do I need multiple downloads?**
A: System ships as a single shaded JAR containing 20 modular addons, a built-in Vault service layer, and all database drivers. You also receive everything needed for lobby management in one purchase.

**Q: Does it support versions newer than 1.8.8?**
A: Currently, System is exclusively engineered for 1.8.8. If future versions are supported, they will be provided as separate, equally optimised branches.

**Q: Do I need Vault or an economy plugin?**
A: No. System includes a built-in Vault addon that registers Permission, Chat, and Economy services natively. No external Vault, Essentials, or economy plugin is required.

**Q: How does the license work?**
A: One payment grants you a permanent license that covers every server you own. There are no recurring fees, no per-server charges, and no hidden costs.

**Q: Can I test the plugin before buying?**
A: Yes. Connect to `mc.hypeland.org` to experience the full plugin on a live server with no registration.

### Technical Questions

**Q: What Java version does my server need?**
A: Java 21 or newer. The JAR is compiled for Java 21 runtime.

**Q: What happens if I disable an addon?**
A: The addon is not loaded, consumes zero CPU, and its configuration file is ignored. All other addons continue to work normally.

**Q: What happens if MongoDB or Redis is unreachable?**
A: The economy addon logs a warning and, for Redis, operates without cache. For MongoDB, the economy addon disables itself. All non-economy features continue to work normally.

**Q: Can I use an external Vault plugin alongside System?**
A: Yes. System declares `softdepend: [Vault]`, loads after it, and lets service priority resolve the providers. The external Vault coexists safely.

### Support

**Q: How do I get help if something breaks?**
A: You have 24/7 direct access to the developer via Discord (`Nerotek01`) or Bale (`Nerotek`). There are no tickets, no forums, and no canned replies.

**Q: Are updates free?**
A: All updates for the current major version are included with your permanent license.

---

## Support & Purchasing

**System** is a premium plugin sold exclusively by the developer.

### How to Purchase
- **Discord:** `Nerotek01`
- **Bale (Iranian users):** `Nerotek`
- **Price:** **€30.00** — one-time payment, permanent license.

### License
**Permanent, all-servers license.** Your purchase covers every server you own — from a single lobby to a 50-server BungeeCord network. There are no recurring fees, no per-server add-ons, and no hidden costs.

### What You Receive
- The complete System plugin JAR (shaded with MongoDB, Redis, and H2 drivers).
- All 20 modular addons, fully integrated and ready to use.
- Built-in Vault service layer (Permission, Chat, Economy).
- 33 decorative animation types with crash recovery.
- Complete economy with MongoDB + Redis.
- Free updates for the current major version.
- **24/7 priority support** via Discord or Bale.

### Support Promise
When an issue arises on your live network, you do not file tickets and hope for a reply. You speak directly with the developer — the person who wrote every line of code. Your uptime is our reputation.

---

<p align="center">
  <a href="https://mc.hypeland.org"><strong>Connect to the demo: mc.hypeland.org</strong></a>
</p>
