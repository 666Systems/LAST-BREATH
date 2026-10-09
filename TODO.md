# LAST BREATH: DEVELOPMENT ROADMAP

## Phase 1: Supabase Connection & MCP Configuration (CURRENT)
- [x] Inspect project directory and establish required structure.
- [x] Configure and verify Supabase MCP targeting Project `htljkpajvphinzwzbvhw`.
- [x] Configure environment variables (`.env.local` and `.env.example`).
- [x] Install `@supabase/supabase-js`.
- [x] Create singleton client in `src/lib/supabase.js`.
- [x] Verify client initialization, build integrity, and security check.

---

## Future Phases (Pending Approval)
- [ ] **Phase 2: Database Schema & Room Metadata**
  - Define rooms table with RLS.
  - Implement room creation, listing, and joining RPC/queries.
- [ ] **Phase 3: Canvas Viewport & Game Loop Foundation**
  - Set up 2D Canvas rendering loop with requestAnimationFrame.
  - Pixel-perfect camera & arena boundaries.
- [ ] **Phase 4: Player Movement & Desktop Controls**
  - WASD / Arrow keys input handling.
  - Player sprite & facing direction based on mouse aim.
- [ ] **Phase 5: Shooting & Hitscan Combat**
  - Instant line-of-sight raycasts on mouse click.
  - Muzzle flash and impact particle visual cues.
- [ ] **Phase 6: Zombie AI & Wave Survival System**
  - Basic zombie navigation towards nearest player.
  - Wave manager with scaling spawn count.
- [ ] **Phase 7: Host-Authoritative Multiplayer over Supabase Realtime**
  - Presence tracking for players in a room (2-4 players).
  - Broadcast input and snapshot state synchronization.
- [ ] **Phase 8: Revive System & Health States**
  - Downed state trigger ("Last Breath") on 0 HP.
  - Teammate proximity revive interaction.
- [ ] **Phase 9: Polish, HUD, & Vercel Deployment**
  - Retro pixel-art HUD, ammo/HP bars, wave indicators.
  - Production build verification and deployment.
