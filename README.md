<div align="center">

# ⚽ Clash of Boots

**A physics-based, turn-taking tabletop football game for the browser.**

Flick your players, blast the ball, collect mystery power-ups, and knock it past your rival to be crowned champion.

Built with **HTML5, CSS3, vanilla JavaScript**, and the **Matter.js** physics engine.

</div>

---

## 📖 Table of Contents

- [About the Game](#-about-the-game)
- [Features](#-features)
- [Gameplay](#-gameplay)
  - [Controls](#controls)
  - [Turns & Scoring](#turns--scoring)
  - [Formations](#formations)
  - [Power-Ups](#power-ups)
- [Screens & Flow](#-screens--flow)
- [Tech Stack](#-tech-stack)
- [Project Structure](#-project-structure)
- [Getting Started](#-getting-started)
- [Audio](#-audio)
- [Roadmap Ideas](#-roadmap-ideas)
- [Credits](#-credits)
- [License](#-license)

---

## 🎮 About the Game

**Clash of Boots** is a two-player, same-device football (soccer) game inspired by tabletop "finger football." Instead of controlling a single character in real time, each player takes turns **dragging and flicking** one of their five on-field players into the ball, using realistic physics-driven momentum to line up shots, passes, and blocks.

The game is fully turn-based: aim, release, and watch physics take over as players and the ball bounce, collide, and (hopefully) find the back of the net.

##  Features

-  **Turn-based physics gameplay** powered by [Matter.js](https://brm.io/matter-js/), with drag-to-aim and release-to-shoot controls
-  **Custom player names** — enter names for Player 1 (red) and Player 2 (blue) before kickoff
-  **Selectable match length** — first to 1, 3, or 5 goals
-  **Dynamic formations** — teams line up in 2-2, 1-2-1, or 3-1 shapes, and formations shuffle automatically after every goal
-  **Mystery box power-ups** that spawn mid-match:
  -  **Speed Boost** — triples shot power and drag sensitivity
  -  **Giant Player** — enlarges and empowers a player for a heavyweight collision
  -  **Slow Opponent** — hampers the rival team's next move
-  **Goal celebrations** with animated confetti bursts
-  **Victory screen** with a "Play Again" (same players) or "Exit to Menu" option
-  **Pause menu** — pause/resume or restart mid-match, accessible via a button or the `Esc` key
-  **Full audio system** — background music per screen, sound effects for clicks, goals, pauses, power-ups, and victory, with independently toggleable music/SFX controls
-  **Touch support** — playable on both desktop (mouse) and mobile (touch) devices
-  **Animated UI** — GSAP-powered title and VS-screen animations

##  Gameplay

### Controls

| Action | Input |
|---|---|
| Select a player | Click / tap and hold one of **your team's** players |
| Aim a shot | Drag away from the player (further = more power) |
| Take the shot | Release the mouse / lift your finger |
| Pause the game | Click the pause icon or press `Esc` |

You may only move players belonging to the team whose turn it currently is, and only one shot may be taken per turn.

### Turns & Scoring

- The match always kicks off with **Red's turn**, alternating after each shot.
- Match length is chosen on the Game Mode screen: first to **1**, **3**, or **5** goals wins.
- When the ball crosses into a goal sensor, a goal is awarded, a confetti celebration plays, and the scoring team's opponent is given the next turn after positions reset.
- Reaching the target goal count ends the match and routes players to the **Victory** screen.

### Formations

Before kickoff, both teams line up in the **2-2 Square** formation. After every goal, the game automatically reshuffles both teams into a new random formation to keep matches varied:

| Formation | Description |
|---|---|
| **2-2 Square** | Balanced spread across two lines |
| **1-2-1 Diamond** | A central playmaker with wide flanks |
| **3-1 Defensive** | Packed defensive line with a lone attacker |

### Power-Ups

A **Mystery Box** occasionally spawns on the pitch. Whichever team's player touches it first receives a random power-up (the pool rotates so you won't get the same effect twice in a row):

| Power-Up | Effect |
|---|---|
|  Speed Boost | Dramatically increases the force and sensitivity of your next shot |
|  Giant Player | Scales up a chosen player's size and mass for powerful collisions |
|  Slow Opponent | Reduces the effectiveness of the opposing team's next move |

## 🖥️ Screens & Flow

```
index.html  →  player.html  →  gamemode.html  →  futsal.html  →  victory.html
(Start Menu)   (Name Entry)     (Match Length)    (Main Game)     (Winner Screen)
```

1. **Start Menu (`index.html`)** — Animated logo and "Enter" button to begin.
2. **Player Setup (`player.html`)** — Enter custom names for Player 1 and Player 2 (defaults are used if left blank); names are stored via `localStorage`.
3. **Game Mode (`gamemode.html`)** — Choose the match length: first to 1, 3, or 5 goals.
4. **Match (`futsal.html`)** — The main physics-based football pitch where the match is played, including score display, pause menu, and power-up system.
5. **Victory (`victory.html`)** — Displays the winning player's name with a celebratory animation, and lets you replay with the same players or return to the start menu.

Every screen features persistent **music and sound-effect toggle controls** in the top corner.

##  Tech Stack

- **HTML5 / CSS3** — structure and styling for each screen
- **Vanilla JavaScript** — game state, input handling, and UI logic
- **[Matter.js](https://brm.io/matter-js/)** (via CDN) — 2D rigid-body physics engine driving player/ball movement, collisions, and goal detection
- **[GSAP](https://greensock.com/gsap/)** (via CDN) — animations for menu titles and transitions
- **[Font Awesome](https://fontawesome.com/)** (via CDN) — icons for audio and menu controls
- **Web Audio (`<audio>` / JS Audio API)** — custom music manager for background tracks and sound effects
- **`localStorage`** — lightweight persistence of player names and match state between pages

No build tools, bundlers, or backend are required — it's a fully static, client-side site.

## 📁 Project Structure

```
Clash-Of-Boots--main/
├── index.html          # Start / landing screen
├── player.html         # Player name entry screen
├── gamemode.html       # Match length selection screen
├── futsal.html         # Main gameplay screen
├── victory.html        # Post-match winner screen
│
├── start.css           # Styles for the start screen
├── player.css          # Styles for the player entry screen
├── gamemode.css        # Styles for the game mode screen
├── futsal.css          # Styles for the main game screen
├── victory.css         # Styles for the victory screen
│
├── futsal.js           # Core game engine: physics, input, turns, scoring, power-ups
├── music.js            # Global music/SFX manager shared across all screens
│
├── img/                # Sprites, backgrounds, logos, and UI art
├── audio/              # Music tracks and sound effects (goal, click, pause, victory, etc.)
└── popper.gif          # Victory screen celebration animation
```

## 🚀 Getting Started
Play instantly (no setup required)
The game is already deployed and ready to play in your browser ; no installation needed:

- **Vercel:** [cob-xi.vercel.app](https://cob-xi.vercel.app/)
- **GitHub Pages:** [luzza-bmp.github.io/Clash-Of-Boots-](https://luzza-bmp.github.io/Clash-Of-Boots-/)

## Audio

Each screen includes independent toggle buttons for:

-  **Music** — background tracks appropriate to each screen (menu, in-game, post-match)
-  **Sound Effects** — clicks, goals, pause/unpause, mystery box, and victory stings

All audio is managed centrally via `music.js`, which persists mute/unmute preferences as players navigate between screens.

##  Roadmap Ideas

Some possible directions for future development:

- [ ] Online multiplayer support
- [ ] Additional formations and customizable team colors/kits
- [ ] AI-controlled opponent for single-player mode
- [ ] Match history / stats tracking
- [ ] Additional power-ups and pitch hazards
- [ ] Mobile-first responsive layout improvements

##  Credits

Built with:
- [Matter.js](https://brm.io/matter-js/) — physics engine
- [GSAP](https://greensock.com/gsap/) — animation library
- [Font Awesome](https://fontawesome.com/) — iconography

##  License

No license has been specified for this project yet. If you intend to share or accept contributions to this repository, consider adding a `LICENSE` file (e.g., MIT) to clarify usage rights.

---

<div align="center">

Made for football fans who'd rather flick than dribble. ⚽

</div>

