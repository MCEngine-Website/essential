## MCEngineEssentialCommon(Plugin plugin)

```java
/**
 * Constructs the Essential API and prepares the internal dispatcher and database.
 * @param plugin the Bukkit Plugin instance bootstrapping this API
 */
public MCEngineEssentialCommon(Plugin plugin)
```

**Behavior:**
- Initializes the internal `MCEngineCoreApiDispatcher`
- Selects DB backend from `plugin.getConfig().getString("database.type", "sqlite")`
  - `sqlite` → `MCEngineEssentialSQLite`
  - `mysql` → `MCEngineEssentialMySQL`
  - `postgresql` → `MCEngineEssentialPostgreSQL`

**Usage:**
```java
MCEngineEssentialCommon common = new MCEngineEssentialCommon(plugin);
```

**Summary:**  
Sets up command routing and chooses the database implementation based on config.
