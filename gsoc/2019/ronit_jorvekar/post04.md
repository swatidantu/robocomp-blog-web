
# Integration of previous work with Robocomp’s DSR
July  30, 2019

## What is DSR?
DSR is Deep state representation. It is a graph-like world models for robots. We need a service, called AGMExecutive, which can run as a mere world-model representation service. The executive is in charge of updating the plan for a list of agents.
I created 5 agents or components with DSR(Deep State Representation) to generate random scenarios. The scenario contains a room, a robot, humans, objects and their interaction with one another which is saved as a graph or DSR.
The 5 agents that i generated are room handler agent, human and interaction agent, object agent, predict score agent and transport agent.

## Scoring mechanism
We have trained a Graph neural network model and use it to predict the score of robot for the current scenario. The range of the score is from 0 to 100.
## Agents :
#### 1) Room Handler
This agent generates a random room after a fixed time period.
#### 2) Human and interaction handler
This agent adds humans and interactions between them in the room.
#### 3) Objects handler
This agent adds objects and interactions between them and humans in the room.
#### 4) Predict score
This agent displays the scenario in the 2D world and whenever the world changes it converts the current scenario to a graph and passes it through the pretrained graph neural network model and updates the score on a slider.
#### 5) Transport
This agent helps to reduce the y co-ordinate of all the entities except the robot which gives the  feeling as if the robot moves ahead. This helps to see how the score varies over the room as the robot traverses ahead.

All generations done by the agents(room, human and interactions, and objects ) are done randomly.

### A demonstration video:
The slider depicts the social acceptibility score of the robot in the current scenario. The robot is colored as red, humans as blue and objects as green.
[![Social Navigation](http://img.youtube.com/vi/QVvuywgomTE/0.jpg)](https://youtu.be/QVvuywgomTE "Social Navigation")
