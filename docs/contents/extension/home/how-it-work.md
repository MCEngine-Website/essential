# How It Works

## Lifecycle
1. **Enable**  
   `Home.java` runs on add-on load:
   - Ensures the **DB schema** via `HomeDB`
   - Registers the `/home` command and binds the tab completer
2. **Commands**
   - **`/home [name]`** → Teleport to an existing home (default name if omitted)
   - **`/sethome [name]`** → Save your current location as a named home  
   - **`/delhome [name]`** → Delete a saved home
   - (Implementations may also support `/homes` to list names)
3. **Tab Completion**
   - `HomeTabCompleter` suggests your saved home names when typing `/home` or `/delhome`
4. **Persistence**
   - `HomeDB` stores homes per player in the Essential database
   - Each record typically includes: `player_uuid`, `home_name`, `world`, `x`, `y`, `z`, `yaw`, `pitch`, `updated_at`

## Permissions (suggested)
- `mcengine.essential.home.use` — use `/home` to teleport
- `mcengine.essential.home.set` — use `/sethome` to create/update
- `mcengine.essential.home.delete` — use `/delhome` to remove

> You can tailor permission checks inside `HomeCommand.java` to your server’s policy.

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
Essential Home provides a clean, database-backed home system with straightforward commands, tab-completion, and optional configuration—built on the same robust foundation as other Essential add-ons.
