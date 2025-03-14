# 🐍 Snake Game with Enemy AI

## 📌 Overview
This is a classic **Snake Game** built using Python and Tkinter, with an added twist—an **enemy snake** that competes for food. The enemy snake spawns based on the player’s score and remains active for a limited time, making the game more challenging!

## ✨ Features
- 🎮 **Classic Snake Gameplay** – Navigate the snake to collect food and grow.
- 🆚 **Enemy Snake AI** – Spawns every **5 points** and competes for food.
- 🚧 **Obstacle Generation** – Random obstacles appear on the grid.
- ⏳ **Enemy Snake Timer** – Stays active for **10 seconds** before disappearing.
- 📊 **Real-Time Score Tracking** – Score updates dynamically.
- 💥 **Game Over Conditions** – The game ends if the player:
  - Collides with an obstacle.
  - Crashes into the enemy snake.
  - Hits the screen boundary.
- 🛠️ **Game Area Customization** – Players can select a game area with obstacle placements that best suit their playstyle before restarting.

## 🎮 Gameplay Mechanics

### 1️⃣ **Starting the Game**  
- The game begins on a static screen.  
- Press **any key** to start playing.

### 2️⃣ **Controls**  
- Use **Arrow Keys** (⬆️⬇️⬅️➡️) to move the snake.
- The goal is to **eat food** and grow in size.

### 3️⃣ **Food Collection & Enemy Snake Behavior**  
- Each food item increases the player's score.
- When the score reaches a **multiple of 5** (5, 10, 15...), an **enemy snake spawns** for **10 seconds**.
- A **countdown starts from 10**, and the enemy competes for food.
- If the score remains at a multiple of 5 without further increase, the enemy snake **respawns**.

### 4️⃣ **Collision Detection & Game Over**  
- The game ends if the player:
  - Collides with an obstacle.
  - Hits the enemy snake.
  - Crashes into the screen boundary.
- The snake cannot reverse direction instantly (e.g., moving left cannot immediately switch to right).

### 5️⃣ **Restarting & Game Area Selection**  
- After losing, press **Space** to restart.
- Keep pressing **Space** to **generate a new game area** with different obstacle placements before starting again.

## 🚀 Installation & Running the Game
### Prerequisites
- Python 3.x
- Tkinter (pre-installed with Python)

## 🔮 Future Improvements
This is just a basic snake game—there’s so much potential for enhancement!
- 🎨 **Enhanced Graphics** – Improve game visuals.
- 🔊 **Sound Effects** – Add audio for actions and collisions.
- 🎭 **Different Game Levels** – Implement structured levels instead of random obstacles.
- ⚙️ **Difficulty Settings** – Adjust enemy snake speed.
- 🏆 **Leaderboard** – Track and display high scores.
- 💥 **Power-ups** – Introduce special abilities for the player.

And much more! 🎉

---
Enjoy playing the game! 🐍🎮

