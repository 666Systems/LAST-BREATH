# ARCHITECTURE DOCUMENT: LAST BREATH

## 1. Technology Stack
* **Framework:** Next.js (App Router, JavaScript)
* **Backend Database:** Supabase PostgreSQL (Project ID: `htljkpajvphinzwzbvhw`)
* **Realtime Networking:** Supabase Realtime Channels (Presence & Broadcast)
* **Styling:** Vanilla CSS / CSS Modules
* **Deployment Target:** Vercel + Supabase Cloud

## 2. Multiplayer Architecture (Host-Authoritative)
For a lightweight browser prototype, the game uses a **Host-Authoritative** model:
* **Host Role:** One client browser acts as the match host. The host is responsible for:
  * Simulating zombie spawns and AI movements.
  * Validating hitscan hits and dealing damage to enemies/players.
  * Managing player HP, downed states, revives, waves, and score.
  * Broadcasting authoritative game state snapshots via Supabase Realtime Broadcast.
* **Peer/Client Role:**
  * Captures local player input (WASD, mouse aim angle, shooting triggers).
  * Sends player inputs and presence to the host via Supabase Realtime.
  * Renders authoritative state updates received from the host.
* **Database Role:**
  * Supabase Database stores persistent metadata: room codes, room status, match results, and leaderboard stats.
  * High-frequency per-frame state is NOT persisted to PostgreSQL; it flows purely through Supabase Realtime Broadcast channels.

## 3. Code Organization & Modularity
The codebase enforces clear separation of concerns:
```
src/
├── app/                  # Next.js App Router pages and layouts
├── lib/
│   └── supabase.js       # Reusable Supabase client singleton
├── game/                 # Game domain modules (to be implemented in future phases)
│   ├── rendering/        # Canvas 2D viewport, sprite rendering
│   ├── input/            # Keyboard & mouse event listeners
│   ├── state/            # Game state container & loop
│   ├── combat/           # Hitscan calculations and damage logic
│   ├── ai/               # Zombie pathfinding and behavior
│   ├── multiplayer/      # Supabase Realtime channel handlers (host/client sync)
│   └── ui/               # HUD overlay, lobby, room browser
```

## 4. Security & Credentials
* Only the **Publishable Key** (`NEXT_PUBLIC_SUPABASE_PUBLISHABLE_KEY`) is used on the client.
* No service_role key, database password, or secret tokens are stored in the client or committed to Git.
* Database tables will strictly enforce Row Level Security (RLS) in future phases.
