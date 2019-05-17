# Post01: Introduction

May 16, 2019

## About me
I am third year Computer Engineering student at the Open University of Catalonia. I studied first a degree in Nursing at University of Sevilla, and I have been working in several hospitals since then. Since I was a child, I have been fascinated by computers, and it was my interest in them what has inspired me to start this new study.

I have developed diverse projects at the university, in which I have worked with many computer languages. On one hand, I have proficient skills with C/C++ and Java, since most of the programs that I have written were in those languages, and I am currently learning Python on my own. On the other hand, I have also become familiar with different Integrated Development Environments such as Eclipse, Visual Studio or CodeLite. Furthermore, I am always ready and happy to learn new languages and tools.

I have knowledge of Computer Science fundamentals, data structures, algorithms, networks and software design. I have also studied the basic machine learning algorithms and models. Experienced working with both Windows and Linux.

With respect to my communication skills, my mother tongue is Spanish, and I am fluent in English and German.

## About the project
RoboComp is an open source robotics framework that affords the tools to create and modify software components. These components communicate through different interfaces and can be created and modified by the tool robocompdsl.

Until now, this tool can only be executed from the command line and its mainly functions are to generate a CDSL template and the code of an existing component or CDSL file. To make the user experience more enjoyable and to avoid programming errors it is proposed in this project to create a graphical interface for robocompdsl.

The implementation of the GUI will consist in a creative and interactive layout with the respective buttons and menus. Our main goals will be to:
-	Design a user-friendly interface
-	Avoid errors in the code.

There is a current version of robocompdsl-gui written in python 2.7 with PySide. It already includes the basic features that we want to develop, so we have carried out some tests to evaluate its shortcomings. The first thing we could improve is Python and PySide versions to more updated technologies, such as Python3 and PySide2. The second proposed improvement is to debug errors while creating the CDSL file. For example, there are some glitches when selecting the communication interfaces, that will cause errors executing the component.

In order to avoid programming mistakes while creating a valid CDSL file, we could implement a validator. It could be used to check if the user has only chosen a valid combination of elements to create the component. For example, the validator will check if the selected interfaces are installed on the system. On the other hand, the graphical interface could be directly used as a validator to avoid a wrong code generation.

Turning to the graphical interface, it might be built with several frameworks. After the discussion with mentors, we propose to develop our GUI using Python3 and Pyside2 (QT5), as we could reuse the existing code. As RoboComp is currently updating its system, we agreed that developing our tool using these new versions would be a good choice. Although we will use the existing GUI as a grounding, it does not mean that we have to keep the same structure if we consider that it must be turned into something completely different.

The graphical interface main operations would be:
-	Create Component/interface
-	Modify existing component

The initial idea is to design a window where the user can add and modify the different available options using boxes, buttons and menus. All the process should be intuitive and provide very visual information, similar to a game.

The elements to take into consideration while creating the CDSL file are:
-	Name of the component: the user must enter the name of the component that he wants to create.
      -	Conditions: alphanumeric, no spaces or symbols.
-	Interfaces to import: interfaces that the component needs to work. They should be added automatically depending on the selected communication interfaces.
      -	Conditions: IDSL files.
      -	Example of available elements: Camera.idsl, GPS.idsl, Laser.idsl, Joystick.idsl.
-	Communications Interface: to create communications. Validator must check used interface existence.
      -	Implement: creates RPC server.
      -	Requires: creates Proxy to RPC Server.
      -	Publish: creates publication proxy to a specific topic.
      -	Subscribes to: subscribes to a specific topic.
-	Language: selected language in which the component will be written.
      -	Cpp: implements component using C++.
      -	Cpp11: implements component using C++11 to allow to use ICE implementation.
      -	Python: implements component using Python 2.7.
-	Window type (GUI): Includes visual interface in different windows types.
      -	QWidget.
      -	QDialog.
      -	QMainWindow.
-	Optional parameters:
      -	Agmagent: includes Cortex-Agent communication patterns.
      -	InnerModelViewer: includes innerModelViewer resources.
      -	New option modules: To incorporate third-party libraries to component. This option must be also modified in actual robocompdsl-core functionality.

After the discussion with mentors, we agreed to add the option “Modules”. It will allow to generate the code to link with other tools. This new feature will be created adding some code to the file robocomdsl-core.

At the end of the process a CDSL file will be created and processed to generate the new code of the component in the selected language. We can reuse the existing Robocompdsl-core to extract the required information of this file.


