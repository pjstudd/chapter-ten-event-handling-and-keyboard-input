# Chapter 10: Event Handling and Keyboard Input (Pygame)

## Overview
This chapter explains how **event handling** works in Pygame and how keyboard input can be used to control objects in a game. You will learn how events are processed, how to detect key presses, how to move a player using arrow keys, and how to properly exit a game.

---

## Objectives
- Understand how the event system works in Pygame.
- Learn how to handle keyboard inputs.
- Create basic player movement using arrow keys.
- Properly close a Pygame application.

---

## 10.1 Understanding Events and the Event Queue

### Discussion
In Pygame, **events** are actions that happen during the program, such as:
- Pressing a key
- Moving the mouse
- Closing the window

These events are stored in something called the **event queue**. The program continuously checks this queue inside the game loop to respond to user actions.

If events are not handled properly, the application may freeze or become unresponsive.

### Key Idea
- The game loop must always process events.
- Each event has a specific **type** (e.g., quit, key press).

---

## 10.2 Handling Keyboard Inputs (KEYDOWN, KEYUP)

### Discussion
Pygame detects keyboard input using event types such as:
- **KEYDOWN** → triggered when a key is pressed
- **KEYUP** → triggered when a key is released

These events allow you to respond to user input, such as moving a character or triggering an action.

### Key Idea
- Use KEYDOWN for actions when a key is pressed.
- Use KEYUP for actions when a key is released.

---

## 10.3 Basic Player Movement using Arrow Keys

### Discussion
Player movement is done by updating the position of an object (e.g., a rectangle or image) when arrow keys are pressed.

Each key corresponds to a direction:
- Up Arrow → move up
- Down Arrow → move down
- Left Arrow → move left
- Right Arrow → move right

The movement happens inside the game loop so the position updates continuously.

---

## 10.4 Exiting the Game Properly

### Discussion
A Pygame program must include a way to exit properly. This is done by detecting when the user clicks the close button of the window.

Failing to handle this event may cause the program to hang or not close correctly.

### Key Idea
- Always listen for the quit event.
- Stop the game loop before closing the program.

---

## Example: Event Handling and Player Movement

Below is a simple example that demonstrates:
- Event handling
- Keyboard input
- Player movement
- Proper exit

```python
import pygame
import sys

pygame.init()

# Window setup
screen = pygame.display.set_mode((800, 600))
pygame.display.set_caption("Event Handling Example")

# Player setup
player = pygame.Rect(375, 275, 50, 50)
speed = 5

# Game loop
running = True
while running:
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            running = False

    # Key handling (continuous press)
    keys = pygame.key.get_pressed()

    if keys[pygame.K_LEFT]:
        player.x -= speed
    if keys[pygame.K_RIGHT]:
        player.x += speed
    if keys[pygame.K_UP]:
        player.y -= speed
    if keys[pygame.K_DOWN]:
        player.y += speed

    # Drawing
    screen.fill((0, 0, 0))
    pygame.draw.rect(screen, (255, 255, 255), player)
    pygame.display.update()

pygame.quit()
sys.exit()