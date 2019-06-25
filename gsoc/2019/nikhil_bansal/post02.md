# Creating scene objects, Move a non-motor and motor object, obstacle sensing, headless mode

June 22, 2019

[![N|Solid](./RoboComp_logo.png)](https://nodesource.com/products/nsolid)


### In order to write components in python, we first need to find the ways to:

  - **Convert Scene files of RoboComp written in XML to .ttt scene file types supported in V-REP**
    - There are some old posts on vrep forum asking the same:
      - http://www.forum.coppeliarobotics.com/viewtopic.php?t=437
      - http://www.forum.coppeliarobotics.com/viewtopic.php?t=4783
    - The above posts describe some ways use xml in vrep, but they are not properly described and are not concrete.
    - One other way is to convert ttt to some plain text format.


  - **Need a way to remotely connect to the scene simulation in V-REP:**
    - We decided to use: [Legacy remote API](http://www.coppeliarobotics.com/helpFiles/en/legacyRemoteApiOverview.htm)
    - [Remote API function list](http://www.coppeliarobotics.com/helpFiles/en/remoteApiFunctionListAlphabetical.htm)


  - **Creating objects in the scene remotely using python script:**
    - The primitive shapes can be created using the regular API function: [sim.createPureShape](http://www.coppeliarobotics.com/helpFiles/en/regularApi/simCreatePureShape.htm).
      - Only the cuboid, cone, sphere and cylinder can be added via this function.
    - But, only a limited remote API functions are available in V-REP([Python Remote API functions List](http://www.coppeliarobotics.com/helpFiles/en/remoteApiFunctionsPython.htm)).  To use the regular API function, one can use:
      - the generic remote API function [simxCallScriptFunction](http://www.coppeliarobotics.com/helpFiles/en/remoteApiFunctions.htm#simxCallScriptFunction), this will call a V-REP script function, which can then execute any type of operation locally, then return data.
    - I have created a test script describing the procedure to create the primitive scenes in a vrep scene:
      - [https://github.com/nikhil3456/V-REP/blob/addTestScripts/components/ebo/object_add.py](https://github.com/nikhil3456/V-REP/blob/addTestScripts/components/ebo/object_add.py)


  - **Moving an non-motor objects in the scene (eg Primitive shapes):**
    - V-REP has no functionalities to give a velocity to such objects.
    - But, we can move such objects by changing their position in each iteration of the loop using the function “simxSetObjectPosition (regular API equivalent: [sim.setObjectPosition](http://www.coppeliarobotics.com/helpFiles/en/remoteApiFunctionsPython.htm#simxSetObjectPosition))" API function”.
    - See the file “[cuboid_control.py](https://github.com/nikhil3456/V-REP/blob/addTestScripts/components/ebo/cuboid_control.py)” for more details on moving such objects.


  - **Moving the motors in vrep and sense the obstacles in VREP**
    - See the file “[moveMotorAndSenser.py](https://github.com/nikhil3456/V-REP/blob/addTestScripts/components/ebo/moveMotorAndSenser.py)” for more details on this.

  - **Running the vrep in headless mode:**
    - A scene named "scene.ttt" can simulated in V-REP using the following command:
      ```sh
      ./vrep.sh -h -s5000 -q scene.ttt
      ```
    - Refer this link for detailed description: [Headless mode](http://www.coppeliarobotics.com/helpFiles/en/commandLine.htm)


## Remote Controlled V-REP

##### Wrote a Library, available at [https://github.com/nikhil3456/VrepLibrary](https://github.com/nikhil3456/VrepLibrary) ([Reference](https://github.com/ctmakro/vrepper)), that could correctly handle the following routine:

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


#### Usage

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
- Refer the following example files:
1. [object_add.py](https://github.com/nikhil3456/VrepLibrary/blob/master/object_add.py)
2. [cuboid_control.py](https://github.com/nikhil3456/VrepLibrary/blob/master/cuboid_control.py)
3. [moveMotorAndSenser.py](https://github.com/nikhil3456/VrepLibrary/blob/master/moveMotorAndSenser.py)

## Todos

 - Find a way to convert Scene files of RoboComp written in XML to .ttt scene file types supported in V-REP.
 - Find a way to simulate a scene as fast as possible i.e super-real time simulation in headless mode


***
Nikhil Bansal

