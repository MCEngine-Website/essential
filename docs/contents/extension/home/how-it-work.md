# How It Works

## Lifecycle
1. **Enable**  
   `Home.java` runs on add-on load:
   - Ensures the **DB schema** via `HomeDB*`
   - Registers the `/home` command and binds the tab completer
2. **Commands**
   - **`/home [name]`** → Teleport to an existing home
   - **`/home set [name]`** → Save your current location as a named home  
   - **`/home delete [name]`** → Delete a saved home
   - **`/home limit add <player> <int>`** → Increase a player’s home limit (requires `mcengine.essential.home.limit.add`)
   - **`/home limit minus <player> <int>`** → Decrease a player’s home limit (requires `mcengine.essential.home.limit.minus`)
   - (Implementations may also support `/homes` to list names)
3. **Tab Completion**
   - `HomeTabCompleter` suggests your saved home names when typing `/home`
   - Also suggests `add`, `minus`, player names, and common integers for `/home limit`
4. **Persistence**
   - `HomeDB*` stores homes per player in the Essential database
   - Each record includes: `player_uuid`, `home_limit`, and named entries in `home_data` with coords

## Permissions
- `mcengine.essential.home.use` — use `/home` to teleport
- `mcengine.essential.home.set` — use `/home set` to create
- `mcengine.essential.home.delete` — use `/home delete` to remove
- `mcengine.essential.home.limit.add` — allow increasing home limits
- `mcengine.essential.home.limit.minus` — allow decreasing home limits

## Configuration (optional)
If present in `config.yml`, `HomeConfigUtil` can read:
- **Limits**: `home.max`
- **Timing**: `home.cooldown-seconds`, `home.warmup-seconds`
- **Behavior**: `home.cross-world`, `home.default-name`

## Data Notes
- **DB portability**: Works with SQLite / MySQL / PostgreSQL via Essential’s DB interface.
- **Safety**: You can add checks for blocked worlds, combat timers, or regions before teleporting.
- **Names**: Treat names case-insensitively for a better UX, but store them consistently.

**Summary:**  
Essential Home provides a clean, database-backed home system with commands, tab-completion, player-specific limits, and optional configuration—built on the same robust foundation as other Essential add-ons.
