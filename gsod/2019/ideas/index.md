# Google Season of Docs 2019 Ideas
RoboComp is an open-source robotic framework. It is made up of different robotic software components and the necessary tools to use them. The running components form a graph of processes that can be distributed over several cores and CPU’s using software component technology. Communications are handled by ZeroC’s Ice middleware. Our main goals in designing the system are efficiency, simplicity and reusability. To achieve these goals, components are created by a code generator that reads a simple description program written in a Domain Specific Language named CDSL. Components created with this tool are formally correct and provide an advanced starting point for the user to start coding. All communication aspects, project creation files, auxiliary libraries, internal concurrency and interchange data structures and initial documentation are provided with the generated code. Programming languages used in the project are mainly C++ and Python but the Ice framework makes possible to easily use components written in many other languages.  


## IDEAS LIST for GSoDs 2019

April 22th 2019

### A gentle introduction to RoboComp
**Mentors**  
Pablo Bustos, Pilar Bachiller
 
**Brief description**  
The first idea offered for the new GSoD program is the integration of many separate pieces of information already existing into a coherent introduction to the framework, A Gentle Introduction to RoboComp, that can guide new users through the initial steps of understanding, installing, coding, deploying and testing with this tools. This manual might include several sections such as:  
* An introduction to component-based programming.
* Software components in RoboComp.
* Installation guide of RoboComp.
* Description of RoboComp’s tools and libraries. 
* Quick reference guide of basic components.  

This documentation should be created for a new RoboComp’s user. No details about the implementation of the framework are required at this level. A tool like ReadtheDocs or similar is advised to support dense hyperlinks inside and outside the text.  



**Needed skills**  
Basic knowledge of OO programming in C++ and Python  


### Creating RoboComp’s components
**Mentors**  
Luis J. manso, Pilar Bachiller
 
**Brief description**  
RoboComp provides a powerful code generator to automatically create the basic software structure of components and their interfaces. This tool is based on two domain-specific languages with which the RoboComp developer defines components (CDSL) and interfaces (IDSL). This idea aims to create a guide to define groups of interconnected components using well-defined interfaces. Thus, the documentation will provide the specification of the CDSL and the IDSL according to their syntaxis, reserved words, etc. Different issues related to the creation of components will be included, such as implementing new interfaces, creating components from existing interfaces or including interfaces to communicate with other components. In addition, the structure of generated components will be detailed from the perspective of the proficient programmer, specifying not only those parts of the component that should be modified to include the specific functionality of the component but also fixed parts of the code that are automatically generated. Finally, additional documentation to explain how to create a deployable file with all necessary elements such as binaries, configuration files or interfaces will be added to the project.  

**Needed skills**  
Basic knowledge of OO programming in C++ and Python  

### RoboComp’s basic components
**Mentors**  
Ramón Cintas, Esteban Martinena
 
**Brief description**  
RoboComp includes a wide set of ready-to-use components for different robotic applications. These components deal with different important issues in Robotics such as low-level perception, motor control, localization and mapping, navigation, recognition (people, objects, ..), etc. Despite the variety of functionality, the usability of these components is limited since most of them lack proper documentation. This project aims to solve this situation by documenting each one of the basic components of RoboComp. This documentation will include a description of the function of the component, an explanation of every method it offers and specific issues about its configuration. In addition, a more general documentation will be generated providing examples of how to use these basic components in new projects to solve well-known problems in Robotics.  

**Needed skills**  
Basic knowledge of OO programming in C++ and Python  


### RCIS: the robot simulator of RoboComp
**Mentors**  
Luis V. Calderita, Pedro Núñez
 
**Brief description**  
RCIS is the robotic simulator of the RoboComp framework. This simulator is very useful for multiple purposes. It can simulate complex worlds and provides a hardware abstraction layer for simulated robots that facilitates testing robot behaviours without modifying the code of the high-level components. The robot and its environment are described through a kinematic tree expressed in an XML file. Nodes of the tree represent entities in the world and geometric transformations among them.  The basic relationship among elements is "part_of" meaning that a child is rigidly attached to her parent and will move with it. Nodes can be geometric (transform, translation, rotation), bodies (mesh, planes), robots (differential robot, omni-robot), sensors (laser, imu, rgbd) and actuators (joints). RCIS implements interfaces of robot devices to allow other components to communicate with the simulated robot. These devices are configured in the XML file representing the simulated world, assigning specific port numbers to those elements of the simulated robot. This project will provide all the necessary documentation to allow the user for creating new simulated worlds and robots to be used in RCIS. In addition, the documentation will describe the software structure of the tool and how to extend it to implement new devices that contribute to the creation of new simulated robotic platforms.  

**Needed skills** 
Basic knowledge of OO programming in C++ and Python  

## Complete list of Mentors:

### Pablo Bustos

>**pbustos**AT**unex**DOT**es**  
Professor, RoboLab,  
University of Extremadura  


### Luis J. Manso

>**l.manso**AT**aston**DOT**ac**DOT**uk**  
Lecturer in Computer Science,  
School of Engineering & Applied Science, Aston University, UK  
[http://ljmanso.com](http://ljmanso.com)

### Pilar Bachiller

>**pilarb**AT**unex**DOT**es**  
Professor, RoboLab,  
University of Extremadura  

### Pedro Núñez

>**pnuntru**AT**unex**DOT**es**  
Professor, RoboLab,  
University of Extremadura  

### Luis V. Calderita

>**lvcalderita**AT**unex**DOT**es**  
Professor, RoboLab  
University of Extremadura  

### Ramon Cintas

>**rcintas**AT**unex**DOT**es**  
Researcher, Robolab,  
University of Extremadura  

### Esteban Martinena

>**emartinena**AT**unex**DOT**es**  
Researcher, Robolab  
University of Extremadura  

