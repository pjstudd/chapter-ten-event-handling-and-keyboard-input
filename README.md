# Chapter 10: Event Handling and Keyboard Input

## Overview
In game development, interaction is very important. Players control the game using the keyboard, mouse, or other input devices. In Pygame, these interactions are handled through **events**.

This chapter explains how to:
- Understand events and the event queue
- Handle keyboard inputs
- Create basic player movement
- Exit the game properly

---

# 10.1 Understanding Events and the Event Queue

An **event** is an action performed by the user, such as:
- Pressing a key
- Releasing a key
- Closing the window

Pygame stores these actions in something called the **event queue**.

We use the following loop to check events:

```python
for event in pygame.event.get():
    print(event)