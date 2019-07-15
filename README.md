# Pathfinding with Neural Network

## Overview

This project is an initiative for taking part in #60daysofudacity challenge.

The purpose of the project is to study and use PyTorch for image data. The general idea is to solve pathfinding problem using Neural Network.

The project is for **learning** purpose, if you believe that other techniques (BFS, A*, etc) are better and NN takes too much resource, then please feel free to do another project ;p

The challenge will be divided into 2 parts:

1. Given a map, does a solution to reach the destination exist?
2. If there is such solution, find the shortest path
3. BONUS: integrate the solution to Unity/Unreal/ROS

## Challenge Instruction

**If you are new**, you can take the challenge in groups/individual, please do **DM me your group members (or your username**, if you are going solo) and your **project repo** so I can make a report to Udacity's officials. 

Remember, **there is no such thing as too late to start!**

After that please DM me with your **weekly progress report** every Saturday/Sunday (any timezone is fine), as I will need to compile the report and submit on Monday every week (this is the rule stated by Udacity officials).

It would be good and beneficial to you if you can actually solve the challenge, you should at least attempt the first part of the project ;)

## Project Instruction

Download / clone this repo

```
git clone https://github.com/albertsundjaja/pathfinding_challenge.git
```

You will get a `train.pkl`

```
# .pkl is a pickle format, you can use pandas to load it

import pandas as pd

df = pd.read_pickle('train.pkl')
```

In this file, there are 3 columns `map`, `path` and `is_solveable`.

the `map` and `path` is a 10x10 flattened matrix, while the `is_solveable` is a boolean indicating whether the map has a solution or not

example of the `map` data (unflattened into a matrix)

```
# matrix (original map)
array([[  1,   1,   1,   0,   1,   1,   1,   1,   1,   1],
       [  1,   0,   0,   1,   0, 200,   0,   1,   0,   0],
       [  1,   0,   1,   1,   1,   0,   1,   1,   1,   1],
       [  1,   1,   0,   1,   1,   1,   1,   1,   1,   0],
       [  0,   1,   0,   1,   0,   1,   1,   0,   0,   1],
       [  1,   1,   1,   1,   1,   0,   1,   1,   0,   1],
       [  1, 100,   1,   0,   0,   1,   0,   1,   1,   1],
       [  1,   0,   1,   0,   1,   0,   1,   0,   1,   1],
       [  0,   0,   1,   1,   1,   1,   0,   0,   1,   0],
       [  1,   0,   1,   0,   0,   1,   0,   1,   1,   0]])

# flattened (data in train.csv)
array([  1,   1,   1,   0,   1,   1,   1,   1,   1,   1,   1,   0,   0,
         1,   0, 200,   0,   1,   0,   0,   1,   0,   1,   1,   1,   0,
         1,   1,   1,   1,   1,   1,   0,   1,   1,   1,   1,   1,   1,
         0,   0,   1,   0,   1,   0,   1,   1,   0,   0,   1,   1,   1,
         1,   1,   1,   0,   1,   1,   0,   1,   1, 100,   1,   0,   0,
         1,   0,   1,   1,   1,   1,   0,   1,   0,   1,   0,   1,   0,
         1,   1,   0,   0,   1,   1,   1,   1,   0,   0,   1,   0,   1,
         0,   1,   0,   0,   1,   0,   1,   1,   0])
         
# you can convert back to matrix using flattened.reshape(10,10)
```

the cell with `100` is the starting point, while `200` is the destination point. `0` indicate obstacle (you can't pass through this path) and `1` indicate a road. You are allowed to move `up, down, left and right` only. It is assumed that the map is surrounded by walls, and as such you can't go outside the map.


### First Part of the Project

Given a map data, is there a path that connect the starting point and the endpoint?

For the example above, the `map` has at least one solution, so `is_solveable` is `True`

### Second Part of the Project

An example of the `path` solution to the above `map` example

```
array([[  0.,   0.,   0.,   0.,   0.,   1.,   1.,   1.,   0.,   0.],
       [  0.,   0.,   0.,   0.,   0., 200.,   0.,   1.,   0.,   0.],
       [  0.,   0.,   0.,   0.,   0.,   0.,   1.,   1.,   0.,   0.],
       [  0.,   0.,   0.,   1.,   1.,   1.,   1.,   0.,   0.,   0.],
       [  0.,   0.,   0.,   1.,   0.,   0.,   0.,   0.,   0.,   0.],
       [  0.,   1.,   1.,   1.,   0.,   0.,   0.,   0.,   0.,   0.],
       [  0., 100.,   0.,   0.,   0.,   0.,   0.,   0.,   0.,   0.],
       [  0.,   0.,   0.,   0.,   0.,   0.,   0.,   0.,   0.,   0.],
       [  0.,   0.,   0.,   0.,   0.,   0.,   0.,   0.,   0.,   0.],
       [  0.,   0.,   0.,   0.,   0.,   0.,   0.,   0.,   0.,   0.]])
```

`100` is the starting point, `200` is the endpoint, `1` is the path that goes from starting point to endpoint, and `0` elsewhere

### Bonus Part

Integrate your solution to something of your choice, Unity/Robot simulation/etc. This would be **very** challenging, as you would need to know how to integrate them in the software. For Unity, I have tested that we can do it by using `ZeroMQ`, this is basically a messaging API similar to REST API but lightweight and faster.


