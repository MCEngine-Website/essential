# Introduction

[`Repository`](https://github.com/MCEngine-Extension/essential-addon-home)
[`GitHub Release`](https://github.com/MCEngine-Extension/essential-addon-home/releases)

**Essential Home** is an AddOn that lets players save and teleport to personal “home” locations.  
Homes are stored in a database via Essential’s DB layer, and tab-completion makes it easy to manage named homes.

**Key features**
- Per-player, **named** homes (e.g., `home`, `mine`, `village`)
- **Database-backed** storage (SQLite / MySQL / PostgreSQL supported by Essential)
- Simple commands for **set**, **teleport**, and **delete**
- **Adjustable home limits** per player (`/home limit add|minus`)
- Smart **tab completion** for home names and limit arguments
- Optional config for limits, cooldowns, and behavior (via the engine’s config)

**Source layout (high level)**
- `Home.java` – registers command & bootstraps DB schema
- `command/HomeCommand.java` – handles `/home`, `/home limit`, and CRUD operations
- `command/HomeCommandUtil.java` – utility functions for validation, teleport, and limit handling
- `tabcompleter/HomeTabCompleter.java` – provides name suggestions and limit autocompletion
- `util/HomeConfigUtil.java` – reads optional config values
- `util/db/HomeDB*` – schema + CRUD for homes (SQLite, MySQL, PostgreSQL implementations)
