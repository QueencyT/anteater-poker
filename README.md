# Anteater Poker

## Overview

Anteater Poker is a multiplayer Texas Hold'em-inspired poker game developed in C, featuring a client-server architecture, TCP socket networking, and graphical interfaces built with GTK3.

The game enables multiple players to connect to a centralized server and compete in real-time poker matches. The server manages game logic, betting rounds, player actions, and shared game state, while graphical clients provide an interactive gameplay experience. The game also introduces a custom Anteater wildcard mechanic and AI-controlled opponents with different decision-making strategies. When in the hand, the anteater card acts as a wildcard. When among the community cards, it reveals all community cards and advances the game to its final round. 

Developed collaboratively by a six-member team, the project integrates network programming, graphical application development, and game-state management into a functional multiplayer application. 

**Team-Members:**

- **Queency Tan** 
- **Austin Nguyen**
- **Mia Ness**
- **Aman**
- **Gurvin Singh**
- **Naveen Islame**
---
## My Contributions

As a member of the six-person development team, I was primarily responsible for GUI development, client-side networking, and system integration.

### Graphical User Interface Development

- Developed the GTK3 client-side interface for interactive multiplayer poker gameplay.
- Designed and implemented the rendering modules and logic for cards, players, betting information, real-time game-state visualization, and responsive GUI scaling to dynamically adapt interface elements to different window sizes and screen resolutions.

### Client-Side Networking

- Implemented TCP socket connections to establish communication between graphical clients and the multiplayer server.
- Integrated socket communication with GTK application initialization and multiplayer lobby functionality.
- Implemented connection error handling and resource cleanup.

### Code Integration

- Integrating independently developed modules into the main codebase.
- Coordinating compatibility between the GUI, networking, and gameplay components.
- Resolving integration conflicts and debugging issues between interconnected modules.


---

## Lobby Showcase 
https://github.com/user-attachments/assets/9dc816eb-5ad8-4530-9742-6994c38f6e4f

A custom multiplayer lobby featuring password-protected access, customizable usernames, and a waiting room that displays connected players before the game begins. 

---

## Gameplay Showcase
https://github.com/user-attachments/assets/3430ed9f-4267-4984-9786-c07f0e478519

Anteater Poker allows players to compete in multiplayer Texas Hold'em matches against other players and AI-controlled opponents, featuring strategic betting, custom Anteater card mechanics, and real-time gameplay. The gameplay interface features a dynamically scaling poker table with interactive betting controls, player avatars, chip balances, community cards, and real-time game-state updates.

---

## Server-Side Game State Monitor UI
<img width="1280" height="763" alt="Image" src="https://github.com/user-attachments/assets/e56a2a83-5a63-4a94-8d6b-a156be13a8bc" />
A custom server-side interface providing a real-time overview of the game state, displaying player information, chip balances, betting activity, community cards, and individual player hands.

---

## Key Features

- **Multiplayer Networking:** Supports multiple players connecting to a centralized server over TCP sockets.
- **Client-Server Architecture:** Separates authoritative game logic from player-facing graphical clients.
- **GTK3 Graphical Interface:** Displays player cards, community cards, chip counts, betting information, and game controls.
- **Real-Time Game Synchronization:** Communicates player actions and game-state updates between the server and connected clients.
- **Automated Opponents:** Includes poker bots with different decision-making strategies to fill unoccupied player seats.
- **Custom Game Mechanics:** Introduces an Anteater wildcard with special behavior that modifies traditional Texas Hold'em gameplay.
- **Interactive Lobby:** Supports player names, password-protected entry, and multiplayer game initialization.
- **Betting and Turn Management:** Handles poker actions, betting rounds, and player turn progression.

---

## System Architecture

The project follows a client-server architecture, separating multiplayer communication, game logic, graphical rendering, and automated player behavior.

### 1. <ins>Server-Side Game Management</ins>

The server coordinates multiplayer sessions and maintains the authoritative game state.

Its responsibilities include:

- Managing connected players and game initialization.
- Processing incoming player actions.
- Enforcing gameplay rules and betting progression.
- Tracking player chips, the pot, and round information.
- Broadcasting updated game states to connected clients.

By centralizing game-state management, the server provides a shared source of truth for all players.

### 2. <ins>TCP Socket Communication</ins>

