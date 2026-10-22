<p align="center">
  <img src="https://img.shields.io/badge/version-4.4-blue?style=flat-square&logo=github" alt="Version 4.4">
  <img src="https://img.shields.io/badge/minecraft-1.8.8-62BF7C?style=flat-square&logo=minecraft" alt="Minecraft 1.8.8">
  <img src="https://img.shields.io/badge/platform-spigot%201.8.8-E5823D?style=flat-square" alt="Spigot 1.8.8">
  <img src="https://img.shields.io/badge/java-21%2B-F89820?style=flat-square&logo=openjdk" alt="Java 21+">
  <img src="https://img.shields.io/badge/license-proprietary-lightgrey?style=flat-square&logo=github" alt="Proprietary license">
</p>

<h1 align="center">System</h1>

<p align="center"><strong>The all-in-one server suite for Spigot 1.8.8 — operations, economy, chat and lobby in a single jar.</strong></p>

---

## Highlights

- **One jar, everything included.** Sixteen toggleable subsystems plus core admin tools — scheduled restarts, backups, world protection, economy, chat moderation and lobby cosmetics — in a single shaded build for Spigot 1.8.8.
- **Runs on a bare server.** Zero hard dependencies: Vault, PlaceholderAPI, GroupManager, PermissionsEx and Essentials are optional, and every integration degrades gracefully with a clear log line.
- **A Vault layer other plugins can use.** Bundled VaultAPI, built-in Permission/Chat providers (GroupManager, PermissionsEx, internal fallback with group detection) and a name alias so `getPlugin("Vault")` resolves to System even when no external Vault plugin is installed.
- **Serious economy, when you opt in.** MongoDB persistence, a Redis read-through balance cache and sorted-set leaderboard, a Vault Economy provider and race-safe `/pay` with per-transfer locking and NaN/overflow rejection. Ships disabled until you enable it.
- **Operations built for uptime.** Timezone-aware daily restarts with countdown broadcasts, a pre-restart protocol that locks containers, movement and chat, tar.gz backups with retention, boot-count backups, login lock under CPU/memory pressure and automatic log cleanup.
- **A complete chat suite.** Anti-caps with progressive decapitalization, anti-swear with a shipped 6,131-entry list, per-world chat mute, 39 chat emojis across chat, signs, books, anvils and Essentials private messages, and a join/leave message engine with 12 action types and rank-priority formats.
- **33 decorative animations.** Four categories (block, particle, item, special) with automatic block restore, crash recovery across restarts and viewer-distance idle optimization.
- **Operator-friendly by design.** `/system reload` re-reads every config without a restart, permissions are enforced per subcommand, tab completion is everywhere, and the core command set is console-safe.

## Features at a glance

