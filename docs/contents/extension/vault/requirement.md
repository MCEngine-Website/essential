# Requirements

- Requires **MCEngine Essential (Engine)** — use the **same version** as your server’s Essential engine.
- Place this AddOn here:  
  `plugins/MCEngineEssential/extensions/addons/`
- (Optional) Configuration file is read from your main Essential `config.yml`.  
  Default keys (auto-used if present):
  - `vault.rows` (1..6, default: `6`)
  - `vault.title` (default: `Vault`)

> Database backend is selected by Essential via `database.type` (`sqlite` | `mysql` | `postgresql`).
