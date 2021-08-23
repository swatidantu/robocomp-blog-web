## Introduction

AGMPlanner is a dsr-graph component builded in C++ created by me. The objective of this agent is to use the interface named AGGLPlanner.idsl and defined in the component AGMPlannerPython, another component of dsr-graph. 

This interface executes the plannerr AGGLPlanner, part of the Robocomp module AGM. The objective of AGGLPlanner is to design a plan. For this it needs a few params: The ruleset file (.aggl), the initial world file (.xml/.JSON), the goal file (.aggt), and, at last and as a optional param,  the result plan file (.plan).

The objective of this component is to make a bridge between the python component and the other dsr-graph agents, so the other agents can call the planner in an easy way. The structure is designed like this because it is more efficient to use the python code in the python agent than call a subprocess, and most dsr-graph does not support python components.

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

As you can see, the robocomp interface that both components use is AGGLPlanner.idsl. The interface has one function and one struct parameter that contains the arguments needed.






## AGMPlanner

As we said before, the AGMLPlanner is the C++ component. Here we have the most important part of this component code:

RoboCompAGGLPlanner::Parameters ParameterList;
  ParameterList.pythonarg = "python3 ";
  ParameterList.agglplanarg = "../../../../AGM/AGGLPlanner/agglplan.py ";
  ParameterList.agglfile = "examples/logistics/domain.aggl "; //Ruleset
  ParameterList.initfile = "examples/logistics/init0.xml "; //init world xml
  ParameterList.aggtgoal = "examples/logistics/prueba0.aggt "; // goal file
  ParameterList.resultplan = "examples/logistics/resultado.plan "; //plan result file
 
  this->agglplanner_proxy->AGGlplannerexecution(ParameterList); //Calling the interface implemented in AGMPlannerPython component.
  printf("done\n");

As we can see, we set the params that the planner is gonna need and we call the interface function AGGLplannerexecution. We will see the implementation of this function on the  next post: AGMPlannerPython.
