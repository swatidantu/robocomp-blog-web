# My fourth post
28th June, 2018

## Explanation of other system parts
At this post I am going to explain other parts of the system that I have not explained before. The system, apart from the state machine, has a lot of things that must check all the time. As our program is a RoboComp component it has a *compute* method that is invoked continuously. This method allows us to do some previous things before the state in which the machine is has been executed. I call it main execution thread.

## Main execution thread
The main execution thread continuously runs the state machine as long as no error occurs. But, before starting the execution of the state in which you are, perform some calculations:
- Get from the RGBD camera, the system sensor, the color image matrix and the distance matrix. This is possible thanks to the fact that the camera is RGBD type and, therefore, it obtains the color image at the same time, such as the distance to each object from which it appears in the scene. Actually, it gets four channels for each pixel: level of red (R), level of green (G), level of blue (B) and distance of the pixel to the point in reality (D).

- *Innermodel* is updated with the position values of the robot in the world obtained in the previous iteration, in case of being the first iteration, they would remain the same. The status of the robot neck motors is also updated. To update, we use the functions from *innermodel*: *updateTransformValues* and *updateJointValue*, respectively.

- Equalize the camera image and draw the rectangles belonging to the objects obtained in the previous iteration, both, by the Yolo server and by our system. In the case of Yolo, a blue box is drawn if its probability is greater than 35 and in our system a green box. You can see it in next figure:

![Colour boxes](images/captura_camara)

- It is checked if any of the objects takes more than 15 seconds without being seen and if the motors do not finish moving. If this is true, the angle that each motor must move is calculated, so that, the object that takes more than 15 seconds without being seen enters in the robot's field of vision; the counter of all the objects in the system is reset and the motors are moved to the calculated position. This position is absolute from the zero position of both engines, thus, the calculation is simpler and the movement is direct towards a position. When the new iteration of the state machine begins, it will be checked if the object is already visible to the robot. To move the motors we use the following *jointMotor* component methods:
```C++
jointmotor_proxy->setPosition(head_yaw_joint);
jointmotor_proxy->setPosition(head_pitch_joint);
```
- The position difference between the current position of the motors and the previous iteration one is calculated. If this difference is significant, it is passed to the *Moving* state of the state machine. This is why, as explained in third post, from any other state it can be passed to the state *Moving*, since it only depends on whether an object takes a certain time without being observed.

To see the code [visit this link](https://github.com/ljmanso/objectDetection2/commit/a649fbb454e05b6d70e6e5fa67d8ec16655fb47c).
