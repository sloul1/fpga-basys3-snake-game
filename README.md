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

``` 
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
```
## Key Modules

- VGA Controller
- Game FSM
- Snake Logic
- Collision Detection
- Score Counter
- Input Handler

A modular architecture improves testability and system reliability.

## 5. VGA Graphics Implementation
Resolution and Structure

VGA 640×480, 60 Hz
The game field is divided into a grid (e.g., 40×30 cells)
Each cell is rendered at an enlarged size (e.g., 16×16 pixels)

Displayed Elements

Background
Snake head and body
Food
Game state text (Start, Game Over)

The VGA controller generates HSYNC and VSYNC signals and RGB color data on a per‑pixel basis.

## 6. Game Logic
Game States (FSM)

INIT – waiting for user input
PLAY – game running
PAUSE – paused state
GAME OVER – collision detected

State transitions are documented with a state diagram.
Snake Structure

The snake is modeled as an array of (x, y) coordinates
Maximum length is predefined
Movement occurs at a fixed interval (game clock)

Food

Pseudo‑random position generation
Must not appear on top of the snake
An LFSR‑based implementation may be used for randomness

## 7. Control
Inputs

Push buttons: up / down / left / right
Alternatively, a PMOD joystick

Reliability

Push button debouncing
Immediate reversal of direction is prevented

## 8. Scoring and 7‑Segment Display


Score increases when food is eaten


7‑segment display:

shows the current score
displays “END” in the Game Over state



Display multiplexing is used

## 9. Reliability and Error Handling
System reliability is ensured through the following measures:

Clear clock signals controlling game timing
Safe and well‑defined state transitions
Handling of edge cases (walls, maximum snake length)
All counters are range‑limited to prevent overflow

The documentation discusses how error conditions are identified and prevented.

## 10. Testing
Testing Methods

Unit testing (simulation)
Manual testing on the FPGA
Edge cases:

maximum snake length
rapid direction changes
collisions



Test Documentation

Test case → expected result → observed result


## 11. Extensions
Possible additional features include:

Speed increase based on score
Two‑player mode
Session‑based high score
Sound via a PMOD Audio module
Visual animation in the Game Over state


## 12. Documentation
The documentation includes:

- Introduction and objectives
- System specification
- Architecture and block diagrams
- Game logic and state machines
- VGA implementation
- Reliability solutions
- Testing and results
- Conclusions and future development?
