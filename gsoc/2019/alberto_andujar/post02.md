# Developing a Serious-Game using RoboComp: First steps

Jul 10, 2019
 
## Introduction

Our ultimate goal is to be able to develop a web application that allows to manage the execution of different serious-games developed by RoboComp staff. That is to say, its general functionality is that of a control panel that allows to execute and monitor different games, as well as manage users. The games are designed specifically for elderly people. Therefore, we need to develop a web application to monitor the state of the game, launch, stop or pause its execution, as well as, visualize and store their scores, among other features. And on the other hand, somehow we must connect the behavior of the serious-games with our web application, therefore, in conjunction with the developers of RoboComp we must write an API Rest that serves as a means of connection between both applications.

To develop our web application we have selected a versatile set of tools. The decision is based on my previous experience and the recommendations of my mentors. We decided to use the framework for developing  web applications: Angular.io, mainly because of my knowledge about him and because it is undoubtedly a suitable environment for developing web applications.

We have also decided to write it using TypeScript. This has been a challenge for me, as I did not know it and I have been learning it in the last weeks. Once again, the GSOC slot allows me to grow as a developer and increase my knowledge as a programmer.

The new features of Zeroc Ice will allow us to communicate RoboComp with the web application. However, we have not yet definitively defined the API Rest to connect the web application that we will develop with RoboComp. Before that, and in order to correctly define it, we have gone through an analysis and design phase to get the best definition and to know in greater depth the problem we face.

RoboComp also had a beta version of the application developed as a component. Therefore, first an analysis of the previous program has been done. We believe that we can take advantage of the design of the interfaces created with Qt for the new application. Therefore, we have analyzed the interfaces defined in the component, to adapt them during the coming weeks to the web version developed with Angular.

## Analysis of the existing component in RoboComp.

In this section, I will show the different screens of the existing component in robocomp, along with a brief description of its behavior. In the same way, its most important elements will be explained.

![capture_1](alberto_andujar/capture_5.jpeg)

- The first screen we find is the typical login screen, its transformation into the new version is simple. This screen should check that the user is actually in the system and provide access.
The behavior to add a new user automatically is not implemented in the component but it will be in the web version.

![capture_2](alberto_andujar/capture_4.jpeg)

- Once the user has logged into the system, a number of options related to his profile will be displayed. Basically you have to choose a serious game and start the session.   A session may consist of more than one game. These will run sequentially. Therefore, it is possible to add more than one game before starting. 

![capture_3](alberto_andujar/capture_3.jpeg)

- Before starting the game, an informative window appears with the characteristics of the game. This allows the user to check that he has chosen the correct game before starting. The user is also allowed to end the session if necessary.

![capture_4](alberto_andujar/capture_2.jpeg)

- The control panel will implement a system of alerts and notifications in real time, such as the one shown in the figure, which occurs when the game does not detect the hand of the patient on the table.

![capture_5](alberto_andujar/capture_1.jpg)

- While the game is running, the application will refresh the game information.  It can be seen that it is the same screen as Figure in which the start and end session buttons have been disabled. At the same time the pause and end buttons have been enabled. These refer to the execution of the current game.
This screen shows general information about the serious-game, as well as  real time information related to the game execution.


* * *
*José Alberto Andújar*
