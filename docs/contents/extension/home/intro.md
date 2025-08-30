# Introduction

**Essential Home** is an AddOn that lets players save and teleport to personal “home” locations.  
Homes are stored in a database via Essential’s DB layer, and tab-completion makes it easy to manage named homes.

**Key features**
- Per-player, **named** homes (e.g., `home`, `mine`, `village`)
- **Database-backed** storage (SQLite / MySQL / PostgreSQL supported by Essential)
- Simple commands for **set**, **teleport**, and **delete**
- Smart **tab completion** for home names
- Optional config for limits, cooldowns, and behavior (via the engine’s config)

**Source layout (high level)**
- `Home.java` – registers command & bootstraps DB schema
- `command/HomeCommand.java` – handles `/home`, `/sethome`, `/delhome` (and variants)
- `tabcompleter/HomeTabCompleter.java` – provides name suggestions
- `util/HomeConfigUtil.java` – reads optional config values
- `util/HomeDB.java` – schema + CRUD for homes
