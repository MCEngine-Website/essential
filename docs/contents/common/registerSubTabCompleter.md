## registerSubTabCompleter(String namespace, String subcommand, TabCompleter tabCompleter)

```java
/**
 * Registers a tab completer for a subcommand under the given namespace.
 * @param namespace the command namespace
 * @param subcommand the subcommand label
 * @param tabCompleter tab completion logic
 */
public void registerSubTabCompleter(String namespace, String subcommand, TabCompleter tabCompleter)
```

**Usage:**
```java
common.registerSubTabCompleter("essential", "ping", new PingTabCompleter());
```

**Summary:**  
Attaches tab-completion logic to a specific namespaced subcommand.
