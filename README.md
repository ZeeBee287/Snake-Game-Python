# Snake Game with Enemy AI

## Overview
This is a classic **Snake Game** built using Python and Tkinter. The game features an **enemy snake** that competes with the player for food. The enemy snake spawns based on the player's score and remains active for a limited time.

## Features
- **Classic Snake Gameplay**: Move the snake around the grid to collect food.
- **Enemy Snake AI**: The enemy snake appears at intervals of **5 points** and competes for food.
- **Obstacle Generation**: Random obstacles are placed on the grid.
- **Countdown Timer for Enemy Snake**: The enemy snake stays for **10 seconds** before disappearing.
- **Score Tracking**: The scoreboard updates in real-time.
- **Game Over Condition**: The game ends if the player collides with obstacles, the enemy snake, or the screen boundaries.
- **Game Play Setting**: Players can choose the game area where they want to start their new game. After *Game Over*, they can press *Space* to restart, but this time, they get to *select the game area* where the obstacles are placed in a way that best suits their playstyle. Once the area is chosen, they can press any key to begin the game.

## Gameplay Mechanics
1. **Player Controls**: Use the arrow keys (**Up, Down, Left, Right**) to control the snake.
2. **Food Collection**: Eating food increases the player's score.
3. **Enemy Snake Spawn Rule**:
   - The enemy snake appears when the score reaches **multiples of 5**.
   - It stays on the screen for **10 seconds**.
   - If the player does not increase their score by another 5 points, the enemy snake respawns.
4. **Collision Detection**:
   - Hitting the screen boundary or an obstacle ends the game.
   - The player cannot move in the opposite direction instantly.

## Installation & Running the Game
### Prerequisites
- Python 3.x
- Tkinter (comes pre-installed with Python)

## Future Improvements
This is a basic snake game with plenty of room for enhancements! Here are some ideas for future improvements:

- **Improve game graphics** for a more polished look.
- **Add sounds** to enhance gameplay experience.
- **Introduce different levels** instead of just randomly placed obstacles.
- **Implement a difficulty setting** to control enemy snake speed.
- **Add a leaderboard** to track high scores.
- **Include power-ups** for special abilities and extra fun!

And so much more! Happy coding, guys! 😃

---

Enjoy playing the game! 🐍🎮