| Domain | What you get |
|---|---|
| Server operations | Timezone-aware daily restart (default `04:00`) with minute- and second-level countdown broadcasts; manual restart scheduling and cancellation; pre-shutdown backup window; a last-minute protocol that locks containers, blocks interaction, freezes X/Z movement and disables chat before the restart lands; `/system status` shows the live countdown and last-backup validity |
| Backups & housekeeping | tar.gz archives of configured folders (worlds saved first, atomic `.tmp` move, retention keeps the newest N); OP-triggered once-per-24h backup slot; boot-count backup every N boots via a local H2 counter; log-size watcher plus day-based old-log cleanup; server warnings and errors mirrored into bounded YAML files |
| Availability | Login lock that kicks connections during the startup window and while CPU or memory exceed lock thresholds, with separate unlock thresholds, hysteresis, a minimum toggle interval and a name/UUID whitelist |
| World protection | Configurable per-world protection covering block break/place, interactions (including containers), entity interaction, hanging break/place, item drop/pickup, damage, damage-by-entity, food level, entity combust and bed entry; per-player build-mode override; sleep and weather-change blockers |
| Lobby life | Auto-closing doors, trapdoors and fence gates on a timer; stair seating on a hidden armor stand with player-facing rotation; persistent lobby potion effect; Kaboom launcher with per-player and global cooldowns; random lobby fireworks on `/fw` |
| Spawn system | Fixed spawn point or a random spawn region defined by two corners, with anti-clustering (minimum distance between recent spawn points, per-player re-spawn distance, point TTL); teleport-on-join and respawn-into-spawn handling; void-fall rescue below y=0 in spawn worlds |
| Chat moderation | AntiCaps with a caps-ratio threshold and progressive decapitalization; AntiSwear with a shipped 6,131-entry regex list (star replacement or cancel, chat-command filtering for `msg`/`tell`/`whisper`/`me` and more, per-world scope); ChatBlocker for a full per-world chat mute |
| Chat cosmetics | 39 configured emoticons rendered as unicode emoji in chat, signs, books, anvil renames and Essentials private messages; per-emoji permission tree; regex guard against catastrophic patterns |
| Join / leave engine | Rank formats with priorities (`joinmessage.format.<rank>`, 25 formats shipped) driving 12 action types — JSON clickables, titles, actionbars, sounds and player/console commands — with world-scoped broadcasts and owner-join fireworks |
| Economy (opt-in) | Full Vault Economy provider with bank methods and fractional digits; MongoDB persistent storage with auth and SSL options; Redis read-through balance cache plus sorted-set leaderboard; race-safe `/pay` with ordered per-UUID locking, single two-document writes and negative/NaN rejection; periodic async dirty-save and an honest shutdown flush |
| Vault service layer | Bundled VaultAPI; Vault `Permission` and `Chat` providers backed by GroupManager and PermissionsEx plus a built-in fallback; live hot-plug when permission plugins enable or disable; class-identity diagnostics for duplicate Vault classes |
| Cosmetics & movement | 33 decorative animations (block, particle, item, special — e.g. `blockrain`, `particletornado`, `itemvortex`, `colorfulsheep` with a configurable reward command) with auto-restore, crash recovery and a 256-active cap; opt-in DoubleJump; AutoFly with no-fall protection and built-in double jump; AntiAfk with four staged warnings, title overlay and return message |
| Items & books | ItemJoin hotbar items with slots, skull owners, enchantments, interact commands (`player:` / `console:` / `message:` / `op:`) and itemflags; InteractiveBooks with `/book <id>`, per-book chat aliases, open-on-join, first-join-only and PlaceholderAPI in pages |
| Scoreboard | Sidebar scoreboard from `scoreboard.yml` with every line PlaceholderAPI-resolved, refreshed every 20 ticks with placeholder work staggered across buckets so per-tick PAPI cost stays low; live reload of layout and enable flag |

## Commands

| Command | Permission | Description |
|---|---|---|
| `/system` (alias `/sys`) | `system.use` | Core command. Subcommands: `reload` (`system.reload`), `status` (`system.status`), `backup` (`system.backup`), `restart` (`system.restart`), `stop` (`system.stop`), `setspawn pos1\|pos2\|clear\|info` (`system.setspawn`, player-only), `build` (`system.build`), `animations`, `help`. Console may use `reload`/`status`/`backup`/`restart`/`stop`/`help` |
| `/system animations <list\|create\|delete\|tp\|info\|stop>` | `system.animations.use` (list/info), `system.animations.admin` (create/delete/tp/stop) | Manage decorative animations; `create` takes `<type> [radius]` with tab completion |
| `/kaboom <player\|all>` | `kaboom.command.use` | Launch a player, a comma-separated name list, or everyone in the configured world |
| `/doublejump` | none (player-only toggle) | Toggle double jump for yourself; disables AutoFly first |
| `/book <id>` | `interactivebooks.open` plus per-book view permission | Open a configured interactive book |
| `/fw`, `/firework` | `firework.launch` | Launch random lobby fireworks; bypasses: `firework.bypass.cooldown`, `firework.bypass.world` |
| `/money <give\|take\|set\|help>` (aliases `/economy`, `/eco`) | `economy.command.give` / `.take` / `.set` / `.help` | Admin money management with usage validation and tab completion |
| `/balance [player]` (alias `/bal`) | `economy.command.balance` | Show your own or another player's balance |
| `/pay <player> <amount>` | `economy.command.pay` | Race-safe player-to-player transfer; self-pay blocked |
| `/joinmessage [version\|help\|reload\|checkformat]` (alias `/jjoin`) | base open; `joinmessage.admin` for `reload`/`checkformat` | Inspect and reload join/leave formats; `checkformat` shows the effective format for a player |
| `/emoji [page]` (alias `/emojis`) | `chatemojis.list` | Paginated list (10 per page) of available chat emojis |

Every command is declared in `plugin.yml` and re-bound at runtime, so disabling an addon swaps in a silent no-op handler instead of leaving a dead command.

## Quick start

System is sold as a personal build — there are no public downloads.

