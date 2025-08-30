# How It Works

## Lifecycle
1. **Enable**  
   On plugin load, the AddOn ensures the schema exists and wires the DB:
   - `fly(fly_id, player_uuid, fly_duration)`
   - Ensures a default row (duration `0`) on **player join**

2. **Activate**  
   Player runs `/fly` (or `/fly on`) → the AddOn:
   - Checks remaining `fly_duration` in DB
   - If `> 0`, enables flight
   - **Prevents duplicate activation** if already flying
   - Starts a **per-player scheduled task** that decrements duration **every 30s**
   - Sends remaining time in **years, hours, minutes, seconds** when activated

3. **Deactivate**  
   - Player runs `/fly off`, leaves server, or duration reaches `0`
   - Disables flight and **cancels the player’s task**
   - On **self-deactivation**, subtracts the **partial elapsed time** since the last 30s tick
   - **Always sends remaining time** in Y/H/M/S when time is reduced (on tick and on self-deactivate)
   - **No decrement offline** (leaving/kick stops the task immediately)

4. **Admin Add**  
   - Admin runs `/fly time add <player> <seconds>`
   - Adds seconds to the target player’s duration in DB
   - Both admin and target see **formatted** remaining time feedback

5. **Get Time**  
   - Player runs `/fly get time`
   - Shows their own remaining flight time in **Y/H/M/S** format

## Permissions
- `mcengine.essential.fly.use` — required to toggle flight  
- `essential.fly.add` — required for `/fly time add`

## Commands
- `/fly`  
- `/fly on`  
- `/fly off`  
- `/fly get time`  
- `/fly time add <player> <seconds>`

## Storage Notes
- **Per-player durations** stored as seconds: `fly_duration`  
- **0 = no remaining time** (activation denied)  
- **Backends**: SQLite / MySQL / PostgreSQL  
- **Safety**: No time is consumed while the player is offline

## File Paths
- AddOn JAR:  
  `plugins/MCEngineEssential/extensions/addons/`  
- Main Essential config:  
  `plugins/MCEngineEssential/config.yml`
