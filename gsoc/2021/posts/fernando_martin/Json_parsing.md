##Introduction

After getting AGGLPlanner to work in python 3, my mentors asked me to add a new feature to the project: Being able to work with initial world files in JSON format.

This request is due to the fact that in the current work environment of my mentors, the world used by the DSR is in JSON format. This means that in order to use the scheduler as it was originally designed, it would have been necessary to convert the JSON world to xml before giving said world to the scheduler, something inefficient, especially if we have to execute the scheduler many times during the robot's execution, since each of these executions would require a conversion.

 
##Designing the JSON parser file

To enable AGGLPlanner to work with JSON input files, two main tasks had to be performed.

The first consisted of modifying the main code of the program, located in agglplan.py (and agglplan2.py if we want to use the second form of execution of the program), so that the program can detect what format the world file has.

Once the first task was done, the second was to carry out this parsing process. For this, a new file called pyJSONparser.py was created. This file contains everything necessary to parse the world file to the data format used by the scheduler.

This last task also required extensive testing to make sure that the parser was working correctly. To do this, I had to convert the existing example xml files and translate them to JSON. In addition to these files, I also used some files that my mentors provided me, and that are taken directly from the worlds that they use in their robot simulations.
