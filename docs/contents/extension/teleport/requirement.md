# Requirements

- Requires [**`MCEngine Essential`**](https://github.com/MCEngine-Engine/essential/releases) must match your server’s Essential engine version.
- Place this AddOn here:  
  `plugins/MCEngineEssential/extensions/addons/`

**Permissions**
- `essential.teleport.tp` — instant teleport (`/tp`), default **OP**
- `essential.teleport.tpa` — request teleport (`/tpa` + `/tpaccept`), default **all players**

These permissions are registered programmatically by the addon, so you don’t need to declare them in `plugin.yml`.

> No database schema is required for this addon.  
> It uses an in-memory cache (`TeleportCache`) that automatically expires requests after 30 seconds.
