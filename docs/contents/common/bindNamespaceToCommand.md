## bindNamespaceToCommand(String namespace, CommandExecutor commandExecutor)

```java
/**
 * Binds a Bukkit command (e.g., /essential) to the internal dispatcher.
 * Typical usage: plugin.getCommand("essential").setExecutor(essential.getDispatcher("essential"))
 * @param namespace the command namespace to bind
 * @param commandExecutor an optional fallback CommandExecutor
 */
public void bindNamespaceToCommand(String namespace, CommandExecutor commandExecutor)
```

**Usage:**
```java
MCEngineEssentialCommon common = MCEngineEssentialCommon.getApi();
common.registerNamespace("essential");
plugin.getCommand("essential").setExecutor(common.getDispatcher("essential"));
```

**Summary:**  
Connects a Bukkit command to the dispatcher for the given namespace.
