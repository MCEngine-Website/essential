## getDispatcher(String namespace)

```java
/**
 * Obtains the dispatcher to assign as the command executor and tab completer
 * for a Bukkit command mapped to the provided namespace.
 * @param namespace the command namespace
 * @return a CommandExecutor that routes to the internal dispatcher
 */
public CommandExecutor getDispatcher(String namespace)
```

**Usage:**
```java
plugin.getCommand("essential").setExecutor(common.getDispatcher("essential"));
```

**Summary:**  
Retrieves the `CommandExecutor` proxy that forwards to the internal dispatcher for the namespace.
