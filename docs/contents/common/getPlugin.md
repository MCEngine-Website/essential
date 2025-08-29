## getPlugin()

```java
/**
 * Returns the Bukkit plugin instance associated with this API.
 * @return the plugin instance
 */
public Plugin getPlugin()
```

**Usage:**
```java
Plugin plugin = MCEngineEssentialCommon.getApi().getPlugin();
```

**Summary:**  
Retrieves the owning Bukkit `Plugin`, useful for config and task scheduling.
