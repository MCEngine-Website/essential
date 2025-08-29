## registerSubCommand(String namespace, String name, CommandExecutor executor)

```java
/**
 * Registers a subcommand under the given namespace.
 * @param namespace the command namespace
 * @param name the subcommand label
 * @param executor logic to execute when the subcommand is invoked
 */
public void registerSubCommand(String namespace, String name, CommandExecutor executor)
```

**Usage:**
```java
common.registerSubCommand("essential", "ping", new PingCommand());
```

**Summary:**  
Adds a namespaced subcommand routed through the core dispatcher.
