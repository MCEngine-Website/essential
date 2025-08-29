# MCEngineEssentialCommon — Quick Reference

A lightweight facade that wires a Bukkit `Plugin` to:
- A namespaced command dispatcher (register namespaces, subcommands, tab completers)
- The Essential DB interface/connection (SQLite/MySQL/PostgreSQL selected via config)

**Typical Usage:**
```java
MCEngineEssentialCommon essential = new MCEngineEssentialCommon(plugin);
essential.registerNamespace("essential");
essential.registerSubCommand("essential", "ping", new PingCommand());
plugin.getCommand("essential").setExecutor(essential.getDispatcher("essential"));

try (Connection conn = essential.getDBConnection()) {
    // Perform queries...
}
```
