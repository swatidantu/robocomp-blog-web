# Google Summer of Code 2018 Ideas

23 Jan 2018

## General information on applications

This is the list of ideas for the Google Summer of Code 2018, if you are interested in any of the ideas listed below or you think you can propose something interesting to improve RoboComp we encourage you to apply. 

* It is important to first familiarize with the software. 
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

For general questions about RoboComp please use: The [developers list]((https://groups.google.com/forum/?hl=es#!forum/robocomp-dev) and the [gitter chat](https://gitter.im/robocomp/home).

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


Needed skills: Javascript, Python, Cog(python module)
Mentor: Esteban Martinena, Pablo Bustos
Backup mentor: Luis J. Manso



## Mentors info

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

