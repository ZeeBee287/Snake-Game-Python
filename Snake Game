#Snake Game
#Enemy Snake competes for food with Player Snake
#Enemy Snake spawns at score of original snake at intervals of 5, for 10 seconds (If score is 5, enemy snake spawns. If score is 10, enemy snake spawns and so on)
#Enemy Snake will spawn again for 10 seconds if original snake is unable to score more than an interval of 5

import tkinter as tk
import random

class SnakeGame:
    def __init__(self, master):
        self.master = master
        self.master.title("Snake Game")
        self.master.geometry("400x460")
        self.master.resizable(False, False)

        self.canvas = tk.Canvas(self.master, bg="black", width=400, height=400)
        self.canvas.pack()

        self.scoreboard = tk.Label(self.master, text="Score: 0", font=("Arial", 16), bg="white", fg="black", padx=10, pady=5)
        self.scoreboard.pack()

        self.countdown_label = tk.Label(self.master, text="", font=("Arial", 16), bg="white", fg="black", padx=10, pady=5)
        self.countdown_label.pack()

        self.snake = [(100, 100), (90, 100), (80, 100)]
        self.direction = "Right"
        self.snake_size = 20

        self.obstacles = self.create_obstacles()
        self.food = self.create_food()

        self.master.bind("<KeyPress>", self.change_direction)

        self.snake_moving = True
        self.score = 0
        self.update_scoreboard()
        self.enemy_snake = []
        self.enemy_direction = None
        self.enemy_start_time = None
        self.update()

    def create_food(self):
        while True:
            x = random.randint(0, 19) * self.snake_size
            y = random.randint(0, 19) * self.snake_size
            food_coords = (x, y, x + self.snake_size, y + self.snake_size)
            if food_coords not in self.obstacles:
                break
        return self.canvas.create_rectangle(food_coords, fill="red", tags="food")

    def create_obstacles(self):
        obstacles = []
        for _ in range(10):
            while True:
                x = random.randint(0, 19) * self.snake_size
                y = random.randint(0, 19) * self.snake_size
                obstacle_coords = (x, y, x + self.snake_size, y + self.snake_size)
                if obstacle_coords not in obstacles:
                    obstacles.append(obstacle_coords)
                    self.canvas.create_rectangle(obstacle_coords, fill="gray", tags="obstacle")
                    break
        return obstacles

    def available_directions(self, head):
        directions = ["Right", "Left", "Up", "Down"]
        available = []
        
        for direction in directions:
            if direction == "Right" and (head[0] + self.snake_size, head[1]) not in self.enemy_snake and (head[0] + self.snake_size, head[1]) not in [obs[:2] for obs in self.obstacles]:
                available.append(direction)
            elif direction == "Left" and (head[0] - self.snake_size, head[1]) not in self.enemy_snake and (head[0] - self.snake_size, head[1]) not in [obs[:2] for obs in self.obstacles]:
                available.append(direction)
            elif direction == "Up" and (head[0], head[1] - self.snake_size) not in self.enemy_snake and (head[0], head[1] - self.snake_size) not in [obs[:2] for obs in self.obstacles]:
                available.append(direction)
            elif direction == "Down" and (head[0], head[1] + self.snake_size) not in self.enemy_snake and (head[0], head[1] + self.snake_size) not in [obs[:2] for obs in self.obstacles]:
                available.append(direction)
        
        return available

    def move_snake(self, snake):
        head = snake[0]
        new_head = None

        if self.direction == "Right":
            new_head = (head[0] + self.snake_size, head[1])
        elif self.direction == "Left":
            new_head = (head[0] - self.snake_size, head[1])
        elif self.direction == "Up":
            new_head = (head[0], head[1] - self.snake_size)
        elif self.direction == "Down":
            new_head = (head[0], head[1] + self.snake_size)

        if (new_head[0] < 0 or new_head[0] >= 400 or 
            new_head[1] < 0 or new_head[1] >= 400 or
            new_head in [obs[:2] for obs in self.obstacles] or
            new_head in snake):
            return False

        snake.insert(0, new_head)
        snake.pop()
        return True

    def create_enemy_snake(self):
        self.enemy_snake = [(300, 300), (310, 300), (320, 300)]
        self.enemy_direction = "Left"
        self.enemy_start_time = self.master.after(10000, self.clear_enemy_snake)
        self.start_countdown(10) 

    def start_countdown(self, seconds):
       self.countdown_label.config(text=f"Countdown: {seconds}")
       if seconds > 0:
           self.countdown_after_id = self.master.after(1000, lambda s=seconds-1: self.start_countdown(s))
       else:
           self.clear_enemy_snake()
           self.countdown_label.config(text="")

    def move_enemy_snake(self):
        enemy_head = self.enemy_snake[0]
        food_coords = self.canvas.coords(self.food)

        directions = self.available_directions(enemy_head)

        if enemy_head[0] < food_coords[0] and "Right" in directions:
            self.enemy_direction = "Right"
        elif enemy_head[0] > food_coords[0] and "Left" in directions:
            self.enemy_direction = "Left"
        elif enemy_head[1] < food_coords[1] and "Down" in directions:
            self.enemy_direction = "Down"
        elif enemy_head[1] > food_coords[1] and "Up" in directions:
            self.enemy_direction = "Up"
        else:
            self.enemy_direction = random.choice(directions)

        new_head = enemy_head
        if self.enemy_direction == "Right":
            new_head = (enemy_head[0] + self.snake_size, enemy_head[1])
        elif self.enemy_direction == "Left":
            new_head = (enemy_head[0] - self.snake_size, enemy_head[1])
        elif self.enemy_direction == "Up":
            new_head = (enemy_head[0], enemy_head[1] - self.snake_size)
        elif self.enemy_direction == "Down":
            new_head = (enemy_head[0], enemy_head[1] + self.snake_size)

        if (new_head[0] < 0 or new_head[0] >= 400 or 
            new_head[1] < 0 or new_head[1] >= 400 or
            new_head in [obs[:2] for obs in self.obstacles] or
            new_head in self.enemy_snake):
            self.clear_enemy_snake()
            return

        self.enemy_snake.insert(0, new_head)
        if self.canvas.coords(self.food) == [new_head[0], new_head[1], new_head[0] + self.snake_size, new_head[1] + self.snake_size]:
            self.canvas.delete("food")
            self.food = self.create_food()
        else:
            self.enemy_snake.pop()

    def clear_enemy_snake(self):
        self.enemy_snake.clear()
        self.enemy_start_time = None
        self.canvas.delete("enemy")
        self.countdown_label.config(text="")

    def update_scoreboard(self):
        self.scoreboard.config(text=f"Score: {self.score}")

    def pause_enemy_snake(self):
        if self.enemy_start_time:
            self.master.after_cancel(self.enemy_start_time)

    def end_game(self):
        self.snake_moving = False
        self.pause_enemy_snake()  
        self.canvas.create_text(200, 200, text="Game Over!", fill="white", font=("Arial", 24))
        if self.countdown_after_id:
            self.master.after_cancel(self.countdown_after_id)
            self.countdown_label.config(text="")

    def update(self):
        snake_moved = self.move_snake(self.snake)
        if not snake_moved:
            self.end_game()

        self.canvas.delete("snake")
        for segment in self.snake:
            self.canvas.create_rectangle(segment[0], segment[1], segment[0] + self.snake_size, segment[1] + self.snake_size, fill="green", tags="snake")

        if self.score % 5 == 0 and self.score != 0 and not self.enemy_snake:
            if self.enemy_start_time is None:
                self.create_enemy_snake()

        if self.enemy_snake:
            self.move_enemy_snake()
            self.canvas.delete("enemy")
            for segment in self.enemy_snake:
                self.canvas.create_rectangle(segment[0], segment[1], segment[0] + self.snake_size, segment[1] + self.snake_size, fill="blue",tags="enemy")

        food_coords = self.canvas.coords(self.food)
        if int(self.snake[0][0]) == food_coords[0] and int(self.snake[0][1]) == food_coords[1]:
            self.snake.append(self.snake[-1])
            self.canvas.delete("food")
            self.food = self.create_food()
            self.score += 1
            self.update_scoreboard()

        if self.snake_moving:
            self.master.after(100, self.update)

    def change_direction(self, event):
        if event.keysym == "Right" and self.direction != "Left":
            self.direction = "Right"
        elif event.keysym == "Left" and self.direction != "Right":
            self.direction = "Left"
        elif event.keysym == "Up" and self.direction != "Down":
            self.direction = "Up"
        elif event.keysym == "Down" and self.direction != "Up":
            self.direction = "Down"

if __name__ == "__main__":
    root = tk.Tk()
    game = SnakeGame(root)
    root.mainloop()
