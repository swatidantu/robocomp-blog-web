# Google Summer of Code 2021

19 Feb 2022

## General information on applications

The list of ideas for Google Summer of Code 2021. If you have any suggestion you can tell us about it [here](https://gitter.im/robocomp/robocomp/robocomp-gsoc).

* It is important to first familiarize with the [software](https://github.com/robocomp/robocomp).
* Please, go through the available tutorials and direct your questions to the [gitter chat](https://gitter.im/robocomp/robocomp/robocomp-gsoc).
* Please read all the information posted in this page before applying or asking.
* Make sure you are familiar with the required skills for the idea.
* Since several of the mentioned RoboComp tools and components are not explained here to keep this list short, we encourage everyone to check the RoboComp documentation linked below.
* Mentors and backup [mentors](/web/gsoc/2022/ideas/#complete-list-of-mentors)  are listed right after the idea title. All [mentors](/web/gsoc/2021/ideas/#complete-list-of-mentors) contact info is at the end of the page. Contact them directly for specific questions on the idea.


Robocomp installation and tutorials: [https://github.com/robocomp/robocomp/tree/stable/doc#tutorials](https://github.com/robocomp/robocomp/tree/stable/doc#tutorials)

If you have not worked before with Git Branching, we encourage you to visit this web: [https://learngitbranching.js.org/](https://learngitbranching.js.org/)

**Where can I start and what to include on my application?**

You are encouraged to go through these steps for a better understanding and follow-up of your application:

1.  Download and install RoboComp: [https://github.com/robocomp/robocomp/blob/stable/README.md](https://github.com/robocomp/robocomp/blob/stable/README.md).
2.  Follow the tutorials: [https://github.com/robocomp/robocomp/tree/stable/doc#tutorials](https://github.com/robocomp/robocomp/tree/stable/doc#tutorials).
3.  Once you are familiar with RoboComp and the components and tools involved in the particular idea you want to contribute to, try to understand how these components/tools work and, if possible, their design.
4.  Participate in gsoc [gitter](https://gitter.im/robocomp/robocomp/robocomp-gsoc) asking any question you might have.
5.  Create a schedule with the milestones you plan to follow during the GSoC 2022 program.
6.  **Send the schedule and any code you might have written along with your CV and other application materials to the mentor of your idea and the backup mentor ([/web/gsoc/2021/ideas/#complete-list-of-mentors](/web/gsoc/2022/ideas/#complete-list-of-mentors)).**

For general questions about RoboComp please use: The [gitter chat](https://gitter.im/robocomp/robocomp).

## LIST of IDEAS for GSoC 2022

### 1\. Improvements on the social navigation toolkit SONATA
**Mentors**  
Pilar Bachiller, Daniel Rodríguez
 
**Brief description**  
SONATA (SOcial NAvigation Toolkit for data Acquisition) is a toolkit designed to create datasets generators in the context of social robot navigation. The toolkit architecture has been designed as a network of RoboComp components: the simulator component, the event publisher, and the controller component. The simulator component instantiates the simulation (using the CoppeliaSim simulator), publishes the information about the simulated entities (people, walls, objects, and goals), and acts as an interface with the simulator, handling robot control and scene regeneration commands from a controller component. The event-publisher component receives events from a joystick or mouse and publishes the corresponding data. These two software elements are common to every specific dataset generation tool built using SONATA. The only problem-specific component is the controller, so the toolkit has been designed to facilitate forking the project and modifying the controller component. 

This project aims to improve the current implementation of SONATA adding more variability to the kind of scenarios that can be created. In addition, the simulator component will be reimplemented to interface with Webots (instead of CoppeliaSim), an open-source simulator widely used in industry, research, and education.


**Repository**  
[https://github.com/robocomp/sngnn](https://github.com/robocomp/sngnn)

**Needed skills**  
RoboComp, Python, C++, Webots

### 2\. ROS2 to CORTEX bridge
**Mentors**  
Marco A. Gutiérrez
 
**Brief description**  
This project intends to create a simple and efficient way to allow CORTEX agents to connect with ROS2. CORTEX agents share a distributed graph (DSR) through a dedicated DDS topic, and can access the “external world” outside DSR through RoboComp, for instance to access the robot sensors and actuators or the cloud. You can read more about CORTEX in RoboComp’s web page. The goal here is to extend this schema to add ROS2 access as part of the optional external communication middlewares and protocols. With this new functionality, a CORTEX agent will be able to subscribe and publish ROS2 topics. The final objective is to integrate this development into the RoboComp code generator, robocompdsl. Extra steps might be taken to ensure different vendors can be used with the bridge, mostly FastDDS and CycloneDDS.

**Needed skills**  
C++, DDS, ROS2 (prefered)

### 3\. CoppeliaSim’s ZeroMQ to CORTEX connector
**Mentors**  
...
 
**Brief description**  
This project intends to create a simple and efficient way to allow CORTEX agents to connect through the ZeroMQ pub/sub middleware. CORTEX agents share a distributed graph (DSR) through a dedicated DDS topic, and can access the “external world” outside DSR through RoboComp, for instance to access the robot sensors and actuators or the cloud. You can read more about CORTEX in RoboComp’s web page. The goal here is to extend this schema and add ZeroMQ as one of the options of RoboComp’s code generator, robocompdsl. The primary reason to use ZeroMQ from RoboComp is to connect to the CoppeliaSim robotics simulator, which has included in its latest version ZeroMQ as the preferred middleware for external clients. 

**Needed skills**  
C++17, Python

### 4\. WebSockets to CORTEX connector
**Mentors**  
Luis V. Calderita
 
**Brief description**  
This project intends to create a simple and efficient way to allow CORTEX agents to connect through the WebSockets protocol. CORTEX agents share a distributed graph (DSR) through a dedicated DDS topic, and can access the “external world” outside DSR through RoboComp, for instance to access the robot sensors and actuators or the cloud. You can read more about CORTEX in RoboComp’s web page. The goal here is to extend this schema and add WebSockets as one of the options of RoboComp’s code generator, robocompdsl. The primary reason to use WebSockets from RoboComp is to connect to browser based applications and viewers The project will start by studying WebSockets and RocoComp, and then implementing several examples of agents communicating with a browser application. Finally, the student will extend robocompdsl to make it generate the necessary code and CMake instructions, to create functioning agents capable of communicating through WebSockets.

**Needed skills**  
C++, Python

### 5\. SDFormat parser and generator for DSR
**Mentors**  
José Miguel Sanchez, Marco A. Gutiérrez
 
**Brief description**  
SDFormat is an XML format that describes objects and environments for robot simulators, visualization and control, developed and supported by the Open Robotics Foundation.  A library for parsing the XML content is provided by this organization. CORTEX agents are components that share a distributed graph (DSR) through a dedicated DDS topic, and can access the “external world” outside DSR through RoboComp, for instance to access the robot sensors and actuators or the cloud. The DSR graph represents the current belief of the robot about itself and the world. You can read more about CORTEX in RoboComp’s web page. The goal of this project is to integrate this parser into the CORTEX agents’ code, to make SDF the preferred format to save and load the DSR graph. SDF is also the native format for the new Ignition robotics simulator. The project will test if world descriptions coming from the DSR can be used as scene graph in Ignition, and vice versa.

**Needed skills**  
XML, C++, SDFormat

### 6\. Model Predictive Control for path following and obstacle avoidance
**Mentors**  
...
 
**Brief description**  
Model Predictive Control is a form of Optimal Control that can be used to compute robot navigation control actions in real time, directly from the dynamic model of the robot, constraints on its parameters and LIDAR data. A correct formulation of the problem is challenging since the dynamics of a differential robot is non-linear, and the modelling of the free-zone where the robot is allowed to move should be a set of convex polygons. The goal of this project is to extend and improve our current RoboComp implementation, validating its functioning in several complex scenarios that include person accompanying by a social robot and  autonomous car track following. We use Casadi as the optimization frontend and CoppeliaSim for simulation.

**Needed skills**  
C++17, Python, Casadi, optimization and control theory

### 7\. Human activity detection and recognition from skeleton views
**Mentors**  
...
 
**Brief description**  
...
**Needed skills**  
...

### 8\. Human 3D graphical representation in CORTEX agents
**Mentors**  
...
 
**Brief description**  
...
**Needed skills**  
...

### 9\. Hand gestures interpretation for transfer of simple objects
**Mentors**  
...
 
**Brief description**  
...
**Needed skills**  
...

### 10\. Reinforcement Learning for pick and place operations
**Mentors**  
...
 
**Brief description**  
...
**Needed skills**  
...

### 11\. People accompanying algorithms
**Mentors**  
Gerardo Pérez, Pedro Núñez
 
**Brief description**  
Social robot navigation is a recurring issue in every RoboComp GSoC program. Currently, RoboComp and its CORTEX architecture (based on Deep State Representation) has different agents that endow the robot with the ability to move with social awareness. The latter implies that 1) the robot must know people's pose; 2) the robot must somehow establish socially accepted routes; 3) during navigation, the robot must adapt to dynamic situations, such as people moving around it. The current configuration of agents in RoboComp solves these problems. In this GSoC we intend to extend the use case to the accompanying of people during navigation. Accompanying a person involves adjusting velocities, robot responses, safety navigation, etc., with the goal of navigating together with the person to a specific target. Therefore, this GSoC focuses on the implementation of an agent, or several agents, that allow interacting with the current ones to carry out this new functionality.  

During the GSoC the student will learn the SNAPE navigation stack and the use of simulators, such as Coppelia. In a second phase, the student will aim to develop specific algorithms to accompany one or several people in a challenging and dynamic environment. 

**Needed skills**  
RoboComp, Python, C++, CoppeliaSim

### 12\. Self-adaptive controllers for path following
**Mentors**  
Noe Zapata, Sergio Barroso 
 
**Brief description**  
Self-adaptation is a key ability for future autonomous robots. Thanks to this capability, a robot is able to automatically adapt to changes during its operation. In the case of autonomous navigation, if the robot is endowed with this skill, it can automatically adjust its free parameters to achieve safe, efficient and, if necessary, socially aware navigation. Some of these algorithms are based on classical optimizers, which aim to minimize some specific metric (e.g., distance to the target, time taken by the robot to reach the destination, etc.). In the same way, it is also possible to reach this self-adaptation using different approaches, such as neural networks. 

The main objective of this GSoC is to develop an agent in the CORTEX architecture that endows the robot with self-adaptation capabilities for path following. The student will implement this new functionality with the help of the Coppelia simulator, where dynamic elements, such as people, can be added to make the challenge more exciting.

**Needed skills**  
RoboComp, Python, C++, CoppeliaSim

### 13\. RCManager: CORTEX agent configuration GUI
**Mentors**  
Esteban Martinena, Pedro Núñez
 
**Brief description**  
As the number of RoboComp agents grows, the complexity of managing many of the most basic functionalities also increases. Tasks as simple as starting an agent now require the user to execute command lines. Likewise, if an agent goes down, something as simple as alerting the user becomes challenging to see if many agents are operating concurrently. For this reason, it is always interesting to have a graphical tool, a user interface, that facilitates and speeds up a set of basic tasks. 
The main objective of this GSoC is the development of a graphical tool that allows, among other options: 1) the start of all agents that constitute a particular experiment from a description file; 2) display the status of each agent (running, paused, failure); and 3) safe shutdown of the agent, all at the click of a button. The user interface will be developed with Qt, identifying agents with nodes and dependencies between agents with arcs.

**Needed skills**  
RoboComp, Python, C++, Qt

### 14\. Generation of simulation environments using OSRF’s traffic editor
**Mentors**  
Marco A. Gutiérrez
 
**Brief description**  
The traffic editor is a set of tools to auto-generate simulation worlds from annotated 2D floor plans with building infrastructure information. The tool was developed as part 
https://github.com/open-rmf/rmf_traffic_editor

This project intends to extend the usage of traffic editor to the generation of simulation environments for outdoor robotics (i.e. self driving cars). Students will have to make the necessary changes to the tool in order to process outdoor data and generate suitable simulation environments for the specific needs of those types of robots. 

**Needed skills**  
C++, CooppeliaSim, RoboComp, Qt5

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

### Pablo Bustos

>**pbustos**AT**unex**DOT**es**  
Associate Professor, RoboLab,  
University of Extremadura  

### Luis V. Calderita

>**lv**DOT**calderita**AT**unileon**DOT**es**  
Lecturer in Computer Science,  
University of León  

### Ramon Cintas

>**rcintas**AT**unex**DOT**es**  
Researcher, Robolab,  
University of Extremadura  

### Marco A. Gutiérrez
>**marcog**AT**unex**DOT**es**  
Robocomp Developer  

### Luis J. Manso

>**l.manso**AT**aston**DOT**ac**DOT**uk**  
Lecturer in Computer Science,  
School of Engineering & Applied Science, Aston University, UK  
[http://ljmanso.com](http://ljmanso.com)

### Esteban Martinena

>**emartinena**AT**unex**DOT**es**  
Researcher, Robolab  
University of Extremadura  

### Pedro Núñez

>**pnuntru**AT**unex**DOT**es**  
Associate Professor, RoboLab,  
University of Extremadura  

### Daniel Rodríguez

>**190229717**AT**aston**DOT**ac**DOT**uk**  
PhD Student,  
School of Engineering & Applied Science, Aston University, UK  