The networking layer enables communication between the server and individual clients using TCP sockets.

Clients transmit gameplay actions to the server, while the server distributes relevant game-state updates.

The project uses communication and protocol components to exchange structured gameplay information between connected processes.

This architecture allows multiple clients to interact with the same game session over a network.

### 3. <ins>GTK3 Graphical Interface</ins>

The graphical client is implemented using GTK3 and custom rendering components.

The interface displays the poker table, player information, cards, betting controls, and other gameplay elements.

The GUI also incorporates graphical assets, custom fonts, and player avatars to provide a more complete interactive experience.

### 4. <ins>Poker Game Logic</ins>

The game logic is separated into reusable components responsible for cards, decks, players, hand evaluation, and gameplay rules.

These components manage:

- Card generation and deck operations.
- Player information and chip balances.
- Betting actions and round progression.
- Hand evaluation and game outcomes.
- Game-state transitions.

This modular design separates the core game mechanics from the networking and graphical layers.

### 5. <ins>AI-Controlled Opponents</ins>

The game includes automated opponents that can participate when player seats are unoccupied.

Bot decision-making evaluates game conditions such as hand strength, betting costs, and potential draws to determine gameplay actions.

The project also includes Monte Carlo-related functionality for poker-hand analysis.

These components allow the game to support automated participation alongside human players.

---

## Core Components

The application is organized into reusable C modules.

| Component | Responsibility |
|-----------|----------------|
| `server` | Manages network connections and server-side gameplay |
| `communication` | Handles network communication between processes |
| `poker_protocol` | Defines and processes gameplay communication messages |
| `state_protocol` | Supports transmission of game-state information |
| `game` | Implements core poker gameplay and progression |
| `state` | Maintains shared game-state information |
| `player` | Manages player information and actions |
| `card` / `deck` / `hand` | Implements cards, decks, and hand evaluation |
| `rules` | Defines poker gameplay and rule evaluation |
| `gui` / `render` | Implements the graphical interface and rendering |
| `lobby` | Manages multiplayer lobby functionality |
| `bot` | Implements automated player decision-making |
| `monte_carlo` | Provides simulation-based poker analysis |

---

## Build and Run

### Requirements

The project is designed for Linux and requires:

- GCC
- GNU Make
- GTK+ 3 development libraries
- Fontconfig development libraries

### 1. Clone the Repository

```bash
git clone https://github.com/QueencyT/anteater-poker.git
cd anteater-poker
```

### 2. Compile the Project

```bash
make
```

This builds the server and graphical client executables:

```text
bin/poker_server
bin/poker_client
```

### 3. Start the Server

Open a terminal and run:

```bash
make run-server PORT=10215
```

### 4. Connect a Client

Open another terminal and run:

```bash
make run-client HOST=localhost PORT=10215
```

To connect from another computer, replace `localhost` with the server's hostname or IP address.

Additional players can connect by running separate clients.

The game can fill remaining player seats with automated opponents.

---

## Testing

The project includes automated tests covering communication protocols and core gameplay components.

Run the complete automated test suite:

```bash
make test
```

Run communication tests:

```bash
make test-comm
```

Run unit tests:

```bash
make test-unit
```

Individual tests are available for components including cards, decks, hands, players, game state, rules, bot behavior, and communication protocols.

---

## Project Structure

```text
anteaterPoker/
├── doc/               # Software specification and user manual
├── include/           # Header files and interface declarations
├── resources/         # Cards, avatars, fonts, and GUI assets
├── src/               # Application source code
├── tests/             # Unit and communication tests
├── Makefile           # Build and testing automation
├── INSTALL            # Installation instructions
└── README             # Original project documentation
```

---

## Project Information

**Project:** Anteater Poker  
**Language:** C  
**GUI Framework:** GTK3  
**Networking:** TCP Sockets  
**Platform:** Linux  
**Course:** EECS 22L, University of California, Irvine  
**Team:** Team 21

### Contributors

Anteater Poker was developed collaboratively by Team 21.

The original project repository and complete team contribution history are available at [NguyenDAustin/anteaterPoker](https://github.com/NguyenDAustin/anteaterPoker).

**Portfolio maintained by:** Queency Tan (`QueencyT`, formerly `qatan-glitch`)
