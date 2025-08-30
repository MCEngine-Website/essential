# Requirements

- Requires **MCEngine Essential (Engine)** — use the **same version** as your server’s Essential engine.
- Place this AddOn here:  
  `plugins/MCEngineEssential/extensions/addons/`
- (Optional) Settings can be read from your main Essential `config.yml`.  
  Common keys (only if you choose to define them):
  - `home.max` (integer; maximum homes per player, e.g., `3`)
  - `home.default-name` (string; name used when none is provided, e.g., `"home"`)
  - `home.cooldown-seconds` (integer; cooldown after teleport)
  - `home.warmup-seconds` (integer; warmup before teleport)
  - `home.cross-world` (boolean; allow teleporting across worlds)

> The database backend is selected by Essential via `database.type` (`sqlite` | `mysql` | `postgresql`) in `plugins/MCEngineEssential/config.yml`.
