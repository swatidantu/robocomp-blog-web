# Integrating V-REP with RoboComp as an external simulator and as an in-the-loop simulator

June 22, 2019

[![N|Solid](./RoboComp_logo.png)](https://nodesource.com/products/nsolid)



## Goals:

  ### Need a way to remotely connect to the scene simulation in V-REP
  - To control the simulation running in V-REP, we need a way to remotely connect to the simulation to control the objects in the scene.
  - **Advances:**
    - We decided to use: [Legacy remote API](http://www.coppeliarobotics.com/helpFiles/en/legacyRemoteApiOverview.htm), which allows to control a simulation (or the simulator itself) from an external application.
    - The [Remote API function list](http://www.coppeliarobotics.com/helpFiles/en/remoteApiFunctionListAlphabetical.htm) is the list of functions that can be used to control the simulation remotely.

  

  ### Convert scene files of RoboComp written in XML to .ttt scene file types supported in V-REP

  - The scene files (like simpleworld.xml) of RoboComp are in .xml format, so, our goal is to convert these xml file to the filetype supported by V-REP.
  - V-REP supports binary file format with .ttt extension.


  - **Advances:**
    - The following are posts on the vrep-forum, that enquire about converting xml/text files into .ttt files:
      - http://www.forum.coppeliarobotics.com/viewtopic.php?t=437
      - http://www.forum.coppeliarobotics.com/viewtopic.php?t=4783
    - V-REP does not directly support XML. We can however write XML importers/exporters. For writing importers/exporters, we can use the source code of the COLLADA importer/exporter, or the URDF importer plugins as reference.
    - Or, another way is to go through the whole set of elements in the scene using the Python API and write them in a file using a text format (innermodel for instance). This, way we can go from ttt to other readable file formats.

  

  ### Creating objects in the scene remotely using python script
  - We need the ability to create the objects in the scene(running in V-REP) remotely via a python script.
  - **Advances:**
    - There are no Remote API function to create objects in the scene. So, we can use the regular API function: [sim.createPureShape](http://www.coppeliarobotics.com/helpFiles/en/regularApi/simCreatePureShape.htm) to create objects. But, regular API functions cannot be used in a remote script.
      - So, to use a regular API function, one can use:
        - the generic remote API function [simxCallScriptFunction](http://www.coppeliarobotics.com/helpFiles/en/remoteApiFunctions.htm#simxCallScriptFunction), this will call a V-REP function in the embedded script in scene, which can then execute any type of operation locally, then return data.
      - I have created a test script describing the procedure to create the primitive scenes in a vrep scene:
        - [https://github.com/nikhil3456/V-REP/blob/addTestScripts/components/ebo/object_add.py](https://github.com/nikhil3456/V-REP/blob/addTestScripts/components/ebo/object_add.py)

  

  ### Moving an non-motor objects in the scene (eg Primitive shapes)
  - We might require the ability to move a non-motor object in the scene.
  - **Advances:**
    - V-REP has no functionalities to give a velocity to non-motor objects.
    - But, we can move non-motor objects by changing their position in each iteration of the loop using the function “simxSetObjectPosition (regular API equivalent: [sim.setObjectPosition](http://www.coppeliarobotics.com/helpFiles/en/remoteApiFunctionsPython.htm#simxSetObjectPosition))" API function.
    - I have created a test scripts that demonstrates how we can move a non-motor objects:
      - See the file “[cuboid_control.py](https://github.com/nikhil3456/V-REP/blob/addTestScripts/components/ebo/cuboid_control.py)” for more details on moving non-motor objects.

  


  ### Moving the motors in vrep and sense the obstacles in VREP
  - We might need the ability to move the motors in the scene remotely.
  - We also need the ability to sense the obstacles/nearby-objects in the scene. 
  - **Advances:**
    - We can set the velocity of motor/joint using the Remote API function: 'simxSetJointTargetVelocity'.
    - We can sense the nearby obstacles/objects by adding a proximity sensor to our robot in the scene and then using the Remote API function "simxReadProximitySensor" to get the position and other details of objects near the robot.
    - I have created a test scripts that demonstrates the above mentioned functionalities:
      - See the file “[moveMotorAndSenser.py](https://github.com/nikhil3456/V-REP/blob/addTestScripts/components/ebo/moveMotorAndSenser.py)” for more details.
  


  ### Running the vrep in headless mode:
  - We need the ability to run V-REP simulation of a scene and the associated scripts in headless mode(i.e. without any GUI).
  - **Advances:**
    - A scene named "scene.ttt" can simulated in V-REP using the following command:
      ```sh
      ./vrep.sh -h -s5000 -q scene.ttt
      ```
      - -h: runs V-REP in headless mode (i.e. without any GUI)
      - -sXXX: automatically start the simulation. XXX represents an optional simulation time in milliseconds after which simulation should stop again.
      - -q: automatically quits V-REP after the first simulation run ended.
    - Refer this link for detailed description: [Headless mode](http://www.coppeliarobotics.com/helpFiles/en/commandLine.htm) on running V-REP in headless mode.

  



## This section describes the Library to Remotely Control V-REP

- With the help of the library: 
  - We can now run our script with just one command eg: "python script.py"
    - The above command will automatically starts vrep in headless mode (as a subprocess) and perform the control using script.py (eg: moving an object, obstactle detection etc) and store the data and prints the data on terminal.

- The Library, available at [https://github.com/nikhil3456/VrepLibrary](https://github.com/nikhil3456/VrepLibrary), can correctly handle the following routines:

  1. Start a V-REP instance from Python
  2. Connect to the instance you've started
  3. Load the scene file (the scene we are about to simulate)
  4. Start the simulation
  5. Step the simulation
  6. Read/Write something from/to V-REP to control the simulation and record data
  7. Goto 5 several times
  8. Stop the simulation
  9. Check to see if the simulation actually stopped.
  10. Goto 4 several times
  11. Kill the V-REP instance from python if no longer needed.


- For testing the library
  1. Clone this repository: [https://github.com/nikhil3456/VrepLibrary](https://github.com/nikhil3456/VrepLibrary)
  2. Open the file VrepLibrary/moveMotorAndSenser.py in your favourite editor.
  3. Change the arguments of this line 'venv = vrepper(dir_vrep='/home/nikhil/V-REP_PRO_EDU_V3_5_0_Linux/', headless=True)'.
    - dir_vrep: denotes the path to vrep directory.
    - headless: denotes whether to start the simulation in headless mode or not.
  4. Save the above file
  5. Run 'python moveMotorAndSenser.py' 




#### Instructions on writing python script that uses above Library

A python script to start the simulation (following above routine) in headless mode, can be written using following functions:
```sh

from vrepper.core import vrepper

# create a vrepper object using the following command:
# dir_vrep is the path to vrep directory.
# port_num denotes the port on which to start vrep(if port_num=None then a random port will be assigned)
venv = vrepper(port_num=None, dir_vrep='/home/nikhil/V-REP_PRO_EDU_V3_5_0_Linux/', headless=True)

# Start a V-REP instance
venv.start()

# To load a scene after creating V-REP instance:
venv.load_scene(current_dir + '/scenes/scene.ttt')

# start simulation in realtime mode to set initial position
venv.start_simulation(is_sync=False)

```

- See the following "[Readme.md](https://github.com/nikhil3456/VrepLibrary/blob/master/README.md)"  for detailed description.
- Refer the following example files for detailed description:
  1. [object_add.py](https://github.com/nikhil3456/VrepLibrary/blob/master/object_add.py)
  2. [cuboid_control.py](https://github.com/nikhil3456/VrepLibrary/blob/master/cuboid_control.py)
  3. [moveMotorAndSenser.py](https://github.com/nikhil3456/VrepLibrary/blob/master/moveMotorAndSenser.py)

## Todos

 - Find a way to convert Scene files of RoboComp written in XML to .ttt scene file types supported in V-REP.
 - Find a way to simulate a scene as fast as possible i.e super-real time simulation in headless mode


***
Nikhil Bansal

