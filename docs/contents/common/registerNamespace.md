## registerNamespace(String namespace)

```java
/**
 * Registers a command namespace (e.g., "essential") for this module.
 * @param namespace unique namespace to register
 */
public void registerNamespace(String namespace)
```

**Usage:**
```java
MCEngineEssentialCommon common = MCEngineEssentialCommon.getApi();
common.registerNamespace("essential");
```

**Summary:**  
Creates a logical bucket for subcommands and tab completers within the dispatcher.
