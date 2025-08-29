# MCEngineEssential Plugin — Overview

The **MCEngineEssential** plugin is the core engine module that provides shared utilities, database access, and an extension loading framework for Bukkit/Spigot/Paper servers.

## Responsibilities
- Bootstraps the **Essential Common API** (`MCEngineEssentialCommon`)
- Initializes and manages database backends (SQLite/MySQL/PostgreSQL) via `database.type` in `config.yml`
- Provides a **command dispatcher** with support for namespaces, subcommands, and tab completers
- Dynamically loads external extensions:
  - **AddOns** (`IMCEngineEssentialAddOn`)
  - **APIs** (`IMCEngineEssentialAPI`)
  - **DLCs** (`IMCEngineEssentialDLC`)
  - **Libraries** (`IMCEngineEssentialLibrary`)
  - **Agents** (`IMCEngineEssentialAgent`)

## Typical Usage
```java
@Override
public void onEnable() {
    // Initialize common API
    MCEngineEssentialCommon essential = new MCEngineEssentialCommon(this);

    // Register commands
    essential.registerNamespace("essential");
    essential.registerSubCommand("essential", "ping", new PingCommand());
    getCommand("essential").setExecutor(essential.getDispatcher("essential"));

    // Database connection
    try (Connection conn = essential.getDBConnection()) {
        // Perform queries or prepared statements
    }
}
