# Introduction

[`Repository`](https://github.com/MCEngine-Extension/essential-addon-fly)
[`GitHub Release`](https://github.com/MCEngine-Extension/essential-addon-fly/releases)

**Essential Fly** is an AddOn that provides per-player timed flight support.  
It integrates with Essential’s DB layer to persist remaining flight durations and enforces them automatically.

**Key features**
- Per-player flight time tracking (stored in DB)
- Auto-decrement every 30s only while flying
- Automatic disable on quit/kick (no offline decrement)
- Admin command to grant additional flight time
- Works with SQLite/MySQL/PostgreSQL

Use `/fly` (or `/fly on`) to enable flight if you have time.  
Disable with `/fly off` or when your time runs out.
