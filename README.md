## About the Project

This is a low-level implementation of the classic Breakout-style game built entirely in **x86 Assembly (8086)** and running inside **DOSBox**.
The goal was to build everything from scratch using BIOS interrupts and direct video memory.

It includes:

* A full menu system
* Game loop and physics
* Mouse-based paddle control
* Sound effects using PC speaker
* Multi-level gameplay with increasing complexity


## How to Run

### Requirements

* DOSBox (0.74 or newer)
* NASM (for assembling)

### Steps

1. Assemble the code:

   ```bash
   nasm game.asm -o game.com
   ```

2. Open DOSBox and mount your folder:

   ```bash
   mount c .
   c:
   ```

3. Run the game:

   ```bash
   game.com
   ```


## Controls

* **Mouse / Trackpad** → Move paddle
* **ESC** → Exit game / go back
* **Menu Keys**:

  * `1` → Start Game
  * `2` → Instructions
  * `3` → Exit


## Gameplay

* Break all bricks using the ball
* Don’t let the ball fall below the paddle
* You have **3 lives**

### Level System

**Level 1**

* 4 rows of bricks
* Basic gameplay

**Level 2**

* 5 rows of bricks
* Includes falling objects (drops)


## Special Mechanics

* **Green `$` drop**

  * Catch it → +20 score

* **Red `#` drop**

  * Catch it → Lose 1 life

## Features

* Text-mode graphics using video memory (`0xB800`)
* Real-time paddle control via mouse interrupt (`int 0x33`)
* Sound effects using PC speaker
* Collision detection (walls, paddle, bricks)
* Dynamic ball angles based on paddle hit position
* Multi-level progression
* Drop system with randomized effects
* Clean screen transitions and UI

## Technical Highlights

* Direct hardware interaction (ports + interrupts)
* Custom rendering system (no BIOS graphics mode)
* Efficient memory usage with arrays for:

  * Bricks
  * Drops
  * Game state
* Timing control using software delays

## Notes

* Designed for **DOSBox**, may not run correctly on modern systems directly
* Resolution is fixed to text mode (80x25)
* Timing depends on DOSBox CPU cycles
