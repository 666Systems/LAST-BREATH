# GAME DESIGN DOCUMENT: LAST BREATH

## 1. Overview
* **Title:** Last Breath
* **Genre:** 2D Top-Down Shooter Wave Survival
* **Theme:** Zombie Apocalypse
* **Visual Style:** 2D Pixel Art
* **Platform:** Web (Desktop Browser)

## 2. Core Gameplay
* **Objective:** Players must survive increasingly difficult waves of zombies in a compact arena, working together to keep each other alive.
* **Movement & Controls:**
  * Movement: `W`, `A`, `S`, `D` or Arrow Keys.
  * Aiming: Mouse cursor direction.
  * Shooting: Left Mouse Click (Hitscan ray-casting, instant hit check, no slow projectiles).
* **Survival & Teamwork:**
  * When a player's HP reaches 0, they enter a downed state ("Last Breath").
  * Active teammates can revive downed players by standing near them and interacting.
  * Game Over occurs when all players in the room are downed.

## 3. Multiplayer Design
* **Room-Based Matchmaking:**
  * Rooms support 2 to 4 players.
  * Guest Mode: No compulsory registration or login; players join using an alias/guest ID.
  * Compact single arena map.

## 4. MVP Scope
* **Characters:** 1 default playable survivor character.
* **Weapons:** 1 standard firearm (hitscan rifle/pistol).
* **Enemies:** 1 basic zombie type (melee pathfinding towards nearest living player).
* **Game Loop:** Wave survival (wave counter, zombie count per wave, revive mechanic).
