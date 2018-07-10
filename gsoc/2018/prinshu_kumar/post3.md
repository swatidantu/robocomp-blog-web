# Setting the configuration of the Robot dynamically

I have created the form through which the configuration of the robots can be set dynamically. The ```use Default``` button which sets the configuration corresponding to the connection of the robots of /learnbot/learnbot_simulator/version_2.1/learnBot2WorldDSL_lines.xml file. Then the two robots can be programmed and run simultaneously.

# Publishing using the paho-mqtt

Paho-mqtt package of the python has been used to connect to the other Robots. MQTT is a connectivity protocol designed for M2M. It is an extremely lightweight publish/subscribe messaging transport that is ideal for connecting small devices connected on networks with minimal bandwidth. Every function that the robot uses publishes on the topic "Robot" <Robot id> <Message>. An example of the ```move_left``` function looks like this :

```
from __future__ import print_function
import time
def move_left(lbot, duration=0.05, advSpeed=20, rotSpeed=-0.25, verbose=False):
	lbot.setRobotSpeed(advSpeed, rotSpeed)
	lbot.publish_topic("move_left")
	if duration != 0:
		time.sleep(duration)
```

An example of the published information looks like this:
``` Robot 1 'move_left' ```

# Subscribe function for users :
I have also created an additional tab 'collaborative' which looks like this:
![collaborative](images/subscribe.png)

I have also created a block namely ``` subscribe ``` which takes two argument. The first one is the robot id to which the user wants to subscribe and the second one is the waiting time to which the program should wait. An example looks like this :
![Example](images/example.png)

In the above example ```Robot 2``` waits for 10 second. If the ```Robot 1``` moves left within that time then the other Robot moves Right.
