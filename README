# Anteater Poker

## Overview

Anteater Poker is a multiplayer Texas Hold'em-inspired poker game developed in C, featuring a client-server architecture, TCP socket networking, and a graphical interface built with GTK3.

The game allows multiple players to connect to a centralized server and compete in real-time poker matches. The server manages game logic, player actions, betting rounds, and shared game state, while graphical clients provide an interactive interface for gameplay.

The project also introduces a custom Anteater wildcard mechanic and AI-controlled opponents, combining network programming, graphical application development, and game-state management into a multiplayer application.

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

## Gameplay

Anteater Poker follows a variation of Texas Hold'em in which players compete to form the strongest poker hand.

Players connect to a hosted game, receive cards, and participate in betting rounds using actions such as:

- **Fold:** Leave the current hand.
- **Check:** Continue without placing an additional bet when permitted.
- **Call:** Match the current bet.
- **Bet:** Place a wager.
- **Raise:** Increase the current bet.
- **All-In:** Commit all remaining chips.

### Custom Anteater Card

The game introduces a special Anteater card that changes traditional gameplay:

- **In a player's hand:** Acts as a wildcard.
- **Among the community cards:** Replaces the community cards and advances the game to its final round.

These mechanics introduce additional strategic considerations beyond standard Texas Hold'em.

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
| `timer` | Supports gameplay timing functionality |

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
