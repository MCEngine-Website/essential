# How It Works

## Lifecycle
1. **Enable**  
   On plugin load, the AddOn ensures the schema exists:
   - `essential_vault_meta(player_uuid, rows, title, updated_at)`
   - `essential_vault_item(player_uuid, page, slot, item_bytes)`

2. **Open**  
   Player runs `/vault` (or `/vault open`) → the AddOn:
   - Loads their vault meta/items from DB
   - Builds a Bukkit inventory with the configured rows/title
   - Sets a metadata flag on the player to mark a “vault session”
   - Opens the inventory

3. **Save**  
   When the player closes the inventory:
   - The listener detects the “vault session” flag
   - Captures all non-air items and serializes them with `BukkitObjectOutputStream`
   - Upserts the meta’s `updated_at` and replaces item rows for page `0`
   - **Nothing else is required by the player** — saving is automatic

## Permissions
- `mcengine.essential.vault.use` — required to open the vault

## Commands
- `/vault`  
- `/vault open`

> Rows/title are read from Essential’s `config.yml` (optional). The addon won’t change them via commands.

## Storage Notes
- **Metadata safe**: Every `ItemStack` is stored in a binary column (`BLOB`/`BYTEA`) to preserve full NBT.
- **Backends**: Works with SQLite/MySQL/PostgreSQL; the correct binary type is chosen automatically.

## File Paths
- AddOn JAR:  
  `plugins/MCEngineEssential/extensions/addons/`
- Main Essential config:  
  `plugins/MCEngineEssential/config.yml`
