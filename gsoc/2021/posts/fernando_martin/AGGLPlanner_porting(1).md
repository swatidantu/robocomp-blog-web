##Introduction

AGGLPlanner is the planification tool of AGM. As any planner, AGGLPlanner function is to design a plan. AGGLPlaner works differently than most modern planners. This planners needs a full instantiation of the world, which can be very low efficient in certain cases, like dynamic worlds, huge worlds or when the actions are inherently complex.    

For this reason AGGLPlanner works performing a A* search, so it’s not necessary to instantiate all the world states. To use AGGLPlanner we need to execute the following command:

agglplan file1.aggl file2.xml file3.xml 

The aggl file contains the ruleset that we want to apply to our world. The initial world itself is in the file2.xml, and the file3.xml contains the objective we want to reach. 

##Porting AGGL Planner

Now that we have a general idea of  AGGLPlanner, I am going to talk about how the process of porting the planner has been. Although most of the planner code is already ported, it is not complete yet. Also, AGGLPlanner has three running main files, which have some differences between them. These files are agglplan.py, agglplan2.py and agglplan3.py. 

Most of the problems that arose during the porting process were related to the grammar differences between python2 and python 3 (Parentheses, return syntax, etc). These errors, although common, are not difficult to resolve. It is for this reason that we are going to concentrate on the other main error that has arisen during the porting process: The adaptation of functions.

We already faced some of these errors in the previous phase, with, for example, pyside and pyside2. In this case, it was only necessary to change the references, and this has happened with some libraries that, although they no longer work in python3, have an updated version for it with the same functions names.

But, in the library errors there is another possibility, that they have changed from python 2 to python3. Although it is not so common, this error is more complex because it requires studying the functions of both the old and new libraries, and modifying the program to make an equivalence between what was done in python2 and what is done now in python3 with the new functions. This has happened to me for example with the thread library (now threading in python3).








## State of the porting process right now

agglplan.py is the main work mode of AGGLPlanner. In this moment i am facing a problem about a missing function, and my mentors and I are working to solve it. This error is not about the porting process itself, so we could say that, despite having to solve this, the porting process is mostly finished.

agglplan2 and agglplan3 are in an advanced state in the porting process, but still need some work on them.
