# A very simple console game engine
A functional game engine. How does it work?
Well, there are two core parts of this engine.
The *game state dictionary*, and the *entity system*. 

## Game state dictionary
The game state dictionary is a dictionary containing the game state as well as entities. Good Console++ code uses the dictionary to store data instead of global variables.

The game state dictionary must contain two keys: `"running"` and  `"entities"`. `"running"` is a bool. At the end of every iteration of the main loop, if running is false, the loop ends.`"entities"` is a dictionary of `Entity`. More on that later

The game state is important because of how you update it. Every frame input is taken, and passed to a function that you define along with the game state. The call looks like this: `game(state, key)`. This call returns a new dictionary which replaces the old one.

## Entity system
The entity system is simple. There is a class called `Entity`. Its constructor takes 4 parameters: `x, y, char, style`.

Each iteration of the main loop, each entity calls `update()` (so, `entity.update()`.  Then, they are drawn at the x and y with the char and style. Update is a stub, but you can extend entity to add your own behaviour.

## Main loop

Finally, to initialize the main loop, run
```py
run_loop(game, {"running": True, "entities": {
  "player": Entity(10, 10, "@", style.RED)
  }})
````
Replace `game` with your own update function, and add and remove entities.
