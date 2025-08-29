# Introduction to MCEngine Essential (Engine)

The **MCEngine Essential Engine** is the core plugin module that provides fundamental services for the MCEngine ecosystem.  
It acts as the backbone for **Essential extensions** such as AddOns, APIs, DLCs, Libraries, and Agents.

## Key Responsibilities
- Bootstraps the **Essential Common API** (`MCEngineEssentialCommon`)
- Loads and manages extensions dynamically:
  - **AddOns** – feature modules extending gameplay
  - **APIs** – shared logic and service layers
  - **DLCs** – optional feature packs
  - **Libraries** – reusable utilities for other modules
  - **Agents** – specialized integrations or runtime helpers
- Handles **database initialization** (SQLite, MySQL, PostgreSQL)
- Provides a **namespaced command dispatcher** with subcommand and tab-completion support
- Performs **update checks** through GitHub integration

## Typical Workflow
1. **Enable Plugin**
   - Loads config (`config.yml`)
   - Sets up DB backend (default: SQLite)
   - Initializes `MCEngineEssentialCommon`

2. **Register Commands**
   - Define namespaces and subcommands using the dispatcher
   - Bind Bukkit commands to the dispatcher

3. **Load Extensions**
   - AddOns, APIs, DLCs, Libraries, and Agents are discovered and loaded at runtime
   - Each extension implements its lifecycle (`onLoad`, `onDisload`, `setId`)

4. **Database Access**
   - Developers can use `getDBConnection()` for direct SQL queries
   - DB type controlled via `database.type` in `config.yml`

## Configuration
```yaml
enable: true
license: free

database:
  type: sqlite   # or mysql / postgresql
  host: localhost
  port: 3306
  name: essential
  username: root
  password: secret
```

## Why Use Essential?
- Centralized **plugin lifecycle management**
- Unified **command routing and DB access**
- Flexible **extension framework** for building modular server features
- Reliable **update checks** to keep deployments current

**Summary:**  
MCEngine Essential is the foundation for everything built on the Essential ecosystem. It ensures consistency, scalability, and extensibility for developers and server owners alike.
