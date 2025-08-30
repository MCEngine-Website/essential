# Configuration

**Essential Home** does not require a dedicated config file — simply drop the JAR into:

plugins/MCEngineEssential/extensions/addons/


It will automatically create its database schema on first run.

---

## Optional Configuration (via main `config.yml`)

The addon can read values from your main **Essential config** (`plugins/MCEngineEssential/config.yml`).  
These keys are **optional**; defaults are applied if missing:

```yaml
home:
  max: 3                 # Maximum homes per player (default: unlimited if not set)
  default-name: "home"   # Fallback name used if player doesn’t specify
  cooldown-seconds: 30   # Cooldown in seconds after using /home
  warmup-seconds: 5      # Warmup delay before teleportation
  cross-world: true      # Allow teleportation across worlds
