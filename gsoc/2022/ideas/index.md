# Google Summer of Code 2022

19 Feb 2022



This is the list of ideas for Google Summer of Code 2022. If you have any suggestion you can tell us about it [here](https://gitter.im/robocomp/robocomp/robocomp-gsoc).

If you need more information about how to apply, please refer to the [contributor guidance page](/web/gsoc/2022/contributor_guidance).

## LIST of IDEAS for GSoC 2022

### 1\. Improvements on the social navigation toolkit SONATA
**Mentors**  
Pilar Bachiller, Daniel Rodríguez
 
**Description and outcomes**  
SONATA (SOcial NAvigation Toolkit for data Acquisition) is a toolkit designed to create datasets generators in the context of social robot navigation. The toolkit architecture has been designed as a network of RoboComp components: the simulator component, the event publisher, and the controller component. The simulator component instantiates the simulation (using the CoppeliaSim simulator), publishes the information about the simulated entities (people, walls, objects, and goals), and acts as an interface with the simulator, handling robot control and scene regeneration commands from a controller component. The event-publisher component receives events from a joystick or mouse and publishes the corresponding data. These two software elements are common to every specific dataset generation tool built using SONATA. The only problem-specific component is the controller, so the toolkit has been designed to facilitate forking the project and modifying the controller component. 

This project aims to improve the current implementation of SONATA adding more variability to the kind of scenarios that can be created. In addition, the simulator component will be reimplemented to interface with Webots (instead of CoppeliaSim), an open-source simulator widely used in industry, research, and education.


**Repository**  
[https://github.com/robocomp/sngnn](https://github.com/robocomp/sngnn)

**Needed skills**  
RoboComp, Python, C++, Webots

**Hours**  
175

**Difficulty**  
Medium

### 2\. ROS2 to CORTEX bridge
**Mentors**  
Marco A. Gutierrez, José Miguel Sánchez
 
**Description and outcomes**  
This project intends to create a simple and efficient way to allow CORTEX agents to connect with ROS2. CORTEX agents share a distributed graph (DSR) through a dedicated DDS topic, and can access the “external world” outside DSR through RoboComp, for instance to access the robot sensors and actuators or the cloud. You can read more about CORTEX in RoboComp’s web page. The goal here is to extend this schema to add ROS2 access as part of the optional external communication middlewares and protocols. With this new functionality, a CORTEX agent will be able to subscribe and publish ROS2 topics. The final objective is to integrate this development into the RoboComp code generator, robocompdsl. Extra steps might be taken to ensure different vendors can be used with the bridge, mostly FastDDS and CycloneDDS.

**Needed skills**  
C++, DDS, ROS2 (prefered)

**Hours**  
175

**Difficulty**  
Medium

### 3\. CoppeliaSim’s ZeroMQ to CORTEX connector
**Mentors**  
Félix Vidarte, Javier Durán
 
**Description and outcomes**  
This project intends to create a simple and efficient way to allow CORTEX agents to connect through the ZeroMQ pub/sub middleware. CORTEX agents share a distributed graph (DSR) through a dedicated DDS topic, and can access the “external world” outside DSR through RoboComp, for instance to access the robot sensors and actuators or the cloud. You can read more about CORTEX in RoboComp’s web page. The goal here is to extend this schema and add ZeroMQ as one of the options of RoboComp’s code generator, robocompdsl. The primary reason to use ZeroMQ from RoboComp is to connect to the CoppeliaSim robotics simulator, which has included in its latest version ZeroMQ as the preferred middleware for external clients. 

**Needed skills**  
C++17, Python

**Hours**  
175

**Difficulty**  
Medium


### 4\. WebSockets to CORTEX connector
**Mentors**  
Luis V. Calderita, Margarita Martínez
 
**Description and outcomes**  
This project intends to create a simple and efficient way to allow CORTEX agents to connect through the WebSockets protocol. CORTEX agents share a distributed graph (DSR) through a dedicated DDS topic, and can access the “external world” outside DSR through RoboComp, for instance to access the robot sensors and actuators or the cloud. You can read more about CORTEX in RoboComp’s web page. The goal here is to extend this schema and add WebSockets as one of the options of RoboComp’s code generator, robocompdsl. The primary reason to use WebSockets from RoboComp is to connect to browser based applications and viewers The project will start by studying WebSockets and RocoComp, and then implementing several examples of agents communicating with a browser application. Finally, the contributor will extend robocompdsl to make it generate the necessary code and CMake instructions, to create functioning agents capable of communicating through WebSockets.

**Needed skills**  
C++17, Python, Javascript

**Hours**  
350

**Difficulty**  
Medium


### 5\. SDFormat parser and generator for DSR
**Mentors**  
José Miguel Sanchez, Álvaro García
 
**Description and outcomes**  
SDFormat is an XML format that describes objects and environments for robot simulators, visualization and control, developed and supported by the Open Robotics Foundation.  A library for parsing the XML content is provided by this organization. CORTEX agents are components that share a distributed graph (DSR) through a dedicated DDS topic, and can access the “external world” outside DSR through RoboComp, for instance to access the robot sensors and actuators or the cloud. The DSR graph represents the current belief of the robot about itself and the world. You can read more about CORTEX in RoboComp’s web page. The goal of this project is to integrate this parser into the CORTEX agents’ code, to make SDF the preferred format to save and load the DSR graph. SDF is also the native format for the new Ignition robotics simulator. The project will test if world descriptions coming from the DSR can be used as scene graph in Ignition, and vice versa.

**Needed skills**  
XML, C++, SDFormat

**Hours**  
350

**Difficulty**  
Medium

### 6\. Model Predictive Control for path following and obstacle avoidance
**Mentors**  
Pablo Bustos, Pilar Bachiller
 
**Description and outcomes**  
Model Predictive Control is a form of Optimal Control that can be used to compute robot navigation control actions in real-time, directly from the dynamic model of the robot, constraints on its parameters and LIDAR data. A correct formulation of the problem is challenging since the dynamics of a differential robot is non-linear, and the free-zone where the robot is allowed to move must be modeled keeping the convexity of the problem. The goal of this project is to extend and improve our current RoboComp implementation, exploring new ways of representing the obstacles or free zones, and introducing new solutions for dynamic obstacles.
The contributor will validate its functioning in several complex scenarios that include a person accompanying by a social robot and autonomous car track following. We use Casadi as the optimization frontend and CoppeliaSim for simulation.


**Needed skills**  
C++17, Python, Casadi, optimization and control theory

**Hours**  
350

**Difficulty**  
Hard

### 7\. Human activity detection and recognition from skeleton views
**Mentors**  
Gerardo Pérez,  Francisco Andrés
 
**Description and outcomes**  
With the availability of embedded hardware that can run DNN in real-time, social mobile robots can now perceive humans in their environment with unprecedented ease. In this project, we want to explore learning schemas to recognize a set of simple human activities that occur in social robotics scenarios. Assuming that the robot can detect, track, extract the skeleton and identify a person in its surroundings, we want it to recognize which activity she is doing and inject that information into the CORTEX shared graph representation. By doing this, other agents will be able to use this information to improve the robot’s social behavior. The contributor will review the existing DNN architectures to select some promising architectures and validate them with data obtained from our robots.

**Needed skills**  
C++, Python, DNN

**Hours**  
350

**Difficulty**  
Hard

### 8\. Human 3D graphical representation in CORTEX agents
**Mentors**  
Ramón Cintas, Ana Bejarano
 
**Description and outcomes**  
Human detection and representation is a crucial ability of social robots. CORTEX is a robotics cognitive architecture created to control socially-aware robots. Its shared working memory, DSR, is a representation of the robot itself, and of its environment. When humans are present, our robots can detect, track and identify them, using advanced edge computing DNN devices. However, the way humans are represented, in terms of updating frequency, skeleton, identity, emotional state, etc can be challenging, especially when other agents and algorithms depend on it to create new behavior. The goal of this project is to create a new “human” node viewer in DSR, as part of the current graph viewer, that represents in real-time the geometry of the perceived person, and other attributes of its state.  This tool will be invaluable for code debugging and for improving how the robot perceives and represents humans. The contributor will use Qt and Qt3D as a scene-graph and render engine.


**Needed skills**  
C++, Qt

**Hours**  
350

**Difficulty**  
Medium

### 9\. Hand gestures interpretation for transfer of simple objects
**Mentors**  
Mario Haut, Luis J. Manso
 
**Description and outcomes**  
Social robots are gaining more complex capabilities that will be of enormous help for many people in the near future. One of the most interesting skills is the transfer of objects between the robot and a human. This task can be performed in different ways, for example, hand to hand or hand to basket. With the availability of embedded edge computing DNNs, the detection and tracking of human hands have become a real  and reliable skill for social robots. In this project we want to study and implement some initial experiments on human-hand to robot-basket transfer of simple objects. We will use a CoppeliaSim simulation of our robot Gif, that has a RGBD camera connected to a Jetson computer. Using a trained DNN that detects the hands with all the fingers in real-time, we want to detect and track configurations of a hand-with-an-object that moves into the basket, drops the object and moves away. The contributor will propose several techniques to approach this problem and will use simulated and real data obtained from the robot.

**Needed skills**  
C++, Pytrhon, DNNs

**Hours**  
350

**Difficulty**  
Medium

### 10\. Reinforcement Learning for pick and place operations
**Mentors**  
Francisco Andrés, Mario Haut
 
**Description and outcomes**  
Reinforcement learning is an established discipline for the automatic acquisition of control programs from a reward signal. Some early limitations arising from the necessary limited dimension of sensor spaces have been overcome with the integration of DNN as efficient reducers of large input data. In this project we want to apply RL as an online method to improve an existing grasping algorithm. Using a Kinova Gen3 arm simulated in CoppeliaSIm, that already performs a pick and place operation using a gripper with multiple force and distance sensors, the goal is to improve the current grasping performance by running RL algorithms that learn from the existing algorithm and, eventually, replace it to continue is adaptation to the specificities of the environment. If the experiments proceeds as expected, a second stage will try to transfer the learned controller to the grasping of a new target object in the scene, for example, from a block to a cup. All the experiments will be performed with RoboComp’s robotics cognitive architecture CORTEX, and the tools and existing agents already developed and tested.

**Needed skills**  
Python, C++, RL

**Hours**  
350

**Difficulty**  
Hard

### 11\. People accompanying algorithms
**Mentors**  
Gerardo Pérez, Pedro Núñez
 
**Description and outcomes**  
Social robot navigation is a recurring issue in every RoboComp GSoC program. Currently, RoboComp and its CORTEX architecture (based on Deep State Representation) have different agents that endow the robot with the ability to move with social awareness. The latter implies that 1) the robot must know people's pose; 2) the robot must somehow establish socially accepted routes; 3) during navigation, the robot must adapt to dynamic situations, such as people moving around it. The current configuration of agents in RoboComp solves these problems. In this project, we intend to extend the use case to the accompanying of people during navigation. Accompanying a person involves adjusting velocities, robot responses, safety navigation, etc., with the goal of navigating together with the person to a specific target. Therefore, this project focuses on the implementation of an agent, or several agents, that allows interacting with the current ones to carry out this new functionality. 

During the GSoC the contributor will learn the SNAPE navigation stack and the use of simulators, such as Coppelia. In a second phase, the contributor will aim to develop specific algorithms to accompany one or several people in a challenging and dynamic environment.


**Needed skills**  
RoboComp, Python, C++, CoppeliaSim

**Hours**  
350

**Difficulty**  
Hard

### 12\. Self-adaptive controllers for path following
**Mentors**  
Noe Zapata, Sergio Barroso 
 
**Description and outcomes**  
Self-adaptation is a key ability for future autonomous robots. Thanks to this capability, a robot is able to automatically adapt to changes during its operation. In the case of autonomous navigation, if the robot is endowed with this skill, it can automatically adjust a set of free parameters to improve its functioning given a cost function or metric. The effect of this adaptation is safer, more efficient, and, possibly, better socially aware navigation. Adaptation can operate on user-defined algorithms, using a proper optimization technique that adjusts some free parameters given some specific metric (e.g., distance to the target, time taken by the robot to reach the destination, etc.), or by building new controllers that improve the knowledge existing in the user-provided algorithms. The first category falls under Optimization Theory and the last category is known as Reinforcement Learning.  The main objective of this project is to develop an agent in the CORTEX architecture that shows self-adaptation capabilities for path tracking under varying circumstances. The contributor will design and implement this functionality with the help of the CoppeliaSim simulator, where dynamic elements, such as walking people, can be added and controlled to introduce more challenging social constraints.


**Needed skills**  
RoboComp, Python, C++, CoppeliaSim

**Hours**  
350

**Difficulty**  
Medium

### 13\. Generation of simulation environments using OSRF’s traffic editor
**Mentors**  
Marco A. Gutiérrez, Sergio Barroso 
 
**Description and outcomes**  
The traffic editor is a set of tools to auto-generate simulation worlds from annotated 2D floor plans with building infrastructure information. The tool was developed as part 
[https://github.com/open-rmf/rmf_traffic_editor](https://github.com/open-rmf/rmf_traffic_editor)

This project intends to extend the usage of traffic editor to the generation of simulation environments for outdoor robotics (i.e. self-driving cars). Contributors will have to make the necessary changes to the tool in order to process outdoor data and generate suitable simulation environments for the specific needs of those types of robots. 

**Needed skills**  
C++, CooppeliaSim, RoboComp, Qt5

**Hours**  
350

**Difficulty**  
Medium

### 14\. Extending the Social Navigation component to realistic scenarios
**Mentors**  
Luis J. Manso, Aditya Kapoor
 
**Description and outcomes**  
SNGNN-RL was developed for one of the GSoC’21 slots. It is a graph neural network model that is trained using Reinforcement Learning with SNGNN (GSoC’19-GSoC’20) as the learned reward function. We have been able to learn some enriched social policies, but it does not scale to realistic scenarios yet as it does not incorporate interactions in the environment between different entities. This is a limitation that we want to address. The goal of this project is to build on top of the previous implementation to develop a more realistic solution that incorporates static, dynamic obstacles and relations between them. The specific aims of this project are the following:
1. Firstly, we want to show that with SNGNN-RL we can tackle complicated realistic scenarios that contain dynamic and static obstacles.
2. We want to extend this approach to minimize disturbance in environments with labeled interactions.
3. Finally, we want to learn an end-to-end system that will learn which interactions are important and further use this information to navigate in the environment.

Currently, there are no models that tackle the problem of social navigation with static, dynamic object types along with interactions between them with a semi-learned reward function.

**Needed skills**  
Language & Frameworks: Python, CPP, RoboComp, PyTorch, OpenAI Gym (particularly multiagent particle environment)
Knowledge & Experience: Graph Neural Networks, Deep Reinforcement Learning (i.e., DQN and its variants, Policy Gradient methods, Actor-Critic Methods)

**Hours**  
350

**Difficulty**  
Hard

### 15\. Efficient querying of geometric object relationships in CORTEX’s shared graph (G)
**Mentors**  
Lucas Bonilla, Javier Durán
 
**Description and outcomes**  
CORTEX is a cognitive robotics architecture built on top of RoboComp. It provides a highly efficient working memory implemented as a distributed graph (DSR). This graph is accessible to all the agents running in a CORTEX instance and is used collaboratively to store the state of the robot and the state of the environment. Objects and humans are presented as nodes in the graph, while their relationships are stored as edges among them. On special kind of relation is RT, which represents a geometric 6D transformation. RT connected nodes form a tree inside DSR. In CORTEX, the access to the graph is done through an API named G, which has all the required methods to safely insert, modify or delete nodes and edges. On top of this API, other subAPIs have been developed to provide a more expressive and specialized way to access different functionalities on the graph. The goal of this project is to create a new subAPI specialized in geometric queries to G. It should answer questions like, which is the closest object of type X to object A?, Is object B on top of object C? or which is the orientation of object A relative to object B? The contributor will go through the current implementation of G and propose methods for the new API that will be validated with real and simulated (CoppeliaSim) data. 

**Needed skills**  
C++, RoboComp, CORTEX G API, 3D geometry

**Hours**  
Medium

**Difficulty**  
Medium

### 16\. Remote control of CoppeliaSim instances as an imaging resource for the CORTEX architecture
**Mentors**  
Félix Vidarte, Pablo Bustos
 
**Description and outcomes**  
RoboComp’s reference simulator is CoppeliaSim. In its latest release, CoppeliaSim provides an efficient full remote API through the ZeroMQ middleware. CORTEX is a robotics cognitive architecture built on top of RoboComp that provides a highly efficient shared working memory. One of the most challenging features of current cognitive architectures is imagination. An architecture endowed with this capability could simulate in super real-time the near future evolution of its current representation, creating alternative outcomes from small variations in the simulation parameters. The potential of this skill is huge, running from, hybrid symbolic-geometric planning to model-predictive control.  The goal of this project is to create a simple prototype of this skill using the new ZeroMQ API provided by CoppeliaSim, as a new imaging agent in CORTEX. This agent will have to answer a question of the form, what would happen if X? To do that it will initialize an instance of the simulator with the current state of the DSR and run it for a few seconds, introducing the required modifications. Once the simulation is over, it will provide the answer in a form that is representable in the DSR.


**Needed skills**  
C++, RoboComp, CORTEX G API, CoppeliaSim

**Hours**  
350

**Difficulty**  
Medium

## Complete list of Mentors:

### Francisco Andrés

>**pacoan**AT**unex**DOT**es**  
Lecturer, Robolab  
University of Extremadura  

### Pilar Bachiller

>**pilarb**AT**unex**DOT**es**  
Associate Professor, RoboLab,  
University of Extremadura  

### Sergio Barroso

>**sbarmirez**AT**gmail**DOT**com**   
Researcher, Robolab,  
University of Extremadura  

### Ana Bejarano

>**anacristinabejarano**AT**gmail**DOT**com**   
Researcher, Robolab,  
University of Extremadura  

### Lucas Bonilla

>**lucasbonilla2000**AT**gmail**DOT**com**   
RoboComp Developer  

### Pablo Bustos

>**pbustos**AT**unex**DOT**es**  
Associate Professor, RoboLab,  
University of Extremadura  

### Luis V. Calderita

>**lvcalderita**AT**unex**DOT**es**  
Lecturer in Computer Science,  
University of Extremadura  

### Ramon Cintas

>**rcintas**AT**unex**DOT**es**  
RoboComp Developer  

### Javier Durán

>**javiduran.formacion**AT**gmail**DOT**com**   
Researcher, Robolab,  
University of Extremadura  

### Álvaro García
>**alvarogarcia16102000**AT**gmail**DOT**com**  
Robocomp Developer  

### Marco A. Gutiérrez
>**marco.ant.gutierrez**AT**gmail**DOT**com**  
Robocomp Developer  

### Mario Haut

>**juanmariohaut**AT**unex**DOT**es**  
Lecturer in Computer Science,  
University of Extremadura  

### Aditya Kapoor
>**adityakapoor074**AT**gmail**DOT**com**  
Robocomp Developer  

### Luis J. Manso

>**l.manso**AT**aston**DOT**ac**DOT**uk**  
Lecturer in Computer Science,  
School of Engineering & Applied Science, Aston University, UK  
[http://ljmanso.com](http://ljmanso.com)

### Margarita Martínez
>**mmartinevqh**AT**alumnos**DOT**unex**DOT**es**  
Robocomp Developer  

### Pedro Núñez

>**pnuntru**AT**unex**DOT**es**  
Associate Professor, RoboLab,  
University of Extremadura  

### Gerardo Pérez

>**gepegon96**AT**gmail**DOT**com**   
Researcher, Robolab,  
University of Extremadura  

### Daniel Rodríguez

>**190229717**AT**aston**DOT**ac**DOT**uk**  
PhD Student,  
School of Engineering & Applied Science, Aston University, UK  

### José M. Sánchez

>**soy.jmi2k**AT**gmail**DOT**com**  
Robocomp Developer  

### Félix Vidarte

>**fevidarte**AT**alumnos**DOT**unex**DOT**es**  
Robocomp Developer  

### Noé Zapata

>**noez.c.mail**AT**gmail**DOT**com**  
Researcher, Robolab,  
University of Extremadura  

