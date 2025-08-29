## getDB()

```java
/**
 * Returns the database interface used by this module.
 * @return the IMCEngineEssentialDB instance
 */
public IMCEngineEssentialDB getDB()
```

**Usage:**
```java
IMCEngineEssentialDB db = MCEngineEssentialCommon.getApi().getDB();
```

**Summary:**  
Provides access to the Essential database abstraction (driver selected by config).
