# Snake Game on the Basys3 Platform

## 1. Objective of the Project
The objective of this laboratory project is to implement the classic Snake game on an FPGA using the advanced features of the [Basys 3 development platform](http://digilent.com/shop/basys-3-amd-artix-7-fpga-trainer-board-recommended-for-introductory-users/). The game utilizes a VGA display for graphical output, push buttons (or a PMOD controller) for game control, and a 7‑segment display for presenting the score and game state.

## 2. System Overview
In the Snake game, the player controls a snake that moves within a grid. The snake grows when it eats food, and the game ends when the snake collides with a wall or with its own body.  

## Main Functions

- VGA output: game field and graphics  
- Real‑time movement and control  
- Score counting  
- Game state management (menu, gameplay, game over)  
- Increasing speed as the game progresses  

# 3. Hardware and Used Features
Basys3 Platform Features:  

✅ VGA interface (640×480 @ 60 Hz)  
✅ 7‑segment display (score / state display)  
✅ Push buttons and switches  
✅ ??PMOD interface (optional joystick or additional controller)??  
✅ 100 MHz system clock

## 4. Architecture and Block Structure
The system is implemented modularly using the following components:  

+---------------------+
| Clock Divider       |
+----------+----------+
           |
+----------v----------+
| Game State FSM      |
+----------+----------+
           |
+----+-----+----+--------------+
|    |          |              |
v    v          v              v
Input  Logic   VGA Controller  Score Counter
