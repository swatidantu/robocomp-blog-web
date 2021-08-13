# DuelingDQN Agent with SNGNN reward

## Introduction
Following the previous posts, now we are training the Dueling DQN agent but the only difference from the previous experiment is that the reward comprises of both the hand-engineered reward function and the output of SNGNN network.

## About SNGNN
SNGNN is a Graph Neural Network to model adherence to social-navigation conventions for robots. Given a particular scenario composed of a room with any number of walls, objects and people (who can be interacting with each other) the network provides a social adherence ratio from 0 to 1. This information can be used to plan paths for human-aware navigation.
SNGNN can be thought of a learnt reward function and hence can be used for the current RL task.
Please refer to this page for more details: [SNGNN](http://ljmanso.com/sngnn.php)

## Reward Curve
The training has not yet completed but this is how the reward curve looks like
![SNGNN-DuelingDQN](https://user-images.githubusercontent.com/39992294/128668173-c7af2eb6-b36f-4dfb-b8ab-6cfc316aa60d.png)


## Performance


https://user-images.githubusercontent.com/39992294/128668213-b99d43b8-c448-42bd-a44f-3550661c52c6.mp4



## Future work
We will be now trying to evaluate the performance of the agent with and without SNGNN reward func while training the Reinforcement Learning algorithm.
