# Google Summer of Code 2018 Ideas

23 Jan 2018

## General information on applications

This is the list of ideas for the Google Summer of Code 2018, if you are interested in any of the ideas listed below or you think you can propose something interesting to improve RoboComp we encourage you to apply. 

* It is important to first familiarize with the software ([https://github.com/robocomp/robocomp](https://github.com/robocomp/robocomp)). 
* You can go through the available tutorials and direct your questions to the mailing list or gitter chat (listed below, also see contact section). 
* Please read all the information posted in this page before applying. 
* Make sure you are familiar with the required skills for the idea. 
* Since several of the mentioned RoboComp tools and components are not explained here to keep this list short, we encourage everyone to check the RoboComp documentation linked below. 
* Mentors and backup mentors are listed right after the idea explanation. All mentors contact info is at the end of the page. Contact them directly for specific questions on the idea.

Robocomp installation and tutorials: [https://robocomp.readthedocs.io/en/highlyunstable/](https://robocomp.readthedocs.io/en/highlyunstable/)

**Where can I start and what to include on my application?**

You are encouraged to go through these steps for a better understanding and follow-up of your application:

1.  Download and install RoboComp: [https://github.com/robocomp/robocomp/blob/master/README.md](https://github.com/robocomp/robocomp/blob/master/README.md).
2.  Follow the tutorials: https://github.com/robocomp/robocomp/blob/master/doc/README.md.
3.  Once you are familiar with RoboComp and the components and tools involved in the particular idea you want to contribute to, try to understand how these components/tools work and, if possible, their design.
4.  Participate in the mailing list asking any question you might have.
5.  Create a schedule with the milestones you plan to follow during the GSoC 2017 program.
6.  **Send the schedule and any code you might have written along with your CV and other application materials to the mentor of your idea and the backup mentor.**

For general questions about RoboComp please use: The [developers list](https://groups.google.com/forum/?hl=es#!forum/robocomp-dev) and the [gitter chat](https://gitter.im/robocomp/home).

NOTE:  If you send this by email make sure to also submit your application through the official GSoC website otherwise you will not be considered for the programme.

## IDEAS LIST for GSoC 2018

### 1\. RCManager extended functionalities: a tool to deploy and monitor large sets of components. 

 
Currently RoboComp has a tool to deploy components that is being improved through several GSoC editions. It’s name is RCManager and is used on a daily basis by all the people that use RoboComp to program robots. Since this tool is crucial to the software development process and since robot software is all the time increasing its complexity as a large-scale distributed system, we need to improve this tool as much as we can. 
* The first extension is to make the tool access remote RoboComp installations to create a list of potential components to be added to the deployment set.
* The second extension tackles the need to group sets of components into higher order entities, so visualization is simplified.
* A third extension is to include the capability to probe the edges in the graph of components so a pop-up window would show in real time the traffic moving through it. When connections between components use publish/subscribe modality the probing is easy, but when communication is done using the pull/request modality things get more complicated.

Where to start and what to include in my application?

1. Run a test with the RCManager tool and understand how it works
2. Have a look at the tool’s code and check for how to make modifications so a deployment file can be automatically generated in a painless way through the tool
3. Provide some example of a small modification or improvement in the tool.


Technologies involved: Qt5, C++, Python, Zeroc ICE
Mentor: Esteban Martinena, Pablo Bustos
Backup mentor: Luis J. Manso

### 2\. RCIS: improving RoboComp simulator with contact physics

### 3\. RCIS: improving RoboComp simulator with transmission delays

RCIS is RoboComp’s robotics simulator. It is built using the OpenSceneGraph 3D engine as the visual renderer. Over the years we have tuned RCIS to suit or needs for robot software development. Despite the mature state of the software we need to add more functionalities to cope with the increasing complexity of our social robots. One of these new functions is the simulation of different kind of transmission delays that occur when the real robot is running. Ignoring these delay may even cause that a nice simulated result is almost useless in a real-world execution. The goal of this project is to design, model and include a set of realistic delay into RCIS so simulations get closer to real-world results. These delays will include transmission, hardware and computational factors.

Technologies involved: C++, Python, Qt5
Mentors: Luis Manso, Pilar Bachiller
Backup mentor: Pablo Bustos

### 4\. Emotion recognition component for Learnbot 

Learnbot is a small low-cost robot designed to develop computational thinking in kids of age 10 and above. Learnbot is programmed using a block language specifically designed for it. Through this language, kids program robot behaviors in an easy way by specificating what the robot has to to do whenever a given situation occurs. The last version of Learnbot has been equipped with a display that provides it with the possibility to show “emotions”. This way, kids can program not only motor behaviors, but also emotional reactions. To improve the HRI functions in Learnbot and extend the situations that make it to exhibit different emotional behaviours, we want to add new skills in the robot that allow it to recognize emotions in people such as happy, sad, angry, scared, … These new skills will be developed as a Robocomp component in charge of detecting people faces, recognizing basic emotions on them and providing its results to other components demanding this kind of information.

Technologies involved: C++, Python, Qt5, OpenCV3
Mentors: Pilar Bachiller, Iván Barbecho
Backup mentor: Marco A. Gutiérrez

### 5\. Improving the Human-centered Robot Navigation Agent

Currently, RoboComp provides robots with the capability to behave in a socially acceptable manner. Particularly, the strategy followed in our Social Navigation Agent is based on the definition of regions where navigation is either discouraged or forbidden (personal spaces). These regions are related with the Proxemics, which defines spaces that humans mutually respects during an interaction. The navigation architecture combines the Probabilistic Road Map and the Rapidly-exploring Random Tree path planners and an adaptation of the elastic band algorithm to include the social behaviour. All of them are part of different RoboComp components. Considering the complexity of this task, the use of the current version of the social navigation agent is restricted, since it does not analyse, for instance, the human intentions during the robot navigation (do the human want to interact with the robot?) or the size of  personal space depending of context (personal space should be different in a corridor than in a big room). 

The task at hand here would be to integrate improvements in the existing RoboComp Social Navigation Agent. In a future version of this agent, more complex situations will be taking into account, such a s human intention analysis and/or adaptive personal spaces. A typical case of use would be that of a group of humans walking in different environments while the robot performs a task. All these simulations would be made using RCIS (RoboComp InnerModel Simulator)

Technologies involved: C++, Python, Qt5,  
Mentors: Pedro Nuñez, Luis Manso


## Mentors:

### Marco A. Gutiérrez

marcogATunexDOTes
Robocomp Developer

### Pablo Bustos

pbustosATunexDOTes
Professor, RoboLab,
University of Extremadura

### Luis J. Manso

lmansoATunexDOTes
Postdoc Researcher, RoboLab,
University of Extremadura

### Ramon Cintas

rcintasATunexDOTes
Researcher, Robolab,
University of Extremadura

### Esteban Martinena

emartinenaATunexDOTes 
Robocomp Developer

### Pedro Núñez

pnuntruATunexDOTes
Professor, RoboLab,
University of Extremadura

### Pilar Bachiller

pilarbATunexDOTes
Professor, RoboLab,
University of Extremadura

### Ivan Barbecho

ibarbechATalumnosDOTunexDOTes 
Researcher, Robolab,
University of Extremadura

### Nicolas Gonzalez

nicoATunexDOTes
Developer, Robolab,
University of Extremadura

