# 17th June, 2017

# Introducing a new software architecture

Hola guys ! Last week saw some major structural changes in the code design of RCManager. The idea was essentially proposed by my mentor and we had a thorough discussion on its pros and cons. 

Earlier on, we just had two python script files which handled all of its functionalities. Let us call them main.py and config.py, for the sake of simplicity. The function definitions for the GUI components (menubar, buttons etc.), the code to draw the graph and handle the text editor etc. was stored in the config.py. The main.py was responsible for importing the config.py, initializing the GUI window and loading the xml file. Technically, the RCManager code was correct, however, it lacked a clear cut boundary between the roles of the two files. Any new developer trying to add a new feature would immerse himself into the dilemma of where to put the new code. Even if this dilemma stood resolved, a monolithic code design is still very cumbersome to maintain and debug.  

My mentor proposed the idea of incorporating the MVC software architecture into RCManager, which is a very popular way of building user interfaces for systems. Voracious readers can go to this [wikipedia link](https://en.wikipedia.org/wiki/Model%E2%80%93view%E2%80%93controller) to know more. I will briefly describe how I implemented it for RCManager.

Let us start with the major file components of the new RCManager. We now have 4 major files - main.py, model.py, viewer.py and controller.py. Their description is as follows:

1) **model.py** - This file is an abstraction of how the component graph is internally stored in RCManager. We use the NetworkX library to represent a component graph and add only those functions to this file which are necessary for mutating the graph (say add nodes, delete edges, etc.).

2) **viewer.py** - This file is solely responsible for the GUI. It initializes the GUI window and includes all the functions definitions for the GUI components and the necessary event handlers. This is completely independant of the model.py.

3) **controller.py** - This file holds the objects for the model.py and the viewer.py and loads the xml file. It acts as the link between the model.py and the viewer.py. It issues function calls to both of the objects. The model and the viewer can interrupt the controller by sending signals, using the PyQt signal / slot mechanism. (Will describe this in a later blog).

4) **main.py** - This file spawns the objects - M (model type) and V (viewer type) and initializes the controller object with M and V.

There are a few more files which will be described later. The whole idea to segregate independent components of the manager into separate files, so that the code looks cleans and maintenance / development becomes easier. Stay tuned for the upcoming blogs on this amazing tool.

* * * 

[Mayank Kumar](https://github.com/Kmayankkr/)

Email - kr.mayank1997@gmail.com

