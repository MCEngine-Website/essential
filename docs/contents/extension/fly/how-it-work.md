# How It Works

## Lifecycle
1. **Enable**  
   On plugin load, the AddOn ensures the schema exists:
   - `fly(fly_id, player_uuid, fly_duration)`

2. **Activate**  
   Player runs `/fly` (or `/fly on`) → the AddOn:
   - Checks remaining `fly_duration` in DB
   - If > 0, flight mode is enabled
   - Starts a per-player scheduled task that decrements duration every 30s
   - Prevents duplicate activation if already active

3. **Deactivate**  
   - Player runs `/fly off`, leaves server, or their duration hits `0`
   - Flight is disabled, and the per-player task is cancelled
   - On self-deactivation, the AddOn subtracts the partial elapsed time since the last tick
   - Player is always shown their remaining time in **years, hours, minutes, seconds** format
   - No decrement happens while offline

4. **Admin Add**  
   - Admin runs `/fly time add <player> <seconds>`
   - Adds seconds to the target player’s duration in DB
   - Both admin and target receive formatted remaining time feedback

## Permissions
- `mcengine.essential.fly.use` — required to toggle flight  
- `essential.fly.add` — required for `/fly time add`

## Commands
- `/fly`  
- `/fly on`  
- `/fly off`  
- `/fly time add <player> <seconds>`

## Storage Notes
- **Durations stored per player**: `fly_duration` in seconds  
- **0 = no remaining time** (flight activation denied)  
- **Backends**: Works with SQLite/MySQL/PostgreSQL  

## File Paths
- AddOn JAR:  
  `plugins/MCEngineEssential/extensions/addons/`  
- Main Essential config:  
  `plugins/MCEngineEssential/config.yml`
