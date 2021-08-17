## Introduction

AGGLPlanner is the planification tool of AGM. As any planner, AGGLPlanner function is to design a plan. AGGLPlaner works differently than most modern planners. This planners needs a full instantiation of the world, which can be very low efficient in certain cases, like dynamic worlds, huge worlds or when the actions are inherently complex.	

For this reason AGGLPlanner works performing a A* search, so it’s not necessary to instantiate all the world states. To use AGGLPlanner we need to execute the following command:

agglplan file1.aggl file2.xml file3.xml 

The aggl file contains the ruleset that we want to apply to our world. The initial world itself is in the file2.xml, and the file3.xml contains the objective we want to reach. 

## Porting AGGL Planner (Part 2)

As we saw in the previous post, I was stuck in  a missing function error. The missing function was intended to generate the target from an xml file. After talking with my mentors, we decided that AGGLPlanner would not accept xml as target files anymore. This decision was made with the aim of simplifying the program, since the .aggt format also allows more things than the .xml format. This change also required that I convert some goal files from xml format to .aggt format so I could test the program properly with the new goal entry format.

Once this error was solved, I had to face some more common errors, but nothing very remarkable, until we reached the parsing files of the program. Despite the fact that we don't use xml files as goal files anymore, the initial world can still be in xml format. For that reason, we need to parse that world.xml so the program can understand the information of the world. 

In Python 3 the library and the functions used to parse xml files changed. As a result of this, after a few days trying to adapt the original xml parsing code to python 3 without success, both me and my mentors decided to remake the parser from zero as a new file, called py3xmlparser.py

After completing this file and testing it properly, I had to face a few more simple problems before the scheduler started working. After getting AGGLPlanner to work in python 3, I tested it extensively to make sure there were no hidden errors. With this last testing phase the AGGLPlanner porting phase was completed.

