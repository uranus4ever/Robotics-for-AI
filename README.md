# Udacity_Robotics-for-AI
Projects for algorithm practice.
The content includes localization, Kalman filter, A-star path planning and PID control.

## Localization
Suppose there are RED and GREEN signs in the environment.
```
colors = [['R','G','G','R','R'],
          ['R','R','G','R','R'],
          ['R','R','G','G','R'],
          ['R','R','R','R','R']]
measurements = ['G','G','G','G','G']
motions = [[0,0],[0,1],[1,0],[1,0],[0,1]]
position_probablity = [[0.01105, 0.02464, 0.06799, 0.04472, 0.02465],
                        [0.00715, 0.01017, 0.08696, 0.07988, 0.00935],
                        [0.00739, 0.00894, 0.11272, 0.35350, 0.04065],
                        [0.00910, 0.00715, 0.01434, 0.04313, 0.03642]]
```

```
def sense(p, colors, measurement):
    for i in range(len(p)):
        for j in range(len(p[i])):
            hit = (measurement == colors[i][j])
            aux[i][j] = p[i][j] * (hit * sensor_right + (1-hit) * sensor_wrong)
            s += aux[i][j]
def move(p, motion):
    for i in range(len(p)):
        for j in range(len(p[i])):
            aux[i][j] = (p_stay * p[i][j]) + p_move * 
                        p[(i - motion[0]) % len(p)][(j - motion[1]) % len(p[i])]
```

| Filters | State Space | Belief | Efficiency | In Robotics|
| :--: | :--: | :--: | :--: | :--: |
| Histogram Filters | Discrete | Multimodel | Exponential | Approximate |
| Kalman Filters | Continuous | Unimodel | Quadratic | Approximate |
| Particle Filters | Continuous | Multimodel | ? | Approximate |

## A* Searching
```
grid = [[0, 1, 0, 0, 0, 0],
        [0, 1, 0, 0, 0, 0],
        [0, 1, 0, 0, 0, 0],
        [0, 1, 0, 0, 0, 0],
        [0, 0, 0, 0, 1, 0]]
```
_0 stands for paths and 1 means blocks._

list step cost from destination to the beginning:
```
heuristic = [[9, 8, 7, 6, 5, 4],
             [8, 7, 6, 5, 4, 3],
             [7, 6, 5, 4, 3, 2],
             [6, 5, 4, 3, 2, 1],
             [5, 4, 3, 2, 1, 0]]
```
Algorithm refers to ```4. Implement A star.py```
```
*******Successful Search*********
['v', ' ', ' ', ' ', ' ', ' ']
['v', ' ', ' ', ' ', ' ', ' ']
['v', ' ', ' ', ' ', ' ', ' ']
['v', ' ', ' ', '>', '>', 'v']
['>', '>', '>', '^', ' ', '*']
```


