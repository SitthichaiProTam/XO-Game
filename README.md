# XO Game App

## Overview
The XO Game App is a Kotlin-based Android application that allows users to play Tic-Tac-Toe (XO) with dynamic features such as grid size customization, score tracking, game history, and an AI opponent. The app leverages Jetpack Compose for its UI and SQLite for persistent storage.

---

## Features
- **Dynamic Grid Size**: Play on a customizable grid size (3x3 to 10x10).
- **Score Tracking**: Keeps track of scores for both players (`X` and `O`).
- **AI Opponent**: Includes an AI that makes strategic moves to challenge the player.
- **Game History**: Stores game results with details such as date, winner, and grid state.
- **Responsive Design**: UI scales according to grid size for optimal gameplay experience.
- **Reset and Clear Scores**: Reset the game grid or clear the scores easily.

---

## Project Structure

### 1. **`XOGameApp.kt`**
   - Implements the main UI using Jetpack Compose.
   - Handles grid display, score updates, and game history UI.
   - Interacts with `XOGameViewModel` for logic.

### 2. **`XOGameViewModel.kt`**
   - Contains the game logic and state management.
   - Implements the AI for `O` player.
   - Handles game history storage using `PlayerDatabaseHelper`.

### 3. **`MainActivity.kt`**
   - Entry point of the application.
   - Integrates the `XOGameApp` composable with the ViewModel.

### 4. **`Player.kt`**
   - Defines a `Player` data class with attributes like ID, name, and score.

### 5. **`PlayerDatabaseHelper.kt`**
   - Manages SQLite database operations for storing players and game history.
   - Provides methods to insert and retrieve game records.

---

## Algorithm

### 1. **Player Move**
- Validate if the selected grid cell is empty.
- Update the grid with the current player's symbol (`X` or `O`).
- Switch the turn to the other player.
- Check for a winner or draw.

### 2. **AI Move**
- Check if the grid is full; if yes, terminate the move.
- Find the best possible move using:
  - **Minimax Algorithm**: Evaluate all potential moves for the AI and opponent.
  - Block the opponent's winning moves.
  - Make the move that maximizes the AI's chances of winning.
- Update the grid and check for a winner.

### 3. **Winner Detection**
- Check rows, columns, and diagonals for three consecutive identical symbols.
- If found, declare the player as the winner.
- If the grid is full without a winner, declare a draw.

### 4. **Game History Storage**
- After each game, save the winner, score, grid state, and timestamp to the SQLite database.
- Allow users to retrieve and view the game history.

---

## Requirements

- **Android Studio**: Arctic Fox or newer.
- **Kotlin**: 1.5.21 or newer.
- **Jetpack Compose**: Stable version.

---

## Installation

1. Clone the repository.
   ```bash
   git clone https://github.com/your-repository/XOGameApp.git
   ```

2. Open the project in Android Studio.

3. Sync the Gradle files.

4. Run the app on an emulator or connected Android device.

---

## How to Use

1. Launch the app.
2. Customize the grid size (optional).
3. Click "Start Game" to begin.
4. Take turns making moves until there is a winner or a draw.
5. View the game history by clicking "Show History".
6. Reset or clear scores using the respective buttons.

---

## Database Schema

### Players Table (`players`)
| Column       | Type    | Description                  |
|--------------|---------|------------------------------|
| `id`         | INTEGER | Primary key                 |
| `name`       | TEXT    | Player name                 |
| `score`      | INTEGER | Player score                |
| `is_winner`  | INTEGER | Indicates if the player won |

### History Table (`history`)
| Column       | Type    | Description                  |
|--------------|---------|------------------------------|
| `id`         | INTEGER | Primary key                 |
| `name`       | TEXT    | Winner's name               |
| `score`      | INTEGER | Winner's score              |
| `date`       | TEXT    | Date of the game            |
| `grid`       | TEXT    | Grid state of the game      |

---

## Contribution

Contributions are welcome! Please fork the repository and create a pull request with detailed explanations of your changes.

---

## License
This project is licensed under the MIT License. See the `LICENSE` file for more details.

---

## Acknowledgements
- Jetpack Compose for UI components.
- SQLite for local data storage.
- Android Studio for development environment.

---

**Developed by Big Boom.**

