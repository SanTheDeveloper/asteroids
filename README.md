# My Pygame Asteroids Clone

## 🚀 Introduction

This is a basic clone of the classic arcade game "Asteroids," built using Python and the Pygame library. The objective is to navigate a spaceship and destroy incoming asteroids, which split into smaller pieces when hit.

---

## 🎮 How to Play

**Objective:** Destroy all asteroids without getting hit by them.

**Controls:**

- **`W`**: Move forward (in the direction the ship is facing)
- **`S`**: Move backward
- **`A`**: Rotate left
- **`D`**: Rotate right
- **`Spacebar`**: Shoot bullets
- **`X`**: Close the game window (or click the 'X' button)

**Gameplay Mechanics:**

- **Asteroid Destruction:** When an asteroid is hit by a bullet:
  - Large asteroids split into two medium asteroids.
  - Medium asteroids split into two small asteroids.
  - Small asteroids are destroyed completely.
- **Collision:** If your spaceship collides with any asteroid (regardless of size), the game ends immediately.

---

## 🧠 What I Learned

Building this game provided hands-on experience with fundamental programming concepts and specific Pygame functionalities.

### Python Concepts:

- **Object-Oriented Programming (OOP):**
  - **Classes & Objects:** Designed `Player`, `Asteroid`, `Shot`, `CircleShape`, and `AsteroidField` classes to represent game entities and their behaviors.
  - **Inheritance:** Utilized inheritance extensively (e.g., `Player`, `Asteroid`, `Shot` inheriting from `CircleShape`, which itself inherits from `pygame.sprite.Sprite`) to share common attributes and methods (like `position`, `radius`, `update`, `draw`).
  - **Encapsulation:** Grouped related data (attributes) and behavior (methods) within classes (e.g., player movement logic within the `Player` class, asteroid splitting logic within the `Asteroid` class).
- **Modules & Imports:** Structured the project into multiple files (`main.py`, `constants.py`, `circleshape.py`, `player.py`, `asteroid.py`, `asteroidfield.py`) and managed dependencies using `import` statements.
- **Constants:** Used a dedicated `constants.py` file to store game configuration values, making the code more readable and easier to modify.
- **Data Structures:**
  - **Lists:** Used for managing collections of points (e.g., `Player.triangle()` method) and iterating over sprite groups.
  - **`pygame.math.Vector2`:** Crucial for handling 2D positions, velocities, and directional vectors, enabling accurate movement and rotation calculations.
- **Control Flow:** Applied `if`/`else` statements for conditional logic, `while` loops for the main game loop, and `for` loops for iterating through events and game objects.
- **Functions & Methods:** Broke down complex tasks into smaller, manageable functions and class methods.
- **`random` Module:** Used extensively for generating random positions, velocities, and angles for asteroids and their split trajectories.

### Pygame Specifics:

- **Initialization & Setup:**
  - `pygame.init()`: Initializing all Pygame modules.
  - `pygame.display.set_mode()`: Creating the game window and display surface.
  - `pygame.display.flip()`: Updating the entire screen to show new frames.
- **Game Loop:** The core `while running:` loop structure that handles game logic, input, updates, and drawing in each frame.
- **Event Handling:**
  - `pygame.event.get()`: Processing user inputs and system events (e.g., closing the window).
  - `pygame.QUIT`: Handling the window close event for graceful exit.
  - `pygame.key.get_pressed()`: Detecting currently pressed keys for continuous input (movement, shooting).
- **Drawing Primitives:**
  - `screen.fill()`: Clearing the screen with a background color each frame.
  - `pygame.draw.polygon()`: Drawing the player's triangular ship.
  - `pygame.draw.circle()`: Drawing asteroids and bullets as circles.
- **Sprites & Sprite Groups:**
  - `pygame.sprite.Sprite`: The base class for visible game objects, facilitating organization.
  - `pygame.sprite.Group`: Efficiently managing collections of sprites for updates, drawing, and collision detection.
  - `.add()` / `.kill()`: Automatically adding sprites to groups on creation and removing them from all groups when `kill()` is called.
  - `.containers`: A static sprite field used to automatically add new instances to specified groups.
- **Time Management & `dt` (Delta Time):**
  - `pygame.time.Clock()`: Creating a clock object to control the game's frame rate.
  - `clock.tick(FPS)`: Limiting the frames per second (e.g., 60 FPS) and returning the time elapsed since the last tick (in milliseconds).
  - `dt` (Delta Time): Converting milliseconds to seconds (`/ 1000.0`) to make movement and rotation calculations frame-rate independent, ensuring consistent speed across different machines.
- **Vector Math for Game Physics:**
  - `pygame.math.Vector2.rotate()`: Rotating directional vectors for player movement and asteroid splitting.
  - `pygame.math.Vector2.distance_to()`: Calculating the distance between two points for collision detection.
- **Collision Detection:** Implemented custom circle-to-circle collision detection logic based on distances and radii.
- **Rate Limiting:** Implemented a simple cooldown timer for player shooting using `dt`.

---

## 💻 Running the Game

1.  **Prerequisites:**

    - Python 3.x
    - Pygame library (`pip install pygame`)
    - (If on Windows Subsystem for Linux 2 / WSL2): An X server like VcXsrv (XLaunch) running on your Windows host.

2.  **Setup (for WSL2/Linux users):**

    - Ensure XLaunch is running on Windows with "Multiple windows," "Start no client," and "Disable access control" enabled.
    - In your WSL2 terminal, ensure your `DISPLAY` environment variable is correctly set. A common method is adding `export DISPLAY="$(grep -oP "(?<= nameserver ).+" /etc/resolv.conf):0"` to your `~/.bashrc` file.

3.  **Run the Game:**
    - Navigate to the game's directory in your terminal.
    - Execute the `main.py` file:
      ```bash
      python3 main.py
      ```

---

## ✨ Future Improvements (Ideas)

- **Score System:** Track and display the player's score.
- **Lives & Game Over Screen:** Implement multiple lives and a proper "Game Over" display.
- **Level Progression:** Increase asteroid density or speed over time.
- **Sound Effects & Music:** Add audio for shooting, explosions, and background music.
- **Power-ups:** Introduce temporary boosts for the player.
- **Visual Enhancements:** More detailed ship graphics, asteroid textures, particle effects for explosions.
- **Hyperspace / Teleport:** A classic Asteroids feature.
- **Wrap-around Screen Edges:** Make objects that go off one side appear on the other.