1. **Purchase** System at [store.hypeland.org](https://store.hypeland.org).
2. **Verify** your purchase in a ticket on the official [Discord](https://discord.gg/kEPvGp8Yz7).
3. **Receive** your personal build and license key, delivered 1:1.
4. **Install:** drop the jar into `plugins/`, then restart the server.
5. **Configure** under `plugins/System/` — every subsystem ships with generous defaults and is toggled independently.

Optional next steps once it is running: enable the economy addon and point it at MongoDB and Redis, install Vault or PlaceholderAPI for integrations, and adjust the restart schedule and protected worlds in `config.yml`.

## Configuration

The jar ships 17 documented YAML resources, all created under `plugins/System/` on first run:

- `config.yml` — core switches: restart schedule, backups, login lock, world protection, spawn, scoreboard, and the per-addon toggles
- `messages.yml` — every core text, auto-merged on version bumps
- `scoreboard.yml`, `spawn.yml`
- 12 addon configs: `addons/{animations, antiafk, antiswear, autofly, chatemojis, doublejump, economy, interactivebooks, itemjoin, joinmessage, kaboom, lobbyfireworks}/config.yml`

A taste of `config.yml`:

```yaml
restart-time: "04:00"
restart-timezone: Asia/Tehran
pre-restart-protocol:
  enabled: true
backup-management:
  max-backups: 3
world-protection:
  protected-worlds: []
door-toggle:
  revert-seconds: 60
scoreboard-enabled: true
scoreboard:
  stagger-buckets: 4
addons:
  economy:
    enabled: false   # economy ships disabled - enable it when ready
```

> **Economy note:** the economy addon ships **disabled by default** (`addons.economy.enabled: false`) and requires Vault availability — either an external Vault plugin or System's built-in Vault addon. Enable it deliberately, not by accident.

## PlaceholderAPI

System both consumes and registers placeholders:

- **Consumer:** PlaceholderAPI placeholders resolve in scoreboard lines, join/leave message actions, interactive book pages and chat-emoji replacement values. Without PlaceholderAPI installed, the built-in `%player%`, `%displayname%` and `%online%` tokens still resolve everywhere.
- **Provider:** System registers exactly one expansion — the **`vault`** expansion: `%vault_rank%`, `%vault_group%`, `%vault_prefix%`, `%vault_suffix%`, `%vault_rankprefix%`, `%vault_eco_balance%` (plus `_fixed`/`_formatted`/`_commas` variants), `%vault_permgroup_<permission>%` and more. It persists across PlaceholderAPI reloads and stays passive if another `vault` expansion is already present.

## Compatibility & requirements

| Requirement | Detail |
|---|---|
| Minecraft | 1.8.8 — built against the Spigot 1.8.8 API, with 1.8.8 NMS (`v1_8_R3`) reflection for JSON join messages, titles, actionbars and knockback velocity |
| Java | 21 or newer at runtime |
| Hard dependencies | None — the plugin loads on a bare 1.8.8 server |
| Optional plugins | Vault, PlaceholderAPI, GroupManager, PermissionsEx, Essentials — all degrade gracefully |
| Optional storage | MongoDB (economy persistence) and Redis via Jedis (balance cache and leaderboard) — both drivers are bundled inside the jar, so no extra downloads |

## FAQ

**Does System work without Vault installed?**
Yes. VaultAPI ships inside the jar, a built-in permission fallback covers group detection, and through a registry alias System even answers to the plugin name `Vault` when no external Vault plugin is present — so other plugins' Vault hooks keep working.

**Is the economy enabled out of the box?**
No. `addons.economy.enabled` ships as `false` on purpose. Enable it in `config.yml`, and make sure Vault is available (external plugin or System's built-in Vault addon). MongoDB and Redis are then used for persistence and caching once configured.

**Which permissions plugins does it hook natively?**
GroupManager and PermissionsEx, via reflective Vault `Permission` and `Chat` providers that hot-plug as those plugins enable or disable. Any other setup goes through the standard Vault bridge or the built-in fallback.

**Is there a `/spawn`, `/fly` or `/baltop` command?**
No. Spawn handling is automatic on join, respawn and void-fall; flight is automatic through AutoFly in allowed worlds; there is no baltop command. Keeping the command surface small is a design decision, not a missing feature.

**Does ChatBlocker filter specific words or links?**
No. ChatBlocker mutes **all** chat in the worlds you configure — that is its entire job. Word and link-level filtering belong to AntiSwear, which ships with a 6,131-entry list and command filtering.

**How is the plugin delivered and updated?**
Every purchase is delivered 1:1 as a personal build with a license key after verification on the official Discord. There are no public download links.

## Links

<p align="center">
  <a href="https://store.hypeland.org">Store — store.hypeland.org</a> ·
  <a href="https://store.hypeland.org/docs">Docs — store.hypeland.org/docs</a> ·
  <a href="https://discord.gg/kEPvGp8Yz7">Discord — discord.gg/kEPvGp8Yz7</a>
</p>

<p align="center"><em>© Nerotek Development — premium Minecraft plugins.</em></p>
