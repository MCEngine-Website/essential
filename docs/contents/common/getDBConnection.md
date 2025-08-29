## getDBConnection()

```java
/**
 * Retrieves the active SQL database connection being used by the Essential module.
 * @return JDBC Connection or null if the connection couldn't be established
 */
public Connection getDBConnection()
```

**Usage:**
```java
try (Connection conn = MCEngineEssentialCommon.getApi().getDBConnection()) {
    // Perform queries/prepared statements...
}
```

**Summary:**  
Fetches the current JDBC `Connection` from the Essential DB layer.
