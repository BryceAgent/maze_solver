import copy

def d_measure(maze):
    # determine number of dimensions
    # create one-dimensional list from maze according to a rule
    # maze can be reconstructed or solved following a rule

    # find dimensions

    maze_copy1 = copy.deepcopy(maze)

    dimensions = []

    while isinstance(maze_copy1, list):
        dimensions.append(len(maze_copy1))
        maze_copy1 = maze_copy1[0]

    depth = len(dimensions)

    # combine each integer from each list to get all possible coordinates

    all_coords = [[]]

    for length in dimensions:
        new_coords = []
        for coords in all_coords:
            for i in range(length):
                new_coords.append(coords + [i])
        all_coords = new_coords

    flat_maze = []

    r = 0
    while r < len(all_coords):
        search_coords = all_coords[r]
        r += 1
        d = 0
        maze_copy = copy.deepcopy(maze)
        while isinstance(maze_copy, list):
            maze_copy = maze_copy[search_coords[d]]
            d +=1
        flat_maze.append([maze_copy,search_coords])

    # find beginning and end coordinates

    beg = False
    end = False

    for coord in flat_maze:
        if coord[0] == 9:
            beg = coord[1]
        if coord[0] == 4:
            end = coord[1]
        if beg and end:
            break

    # set q

    q = []
    for n in beg:
        q.append(n)

    q = [q]
    con_q = [0]

    # find path

    path = []
    directions = [1,-1]

    t = 0
    while t <= len(q):

        if q[t] == end:
            d = con_q[t]

            shortest = []

            for n in range(len(path)):
                it = path.pop()

                if len(shortest) == 0:
                    shortest.append(it)
                else:
                    r = 0
                    for a in range(len(it)):
                        dif = abs(shortest[-1][a] - it[a])
                        r += dif
                    if r < 2:
                        shortest.append(it)

            rev = []
            for n in range(len(shortest)):
                rev.append(shortest[-n-1])
            shortest = rev

            return d, shortest


        one_step = []
        for direct in directions:
            for i in range(len(q[t])):
                new_q = copy.deepcopy(q[t])
                new_q[i] = new_q[i] + direct
                one_step.append(new_q)

        for c in one_step:
            if c in all_coords:
                idx = all_coords.index(c)
                if flat_maze[idx][0] == 0 or flat_maze[idx][0] == 4:
                    flat_maze[idx][0] = 1
                    q.append(c)
                    path.append(c)
                    con_q.append(con_q[t]+1)

        t += 1

    return -1


maze1 = \
    # 3d maze
    [
    # layer 0
    [[9, 0, 0, 0],
     [1, 1, 1, 0],
     [0, 0, 0, 0],
     [0, 1, 1, 1]],
    # layer 1
    [[1, 1, 1, 1],
     [0, 0, 1, 0],
     [0, 1, 1, 0],
     [1, 1, 1, 0]],
    # layer 2
    [[0, 0, 0, 1],
     [1, 0, 1, 1],
     [1, 1, 1, 1],
     [0, 0, 0, 0]],
    # layer 3
    [[4, 0, 1, 1],
     [1, 1, 1, 1],
     [0, 0, 0, 0],
     [1, 1, 1, 1]]
]

maze2 = \
    # 2d maze
    [
    [9, 0, 0],
    [1, 1, 0],
    [4, 0, 0]
        ]

print(d_measure(maze2))
