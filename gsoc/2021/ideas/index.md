# Google Summer of Code 2021

18 Feb 2021

## General information on applications

The list of ideas for Google Summer of Code 2021. If you have any suggestion you can tell us about it [here](https://gitter.im/robocomp/robocomp/robocomp-gsoc).

* It is important to first familiarize with the [software](https://github.com/robocomp/robocomp).
* Please, go through the available tutorials and direct your questions to the [gitter chat](https://gitter.im/robocomp/robocomp/robocomp-gsoc).
* Please read all the information posted in this page before applying or asking.
* Make sure you are familiar with the required skills for the idea.
* Since several of the mentioned RoboComp tools and components are not explained here to keep this list short, we encourage everyone to check the RoboComp documentation linked below.
* Mentors and backup [mentors](/web/gsoc/2021/ideas/#complete-list-of-mentors)  of the previous year are listed right after the idea explanation. All [mentors](/web/gsoc/2021/ideas/#complete-list-of-mentors) contact info is at the end of the page. Contact them directly for specific questions on the idea.


Robocomp installation and tutorials: [https://github.com/robocomp/robocomp/tree/stable/doc#tutorials](https://github.com/robocomp/robocomp/tree/stable/doc#tutorials)

If you have not worked before with Git Branching, we encourage you to visit this web: [https://learngitbranching.js.org/](https://learngitbranching.js.org/)

**Where can I start and what to include on my application?**

You are encouraged to go through these steps for a better understanding and follow-up of your application:

1.  Download and install RoboComp: [https://github.com/robocomp/robocomp/blob/stable/README.md](https://github.com/robocomp/robocomp/blob/stable/README.md).
2.  Follow the tutorials: [https://github.com/robocomp/robocomp/tree/stable/doc#tutorials](https://github.com/robocomp/robocomp/tree/stable/doc#tutorials).
3.  Once you are familiar with RoboComp and the components and tools involved in the particular idea you want to contribute to, try to understand how these components/tools work and, if possible, their design.
4.  Participate in gsoc [gitter](https://gitter.im/robocomp/robocomp/robocomp-gsoc) asking any question you might have.
5.  Create a schedule with the milestones you plan to follow during the GSoC 2021 program.
6.  **Send the schedule and any code you might have written along with your CV and other application materials to the mentor of your idea and the backup mentor ([/web/gsoc/2021/ideas/#complete-list-of-mentors](/web/gsoc/2021/ideas/#complete-list-of-mentors)).**

For general questions about RoboComp please use: The [gitter chat](https://gitter.im/robocomp/robocomp).

## LIST of IDEAS for GSoC 2021

### 1\. Coding assistant for textual programming in LearnBlock
**Mentors**  
Pilar Bachiller, Iván Barbecho
 
**Brief description**  
LearnBlock is an educational programming tool developed for learning programming through robotics. It has been designed to facilitate the learning process starting with a visual language and progressing towards a professional programming language. Specifically, the user can choose whether to create a program from blocks, from the textual representation of blocks (Block-Text) or coding in Python. In addition, LearnBlock provides a wide variety of functions related to perception and robot control which are available by means of visual blocks. Through the interaction with these blocks, the user has access to the description and usage of every function. These functions can also be used in a textual program using Block-Text and Python. Nevertheless, for textual programming the tool does not provide any help on the available functions. This project aims to include a coding assistance tool that guides the programmer in the use of the available set of functions for creating a textual code. Specifically, the coding assistance will be provided in two ways. Firstly, the tool will provide a new option to show the list of available functions with their corresponding descriptions, parameters’ specification, etc. Additionally, the tool will provide code completion facilities to help the programmer on the use of all the LearnBlock’s functions.

**Repository**  
[https://github.com/robocomp/LearnBlock](https://github.com/robocomp/LearnBlock)

**Needed skills**  
Python, Qt5

### 2\. Revamping Robocomp with DevOps
**Mentors**  
Esteban Martinena, Ramón Cintas
 
**Brief description**  

The DevOps culture came on a long time ago and doesn't seem to be going away. Robocomp is largely based on an agile development philosophy that is part of this culture, but it has always been weak on continuous integration, testing and deployment. For example, several attempts have been made to package the software but have been abandoned, mostly because the processes were not automated and it was impossible for anyone to maintain it. The same has happened with classes and libraries that have become obsolete without anyone being aware of it because there is no testing for it.

This slot is focused on bringing Robocomp into the DevOps era, automating testing, build, integration and deployment processes, as well as restructuring the internal code to make this possible. It is an ambitious, but achievable and necessary project.

Tasks for this idea are:
- Creation of buildbot workflow for Robocomp CI.
- Creation of tests for Robocomp classes and libraries.
- Robocomp core packaging automation.

**Needed skills**  
Python, Dockers, C++, Shell Script

### 3\. Deep Reinforcement Learning for precise robot grasping and object manipulation
**Mentors**  
Mohamed Shawky, Francisco Andrés
 
**Brief description**  
Performing accurate object manipulation with a robot arm involves many challenging tasks, including perception, planning and control. In GSoC’20, we built a grasping pipeline that uses DNN-estimated object poses in order to plan an accurate trajectory to the desired object and then grasp and manipulate it. Our main focus was to perform accurate 6D pose estimation, as well as build and test a complete grasping pipeline. However, the current robot grasping and manipulation pipeline is based on classical approaches, most of which is done using our currently-used simulator (CoppeliaSim). We need to leverage the power of deep reinforcement learning (DRL) to build a complete alternative pipeline for robot control with grasping and object manipulation. The main idea is that the robot uses the DNN-estimated object poses, plans a path to the desired object and then moves to grasp it. One can go for end-to-end approaches or use currently-implemented perception modules. The workflow is to be tested on Kinova Gen3 arm using DNN-estimated poses, previously developed.

**Repository**  
[https://github.com/robocomp/grasping](https://github.com/robocomp/grasping)

**Needed skills**  
Python, C++, RoboComp, Deep Learning, Reinforcement Learning Basics, Familiarity with Tensorflow and/or Pytorch

### 4\. Monocular Depth Estimation from RGB signals
**Mentors**  
Mohamed Shawky, Luis Vicente Calderita
 
**Brief description**  
For a humanoid robot, perception offers crucial knowledge for doing many tasks. Most perception tasks require a depth map for the current scene. Our current Viriato Robot has RGBD cameras with depth sensors to measure scene depth. Our target is to compensate for depth sensors with a depth estimator that extracts a depth map from for each RGB frame, which is also called Monocular depth estimation. One way is to consider end-to-end Deep Learning approaches. The depth estimator should work in real-time or near real-time to ensure system reliability and to be a good compensator for the depth sensors in real life situations. Also, the depth estimator is to be integrated with the current perception modules and tested on different scenarios to evaluate its performance compared to the physical depth sensors.

**Needed skills**  
Python, C++, RoboComp, Machine Learning, Computer Vision

### 5\. Improvement of a Social Navigation component
**Mentors**  
Pilar Bachiller, Luis Manso
 
**Brief description**  
SNGNN1D was developed for one of the GSoC’19 slots. It is a graph neural network model that can be used to assess user discomfort in robot navigation scenarios. Despite the estimates it produces are very accurate, using it for real navigation requires searching in the navigation state space and performing multiple queries (one per state explored). This is a relatively slow process that we want to accelerate. The goal of this project is to build on top of the previous implementation and develop a more lightweight solution.
To test the algorithms we will be using SONATA (a sub-project of RoboComp that we use to generate randomised social navigation environments). You will find SNGNN1D’s and SONATA’s code in [https://github.com/robocomp/sngnn](https://github.com/robocomp/sngnn).

**Needed skills**  
Python, RoboComp, previous experience with graph neural networks

### 6\. Graphical-User Interface for affective human-robot interactions
**Mentors**  
Pedro Núñez, Rishi Gondkar
 
**Brief description**  
Human-robot interaction is one of the most important tasks in a social robot. The way in which a robot talks to the person, what voice it uses, expressiveness, etc. are factors that determine the success of the interaction. The objective of this project is to implement a tool that facilitates the evaluation of a conversation between a person and the robot using the technique known as WOz - wizard of Oz (some references where students can find some ideas: Weiss et al, 2010). For this purpose, a graphical interface will be implemented that should integrate different voices (TTS), and all the functionalities required by the professional who evaluates the conversation. In addition, if the robot can express emotions, we will study the possibility of adding them during the conversation to quantify the impact they have on the interaction. 

Weiss, Astrid & Bernhaupt, Regina & Dürnberger, Daniel & Altmaninger, M. & Buchner, Roland & Tscheligi, M.. (2010). User experience evaluation with a Wizard of Oz approach: Technical and methodological considerations. 303 - 308. 

**Needed skills**  
RoboComp, Python3

### 7\. An object detection component for LearnBlock
**Mentors**  
Iván Barbecho, Francisco Andrés
 
**Brief description**  
LearnBlock is an educational programming tool developed for learning programming through robotics. It has been designed to facilitate the learning process starting with a visual language and progressing towards a professional programming language. LearnBlock includes many interesting features: robot-agnostic design; blocks can be created from code without modifying the core code of the tool; robots can be programmed using different languages (visual, Block-Text or Python); a program can be run and interrupted from the tool itself, ensuring proper stop and disconnection of the robot. LearnBlock also includes components to detect faces, emotions and artificial marks. This functionality is accessible by the user through different sets of visual blocks. The goal of this project is to extend this functionality by creating a new component for object detection. The component will be connected to LearnBlock though new blocks that will allow for the creation of new robot behaviours according to the detected objects around it.

**Repository**  
[https://github.com/robocomp/LearnBlock](https://github.com/robocomp/LearnBlock)

**Needed skills**  
RoboComp, Deep Learning, Python3, Qt5

### 8\. Revamping AGGLPlanner and AGM
**Mentors**  
Luis Manso, Pedro Núñez
 
**Brief description**  
AGM (Active Grammar-based modeling) is a core for robotic architectures capable of performing perception-aware planning (that means that, besides any regular planning-related task, you can use AGM to plan goals that involve detecting and modeling new objects). AGM relies on a visual language named AGGL (Active Graph Grammar Language) that is used to describe the possible changes that robots can make to their world models and the behavior that they should adopt if such changes are desired (see more information in http://ljmanso.com/agm/index.html).  

In this project, you will study how it works, analyse its limitations, and implement a few new features e.g., Python3 support, the 'exists' operator…

The first goal of this project is to migrate AGM and AGMPlanner to python 3. This will allow us to test software agents in RoboComp that currently do not work with the current architecture. Validating these agents will be the second step. Finally, the AGM functionality will be extended with new operators. 

**Needed skills**  
Python3, Qt5

### 9\. Software agent for traffic and pedestrian traffic monitoring in outdoor environments using rgb cameras
**Mentors**  
Nivedita Rufus, Sergio Barroso
 
**Brief description**  
One of the works developed at GSoC'19 was the creation of a software agent to estimate building occupancy using RGB cameras and detection networks.

This time we propose to extend this work, with the aim of monitoring the exterior of buildings, paying special attention to some parameters such as vehicle traffic and pedestrian traffic in an urbanized area. The idea is to implement a software agent that uses vehicle and people detection networks and provides us with information about potential conflict zones that can be identified in an urban road, such as pedestrian crossings, traffic circles or changes of direction. To achieve this, the images provided by RGB cameras located at a distance of approximately 50 meters from the road to be monitored will be used. It is important to search for camera datasets that meet this condition.

**Needed skills**  
Robocomp, Python3

### 10\. Computer vision for detecting elements of a vehicle's environment with RoboComp
**Mentors**  
Araceli Vega,  Sergio Barroso
 
**Brief description**  
The detection of risk situations during the navigation of mobile robots is an essential task for future applications. The goal is to create a software agent in Robocomp with the aim of improving vehicle driving, using deep learning and computer vision techniques.

The main idea is to use one or several RGB cameras placed in a vehicle for lane detection, pedestrian detection, vehicle detection, sign detection and more elements that affect driving.
To perform this task, it is possible to work either with real datasets of cameras placed in vehicles or to use the Carla vehicle driving simulator.

**Needed skills**  
Robocomp, Python3, Computer Vision

### 11\. Sign Language Recognition Component
**Mentors**  
Kanav Gupta,  Aditya Aggarwal
 
**Brief description**  
One of the capabilities of the robot is to efficiently communicate with humans. One way to do this is through hand gestures. Currently, RoboComp includes a Hand Gesture Recognition component ([https://github.com/robocomp/robocomp-robolab/tree/master/components/detection](https://github.com/robocomp/robocomp-robolab/tree/master/components/detection)) which detects and recognizes single hand gestures from American Sign language. In this project, we want to expand upon the functionality of this component, by including recognition of gestures that include hand interactions with other body parts, like in the case of British Sign Language (BSL). The process can be divided into two parts:
- **Body and Hand Detection**: Detecting body and hand joints in the image/video feed.
- **Gesture recognition**: Estimation of hand pose/shape and classification into gestures. Large public datasets along with relevant research is available online which can be referred for the project implementation.

**Needed skills**  
Python3, Tensorflow/Pytorch, Machine Learning, Computer Vision

### 12\. Designing Python agents for CORTEX
**Mentors**  
Juan Carlos García, Pablo Bustos
 
**Brief description**  
CORTEX is a cognitive architecture created on top of RoboComp that provides a set of agents with a shared data structure (G) removing the need for topics, interfaces and ports. All development has been done using C++. The goal of this project is to complete the tools to automatically create Python agents using RoboComp’s code generator and the pybind11 wrapping tool. This project has already started and the most complex part is completed with the G API already ported. The student will work with the developing team to complete the UI where G is displayed in several forms: a dynamic graph, a 2D view of the scene (Qt), a 3D view of the scene (Qt3D) and an editable tree (textual). We expect that with the release of Python agents, more people will become interested in CORTEX and a larger community involved in Cognitive Robotics will surely thrive.

**Needed skills**  
RoboComp, C++, Python, Qt5

## Complete list of Mentors:

### Aditya Aggarwal

>**aditya.aggarwal**AT**students**DOT**iiit**DOT**ac**DOT**in**  
RoboComp Developer  
International Institute of Information Technology, Hyderabad  

### Francisco Andrés

>**pacoan**AT**unex**DOT**es**  
Lecturer, Robolab  
University of Extremadura  

### Pilar Bachiller

>**pilarb**AT**unex**DOT**es**  
Associate Professor, RoboLab,  
University of Extremadura  

### Ivan Barbecho

>**ibarbechodelgado**AT**gmail**DOT**com**   
RoboComp Developer  

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

### Juan Carlos García

>**juancarlos97gg**AT**gmail**DOT**com**   
Researcher, Robolab,  
University of Extremadura  

### Rishi Gondkar

>**rishigondkar**AT**gmail**DOT**com**  
RoboComp Developer  
Pune Institute of Computer Technology  

### Kanav Gupta

>**kanavgupta0711**AT**gmail**DOT**com**  
RoboComp Developer  
International Institute of Information Technology, Hyderabad  

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

### Nivedita Rufus

>**nive**DOT**hardy**AT**gmail**DOT**com**  
RoboComp Developer  
IIIT-Hyderabad  

### Mohamed Shawky

>**mohamedshawky911**AT**gmail**DOT**com**  
RoboComp Developer  
Cairo University  

### Araceli Vega

>**avegamag**AT**alumnos**DOT**unex**DOT**es**  
Researcher, Robolab  
University of Extremadura  


