# maze_solver
A program to solve mazes of any arbitrary number of dimensions.

If you pass the d_measure() function a maze of any number of dimensions, it will find and return the shortest path and number of steps from the beginning (9) to the end (4). The only condition is that the maze must be rectangular, e.g. 3x3x4x2, and it cannot have dimensions that deviate from this. Mazes must be constructed as grid objects, e.g. lists of lists (of lists...). 0 is an open space and 1 is walls.
