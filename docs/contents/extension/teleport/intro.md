# Introduction

[`Repository`](https://github.com/MCEngine-Extension/essential-addon-teleport)  
[`GitHub Release`](https://github.com/MCEngine-Extension/essential-addon-teleport/releases)

**Essential Teleport** is an AddOn that provides instant and request-based teleportation between players.  
It integrates cleanly with the Essential engine and uses a lightweight cache system to handle `/tpa` requests.

**Key features**
- **Instant teleport** with `/tp <player>` (OP-only by default)
- **Request teleport** with `/tpa <player>` and `/tpaccept`  
  - Target must accept within 30 seconds  
  - Automatic cleanup on logout or expiry
- **Configurable delay**: 4-second warmup after `/tpaccept`
- **Dynamic permissions** registered in code
- **Cache + model layer** (`TeleportCache`, `TeleportRequest`) for clean request tracking

**Source layout (high level)**
- `Teleport.java` – registers commands, permissions, and listener
- `command/TeleportCommand.java` – handles `/tp`, `/tpa`, `/tpaccept`
- `tabcompleter/TeleportTabCompleter.java` – tab-completion for player names
- `listener/TeleportListener.java` – cleans up requests on quit
- `cache/TeleportCache.java` – manages request lifecycle + expirations
- `model/TeleportRequest.java` – request data model with expiry info
