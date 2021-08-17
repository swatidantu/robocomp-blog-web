## Introduction

AGMPlannerPython is a dsr-graph component builded in python. The objective of this agent is to implement the interface named AGGLPlanner.idsl so the AGMPlanner can use it.

This interface executes the scheduler AGGLPlanner, part of the Robocomp module AGM. The objective of AGGLPlanner is to design a schedule. For this it needs a few params: The ruleset file (.aggl), the initial world file (.xml/.JSON), the goal file (.aggt), and, at last and as a optional param,  the result plan file (.plan).

The objective of this component is to import the python file and use the scheduler AGGLPlanner included in the AGM module. The original objective was this, but due to lack of time, right now AGMPlannerPython is creating a subprocess instead of use the scheduler as functions 

## AGGLPlanner.idsl

module RoboCompAGGLPlanner
{
    	struct Parameters
    	{
        	string pythonarg;
        	string agglplanarg;
        	string agglfile;
        	string initfile;
           string aggtgoal;
           string resultplan;
    	};
   	 
    interface AGGLPlanner
    {
   	 bool AGGlplannerexecution(Parameters arguments);

    };

};

As you can see, the robocomp interface that both components use is AGGLPlanner.idsl. As you can see the interface has one function and one struct parameter that contains the arguments needed.








## AGMPlannerPython

As we said before, the AGMLPlanner is the python component. Here we have the most important part of this component code:

  
    	#Final Version of the code
    	pythonarg = arguments.pythonarg # python3
    	agglplanarg = arguments.agglplanarg # the command to call the .py file
    	agglfile = arguments.agglfile # ruleset.aggl file
    	initfile = arguments.initfile # initialworld.xml/.json file
    	aggtgoal = arguments.aggtgoal # goalfile.aggt file
    	resultplan = arguments.resultplan # resultplan.plan file
    	#print the full chain before call the command line
    	cadenatotal = pythonarg+agglplanarg +agglfile + initfile +aggtgoal +resultplan
    	print("cadenatotal =")
    	print(cadenatotal)
   	 
    	os.system(cadenatotal)

In the code we can see that we are taking the arguments that we need from the variable “arguments”, a struct variable defined in the IDSL file that contains all the arguments that we need to use, and we execute a subprocess with all these arguments.

This is not optimal since importing the functions and calling them is more efficient than executing a thread. Unfortunately, due to lack of time, it is not possible to me to attack this problem since it is not only necessary to change the component, but it is necessary to modify the core of the scheduler since the python file of the scheduler works like a script right now.


    	


