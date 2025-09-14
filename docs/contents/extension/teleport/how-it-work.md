# How It Works

## Lifecycle
1. **Enable**
   - `Teleport.java` runs when the addon loads
   - Registers permissions dynamically (`essential.teleport.tp`, `essential.teleport.tpa`)
   - Instantiates `TeleportCache` with expiry callback
   - Registers `/tp`, `/tpa`, `/tpaccept` commands and the listener

2. **Commands**
   - **`/tp <player>`**  
     - Requires `essential.teleport.tp` (default OP)  
     - Instantly teleports sender → target
   - **`/tpa <player>`**  
     - Requires `essential.teleport.tpa` (default everyone)  
     - Sends request → target must `/tpaccept`  
     - Request expires in **30s** if ignored
   - **`/tpaccept`**  
     - Accepts the pending `/tpa` request  
     - Teleports requester → target after **4s** warmup

3. **Tab Completion**
   - For `/tp` and `/tpa`, suggests online player names
   - No arguments for `/tpaccept`

4. **Request Handling**
   - `TeleportCache` stores pending requests in memory
   - Each target can only have one active request at a time
   - On expiry (30s), both players are notified
   - On `/tpaccept`, request is removed and teleport scheduled
   - On player quit, requests are cleared by `TeleportListener`

## Permissions
- `essential.teleport.tp` → instant teleport (`/tp`), default **OP**
- `essential.teleport.tpa` → request teleport (`/tpa`, `/tpaccept`), default **all players**

## Data & Safety
- No DB required; cache is in memory
- Requests expire automatically, preventing spam build-up
- Admins can adjust code constants to tweak:
  - **Expiry** (default 30s → 600 ticks)
  - **Warmup delay** (default 4s → 80 ticks)

**Summary:**  
Essential Teleport provides a simple, reliable teleport system for players. `/tp` gives operators instant teleportation, while `/tpa` + `/tpaccept` offers safe, request-based teleports with automatic expiry and warmup delay—implemented with a dedicated cache and model for clean lifecycle management.
