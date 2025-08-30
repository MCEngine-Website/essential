# Introduction

[`Repository`](https://github.com/MCEngine-Extension/essential-addon-vault)
[`GitHub Release`](https://github.com/MCEngine-Extension/essential-addon-vault/releases)

**Essential Vault** is an AddOn that provides a personal, database-backed storage (“vault”) for every player.  
It preserves full Bukkit `ItemStack` metadata (enchantments, custom names, NBT, etc.) so items round-trip exactly as placed.

**Key features**
- Per-player vault (default 6 rows / 54 slots)
- Full item metadata/NBT persistence
- Save-on-close behavior (no commands needed to save)
- Works with SQLite/MySQL/PostgreSQL via Essential’s DB layer
- Simple permission gating for opening the vault

Use `/vault` (or `/vault open`) to access your storage. Close the inventory to save automatically.
