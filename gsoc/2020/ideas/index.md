# Google Summer of Code 2020

03 Feb 2020

## IDEAS LIST for GSoC 2019

### 1\. Human-robot dialogue and collaboration for social navigation
**Mentors**  
Juan Carlos García, Pedro Núñez
 
**Brief description**  
The navigation of a robot in an environment with humans is a subject with enormous interest in the last years. To be accepted in these types of scenarios, it is important that the robot navigate respecting social norms, for example, avoiding getting too close to humans, avoiding interrupting a conversation or asking permission to pass through a blocked path. The aim of this slot is to describe the dialogue manager, besides the corpus that allows establishing dialogues between the robot and the humans in real situations in order to improve the behaviour of the robot navigation system, making it more socially accepted. The dialogue manager should be a RoboComp agent, which reads information from the robot’s world representation (a graph) and adapts the conversation to the current situation (e.g, according to the age of people, genre, etc). The idea of this slot is to select open-source technologies such as  PyText orl Rasa NLU (https://rasa.com/).  

**Needed skills**  

### 2\. Development of graphical user interfaces for robot controlling and monitoring
**Mentors**  
Pedro Núñez, Araceli Vega
 
**Brief description**  
The complexity of robots is increasing year by year. The functionalities to navigate, to detect objects, to recognize people, to interact with humans, etc are challenges that nowadays the scientific community tries to solve. However, it is clear that all these modules do not work properly in most robots, or their functionality is incomplete.  In this project, we propose the design of user interfaces that allows different functionalities to teleoperate the robot and generate inputs/outputs directly by the user (without the need of having an implemented module). 
Among these functionalities, the user interface must allow to send the robot to a specific position, rotate, talk to humans (TTS), enter the response manually (like a ASR). Many of these actions will be simulated directly by the user, adding all the necessary information in the cognitive architecture of the robot. 

**Needed skills**  
 C++, Python, Qt5.

### 3\. Randomly generation and storage of the graph-based world representation used in RoboComp
**Mentors**  
Luis V. Calderita, Ramón Cintas
 
**Brief description**  
Currently, RoboComp keeps in real-time the state of the robot and the world around it. For this, RoboComp uses a graph-based world representation that evolves over time. This graph represents the robot's perception of its environment and is maintained by the sensors onboard the robot.

The aim of this slot is twofold, on the one hand, it is intended to include a tool that can store the evolution of the robot's world representation. To do this, the idea is to represent the graph in JSON format and store it in a document-oriented database such as MongoDB. This first part aims to introduce the student to the concept of world representation used in RoboComp and to RoboComp itself. Once graphs are stored, the second objective is to identify the most similar graph to a given one. To find this similarity among graphs, we pretend to use Machine Learning techniques, specifically Graph Neural Networks. Consequently, we need a tool to generate huge data sets automatically based on the stochastic sampling of a formal spatial grammar encoding all valid worlds. State of the art GNN learning algorithms will be used to obtain a metric over the space of graphs. 
A final feature of the slot is to facilitate the human supervision of the learning process.  The representations generated and retrieved will be rendered using a physics-based robotic simulators  Our interest currently lies in the V-REP simulator, already supported by RoboComp, to render the stored graphs and help in the search process.

**Needed skills**  
Python3, Qt5,  MongoDB,  JSON, XML, V-REP.

### 4\. Efficient acceptable social behaviour using machine learning techniques
**Mentors**  
Daniel Rodriguez, Pilar Bachiller
 
**Brief description**  
The detection and implementation of social skills is usually handcrafted by developers writing hardcoded if-then-else constructs in the robots’ code. This code usually consists of a series of queries to the robots’ world representations (e.g., if the robot is closer than 400mm to a human the person might consider the behaviour inappropriate, if two humans are interacting the robot should not interrupt their visual contact). Although this is a valid approach, it is very time consuming and scales poorly. The aim of this slot is to improve the efficiency of the component in charge of this, generating a heat map instead of a single value per query. The input information to compute such heat maps will be the robot’s world representation (a graph) and the output a two-dimensional array. The machine learning techniques used will be Graph Neural Networks and Convolutional Neural Networks. We will be building on top of a similar slot that took place last year. The current implementation is available at https://github.com/robocomp/sngnn.

**Needed skills**  
Python, DGL/Pythorch-geometric.

### 5\. RoboCompDSL: new functionalities for more resilient components
**Mentors**  
Pablo Bustos, Esteban Martinena
 
**Brief description**  
Currently, RoboComp uses a code generation tool, RoboCompDSL, to generate C++ and Python components. This tool uses two different domain-specific languages, one to define components (CDSL) and another one to define interfaces (IDSL). We have seen that the mode code is generated, the fewer errors a programmer makes when creating components. In this task, we want to extend these languages to include features that will make more resilient components. An example of what we have in mind for IDSL files (in red new language features),

struct Data
{
	int cameraId[range=0:10];    // asserts to control range of 	parameters’ values.
	int width[range=320,640,1280];
	int height;
	int depth;
};

interfaceCamera[pub-sub]
{
	void newPeopleData (Data people[buffer=on] );  / /thread safe interchange buffer in final code
};

Interface Robot[action]   // all declared actions must be asynchronous and provide a getStatus method
{
	void gotoPoint(int x, int y, float angle[range=-pi:pi]);
	Status getStatus();
};

interface Camera[query]
{
	Image = getImage();
};

**Needed skills**  
Python,C++11,  RoboComp, Formal languages.

### 6\. Beautify LearnBlock
**Mentors**  
Iván Barbecho, Luis V. Calderita
 
**Brief description**  
LearnBlock is an educational programming tool developed for learning programming through robotics. It has been designed to facilitate the learning process starting with a visual language and progressing towards a professional programming language. LearnBlock includes many interesting features: robot-agnostic design; blocks can be created from code without modifying the core code of the tool; robots can be programmed using different languages (visual, Block-Text or Python); a program can be run and interrupted from the tool itself, ensuring proper stop and disconnection of the robot. 

To make LearnBlock more appealing, this project aims to beautify the tool by creating new shapes for the blocks composing the visual language. Thus, blocks will be redesigned and integrated into LearnBlock. In addition, new types of connections will be defined to reduce potential syntactical errors. Besides these changes, a new and more intuitive method for changing the input parameters of the blocks (for instance, rotation and translation speed in a block in charge of moving the base of the robot) will be defined and implemented. All these modifications will be included with little impact in the core code of the tool.

**Repository**  
[https://github.com/robocomp/LearnBlock](https://github.com/robocomp/LearnBlock)

**Needed skills**  
Python3, Qt.

### 7\. Syntax-error highlighter for LearnBlock
**Mentors**  
Pilar Bachiller, Iván Barbecho
 
**Brief description**  
LearnBlock is an educational programming tool developed for learning programming through robotics. It has been designed to facilitate the learning process starting with a visual language and progressing towards a professional programming language. Specifically, the user can choose whether to create a program from blocks, from the textual representation of blocks (Block-Text) or coding in Python. The final code executed by the robot is Python code. This final code is generated from the Block-Text code created by the user or obtained from the visual code. If a syntax error is found in the Block-Text code, the Python program is not generated and LearnBlock informs the user that an error was found. However, no message about the specific error is shown.

The aim of this project is to endow LearnBlock with the ability to determine the different syntax-errors of a program and to display those errors in both, the visual program and the Block-Text code. Those parts of the code containing a syntax-error will be highlighted. In addition, information about the kind of error and some guidelines on how to correct will be displayed as long as the user asks for it (for instance, clicking on a highlighted statement or block).

**Repository**  
[https://github.com/robocomp/LearnBlock](https://github.com/robocomp/LearnBlock)

**Needed skills**  
Python3, Qt, PyParsing

### 8\. Hand gesture recognition
**Mentors**  
Aditya Aggarwal, Francisco Andrés
 
**Brief description**  
Hand gesture recognition is very significant for human-robot interaction. It can be used as a tool of communication between humans and robots. It can be further extended to a component that can understand sign language and provide a user-friendly way of communication with the robots.

This component can have a 2 stage pipeline. The first stage will involve detecting hand and estimating hand shape & pose. These can be used as features for the second stage which can be a classifier based on similarity score. Large public image datasets are also available which can be used to train these models.

**Needed skills**  
Python, RoboComp, Tensorflow or PyTorch.
Required Domain Knowledge: ComputerVision.

### 9\. Python3 bindings for the InnerModel library
**Mentors**  
Luis J. Manso, Ramón Cintas 
 
**Brief description**  
InnerModel is RoboComp’s geometry and world model representation library. It is used to compute geometric transformations, projections, transformation matrices and even to visualise the robots’ internal world models. Although it is heavily used in most RoboComp components, the Python bindings currently available are very limited and have not been properly tested in Python 3. The aims of this slot is to complete the Python bindings and develop the corresponding unit tests to ensure the API is working as expected. The current wrapper implementation uses Boost-Python, but it would be possible to try other alternatives.

**Needed skills**  
Python, C++.

### 10\. Human recognition (identification) using multi-modal perception system
**Mentors**  
Pedro Núñez, Diego Faria
 
**Brief description**  
Detecting people in an environment is a task of enormous interest for robotics. In addition, the ability to identify the person among a finite number of users is a very interesting challenge for later complex tasks such as personalized interaction, social navigation, etc. The aim of this project is to implement a software agent with RoboComp that allows, from a multi-modal RGBD sensor, the identification of people in the robot environment. The identification should not only use the face of the detected people, but also using other information related to the skeleton or silhouette of the body, even with semantic information previously extracted (or manually introduced from a GUI). 

**Needed skills**  
Python, RoboComp.
Required Domain Knowledge: Computer Vision.

### 11\. Kinova Gen3 test components using VREP
**Mentors**  
Pablo Bustos, Francisco Andrés
 
**Brief description**  
Kinova Gen3 is a state of that art robot manipulator with 7 DoFs and a two-finger gripper. It also includes an RGBD camera in the wrist. All motors have torque sensors. Kinova provides a high-quality programming SDK for Python and C++. We also have Gen3’s model for the VREP simulator. In this task, we want to create RoboComp components that embed Kinova’s SDK and offer our well-known interfaces. Also, we want to create a couple of scenarios to test the robot in actions. One test scenario can involve classical planning algorithms for the blocks world, and another one can use more recent learning techniques such as Deep Reinforcement Learning. The physics enabled simulator VREP will be of great help for remote working and running learning algorithms.

**Needed skills**  
Python, C++11, RoboComp, V-REP.

### 12\. RoboComp/ROS integration
**Mentors**  
Francisco M. Rico, Luis J. Manso
 
**Brief description**  
This slot aims to endow robocompdsl --RoboComp’s component generation tool-- with the ability to generate ROS2 components based on CDSL descriptions and to ensure that the currently available integration with ROS1 is working properly. To this end, the student working in this project will update the C++ and Python3 templates and generate a set of unit tests to ensure that the integration is correct and to facilitate the early detection of bugs.

**Needed skills**  
Python3, C++17, RoboComp.

### 13\. Automatic and systematic generation of Robocomp components for testing
**Mentors**  
Esteban Martinena, Pablo Bustos
 
**Brief description**  
RoboComp is a Robotics framework based on software components. Building new components is done using the domain-specific language CDSL. RoboComp currently has the rocobocompdsl tool to generate and modify components based on this language and files. 
One of the biggest problems to make changes to the robocompdsl tool or to any of the specific domain languages used in RoboComp is that any minimal change implies the need to test many different variations and possibilities of the component generation tool to be sure that no bug has been introduced. This slot is aimed at creating a new tool that uses the CDSL grammar to automatically and systematically create new valid .cdsl files, create empty components from those cdsl files, compile, and report. This way, a full test of the component generation could be executed anytime that a new change is introduced to robocompdsl. This tool will be a great addition to the current tools of the RoboComp framework.

**Needed skills**  
Python, RoboComp Formal Languages.

### 14\. Live topic translation for ROS (and others) with System Of Systems Synthesizer
**Mentors**  
Marco A. Gutierrez, Ramon Cintas
 
**Brief description**  
The System of Systems Synthesizer (SOSS) is a software meant to connect the messages sent between different communication middlewares. Up to now it supports messages from systems like ROS1, ROS2, websockets, fiware and DDS. The communication is configured in a yaml file and when SOSS is launched messages on one system will be directly translated from one to the other. 

RoboComp communications are handled by the Ice communications middleware by zeroC, by enabling SOSS with Ice support we will be able to connect RoboComp components to a new wide range of systems and applications.

**Needed skills**  
Python, RoboComp, C++, ICE, Yaml.

### 15\. Software agent for estimating occupancy in medium and large buildings using RGB cameras
**Mentors**  
Sergio Barroso, Araceli Vega
 
**Brief description**  
Measuring the number of people (occupation) in an environment is a problem of great interest in different areas of research. Today there are different techniques to estimate the number of people in a small-medium sized room/class by using different sensors. Among these sensors we can use infrared, RGBD cameras, thermal cameras, CO2 measurement sensors... 
The idea of this project is to provide RoboComp with a software agent that, from RGB images,estimates the occupancy in crowded environments. The possibilities are several, but we consider here the use of deep learning techniques for the detection of skeletons, faces, etc, to infer the number of people in a robust way. 

Moreover, the agent must also consider its extension to the use of different cameras that register the access to a large building from different points of view, and the logic of occupation control: who enters, who leaves...

**Needed skills**  
Python, RoboComp.

### 16\. Creation of DNN controlled components for RoboComp
**Mentors**  
Francisco Andrés, Carlos Muñoz
 
**Brief description**  
RoboComp is a Robotics framework based on software components. Building new components is done using a code generator based on the domain-specific language CDSL. Currently, the user can choose between two models of execution for new RoboComp components: sequential and state-machine controlled. This slot aims to create a new execution model for DNNs. The CDSL language will be extended to include the necessary new keywords and options. These new options will select which run-time tools (tensorflow, pytorch, caffe) and model formats will be included in the new component and the necessary dependencies. RoboComp’s parser and code generator will be modified to generate Python supporting the loading, initialization and execution of DNN models.  As an optional development, the CDSL language could be further extended to define multi-network structures such as sequential concatenation of DNN models to build more complex functions.

**Needed skills**  
Python, RoboComp, tensorflow, pytorch, caffe, formal grammars.


## Complete list of Mentors:

### Pablo Bustos

>**pbustos**AT**unex**DOT**es**  
Professor, RoboLab,  
University of Extremadura  

### Pilar Bachiller

>**pilarb**AT**unex**DOT**es**  
Professor, RoboLab,  
University of Extremadura  

### Luis J. Manso

>**l.manso**AT**aston**DOT**ac**DOT**uk**  
Lecturer in Computer Science,  
School of Engineering & Applied Science, Aston University, UK  
[http://ljmanso.com](http://ljmanso.com)

### Pedro Núñez

>**pnuntru**AT**unex**DOT**es**  
Professor, RoboLab,  
University of Extremadura  

### Aditya Aggarwal


### Francisco Andrés

>**pacoan**AT**unex**DOT**es**  
Lecturer, Robolab  
University of Extremadura  

### Ivan Barbecho

>**ibarbech**AT**alumnos**DOT**unex**DOT**es**   
Researcher, Robolab,  
University of Extremadura  

### Sergio Barroso

>**sbarmirez**AT**gmail**DOT**com**   
Researcher, Robolab,  
University of Extremadura  

### Luis V. Calderita

>**lvcalderita**AT**unex**DOT**es**  
Professor, RoboLab  
University of Extremadura  

### Ramon Cintas

>**rcintas**AT**unex**DOT**es**  
Researcher, Robolab,  
University of Extremadura  

### Diego R. Faria

>**d.faria**AT**aston**DOT**ac**DOT**uk**  
Lecturer in Computer Science,  
School of Engineering & Applied Science, Aston University, UK  

### Juan Carlos García

>**juancarlos97gg**AT**gmail**DOT**com**   
Researcher, Robolab,  
University of Extremadura  

### Marco A. Gutiérrez

>**marcog**AT**unex**DOT**es**  
Robocomp Developer
  
### Esteban Martinena

>**emartinena**AT**unex**DOT**es**  
Researcher, Robolab  
University of Extremadura  

### Carlos Muñoz

>**cmzar97**AT**gmail**DOT**com**   
Researcher, Robolab,  
University of Extremadura  

### Francisco M. Rico

### Daniel Rodríguez

### Araceli Vega

>**avegamag**AT**alumnos**DOT**unex**DOT**es**  
Researcher, Robolab  
University of Extremadura  


