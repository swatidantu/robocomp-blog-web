# SocNavEnv: An Environment for Social Navigation 

A typical indoor scenario would contain humans moving around, and humans interacting with other humans, or objects such as laptops. So to have all of these, the environment that we are creating consists of the following entities:

1. The robot
2. Humans
3. Plants
4. Tables
5. Laptops
6. Walls

## First Draft 
This was how the environment looked initially, with just simple humans, tables, and a laptop on the table. It required a lot of improvement, but to get started off with classes for humans, robot etc, this was a good start. The environment was written in OpenAI Gym's style and implemented all the necessary functions that are required by a Gym environment. The green circle represents the robot goal.

https://user-images.githubusercontent.com/57453637/178140491-bec734d2-2939-4e0d-b097-522034a79cc6.mp4

## Random Initialization
The previous environment had the entities placed at fixed coordinates. With random initializations, the environment looks even better, apart from the human motion. Humans were initialized to have a fixed orientation, and once they collide, they were stopped. 

https://user-images.githubusercontent.com/57453637/178141067-c907d976-ea19-4e46-96c2-10972ccb69dd.mp4

## Handling human collision
Referring to OpenAI's [multiagent particle environment](https://github.com/openai/multiagent-particle-envs/tree/master/multiagent) for handling collisions, collision forces were added. So after adding them to the environment, it looked much better:

https://user-images.githubusercontent.com/57453637/178141307-2c1c69e0-97ee-4840-b4c4-483aead331bd.mp4

## Different Room Shapes
Till now, the room was square in shape. Two more shapes rectangular, and L were added. The environment would randomly take shape, and the entities would be placed randomly in them. This is how the L shaped environment looks:

https://user-images.githubusercontent.com/57453637/178141917-18686afb-4b18-4c52-be33-d961747d8992.mp4

## Adding Interactions Between Entities
There are two types of interactions that were added. One is the interactions between humans and humans, and the other is the interaction between humans and laptops. Also, some of the human-human interactions would be stationary, while some of them could be moving. This is how the environment looked with interactions:

https://user-images.githubusercontent.com/57453637/178142077-00981ec3-f1b9-49b4-b356-e82d0e33e70b.mp4


## Fixing Human motion
The human motion still looks bad, that is just moving in a particular direction, and changing direction once a collision takes place. Humans would have goals now (blue circles), and the goals would be randomly sampled. Human motion was modeled using ORCA (Optimal Reciprocal Collision Avoidance) and SFM (Social Force Model). Humans would randomly use one of the two policies to navigate towards the goal.

https://user-images.githubusercontent.com/57453637/178142377-96b9fd35-6c1a-40b5-9b39-396064047bec.mp4

## Modeling motion of Humans in a Moving Interaction
The motion of humans in a crowd of interacting humans was modeled using ORCA. The crowd would have a goal (red circle), and the humans would move towards the goal. The crowd was treated as a single human and the velocity returned by ORCA policy would be divided among humans. A small Gaussian noise is also added to the velocity for each human so that all humans do not have the same velocity and orientation

https://user-images.githubusercontent.com/57453637/178142569-e1c139d2-b4d6-4854-b573-77965676e98b.mp4

