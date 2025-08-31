# How It Works

## Lifecycle
1. **Enable**  
   `Home.java` runs on add-on load:
   - Ensures the **DB schema** via `HomeDB*`
   - Registers the `/home` command and binds the tab completer

2. **Commands**
   - **`/home`** → Opens a GUI listing all saved homes for click-to-teleport
   - **`/home tp [name]`** → Teleports to the named home
   - **`/home set [name]`** → Saves your current location as a named home  
   - **`/home delete [name]`** → Deletes the named home
   - **`/home limit add <player> <int>`** → Increases a player’s home limit (requires `mcengine.essential.home.limit.add`)
   - **`/home limit minus <player> <int>`** → Decreases a player’s home limit (requires `mcengine.essential.home.limit.minus`)
   - (Implementations may also support `/homes` to list names)

3. **Tab Completion**
   - At the first argument, `HomeTabCompleter` now suggests **subcommands only**: `set`, `tp`, `delete`, `limit`
   - For **`/home tp …`** and **`/home delete …`**, it suggests your saved home names for the second argument
   - For **`/home limit`**, it suggests `add`, `minus`, online player names, and common integers

4. **Persistence**
   - `HomeDB*` stores homes per player in the Essential database
   - Each record includes: `player_uuid`, `home_limit`, and named entries in `home_data` with coords

## Permissions
- `mcengine.essential.home.use` — use `/home` features (teleport/open GUI)
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
Essential Home provides a clean, database-backed home system with a GUI, precise `/home tp` teleporting, tab-completion, player-specific limits, and optional configuration—built on the same robust foundation as other Essential add-ons.
