# Google Summer of Docs 2019 Ideas

April 14th 2019

## IDEAS LIST for GSoDs 2019

### A gentle introduction to RoboComp
**Mentors**  

 
**Brief description**  
The aim of this project is to generate a general documentation of RoboComp that provides the user with all the necessary material to understand the fundamentals of RoboComp and start using the framework. This documentation will include:  
* An introduction to component-based programming.
* Software components in RoboComp.
* Installation guide of RoboComp.
* Description of RoboComp’s tools and libraries. 


**Needed skills**  



### Creating RoboComp’s components
**Mentors**  

 
**Brief description**  
RoboComp provides tools to automatically generate the basic software structure of components and their interfaces. These tools are based on domain specific languages through which the RoboComp developer specifies components (CDSL) and interfaces (IDSL)...  

**Needed skills**  


### RoboComp’s basic components
**Mentors**  

 
**Brief description**  
RoboComp includes a wide set of ready-to-use components for different robotic applications. These components deal with different important issues in Robotics such as low-level perception, motor control, localization and mapping, navigation, recognition (people, objects, ..), etc. Despite the variety of functionality, the usability of these components is limited since most of them lack a proper documentation. This project aims to solve this situation by documenting each one of the basic components of RoboComp. This documentation will include a description of the function of the component, an explanation of every method it offers and specific issues about its configuration. In addition, a more general documentation will be generated providing examples of how to use these basic components in new projects to solve well-known problems in Robotics. 

**Needed skills**  



### RCIS: the robot simulator of RoboComp
**Mentors**  

 
**Brief description**  
RCIS is the robotic simulator of the RoboComp framework. This simulator is very useful for multiple purposes. It can simulate complex worlds and provides a hardware abstraction layer for simulated robots that facilitates testing robot behaviours without modifying the code of the high-level components. The robot and its environment are described through a kinematic tree expressed in an XML file. Nodes of the tree represent entities in the world and geometric transformations among them.  The basic relationship among elements is "part_of" meaning that a child is rigidly attached to her parent and will move with it. Nodes can be geometric (transform, translation, rotation), bodies (mesh, planes), robots (differential robot, omni-robot), sensors (laser, imu, rgbd) and actuators (joints). RCIS implements interfaces of robot devices to allow other components to communicate with the simulated robot. These devices are configured in the XML file representing the simulated world, assigning specific port numbers to those elements of the simulated robot. This project will provide all the necessary documentation to allow the user for creating new simulated worlds and robots to be used in RCIS. In addition, the documentation will describe the software structure of the tool and how to extend it to implement new devices that contribute to the creation of new simulated robotic platforms.

**Needed skills** 

