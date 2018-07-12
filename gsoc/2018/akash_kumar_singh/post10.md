# Gazebo-RoboComp Integration: TimeLine

In this post I wanted to describe the whole progress that I made in these two months, the things I have done so far and how did I do it. So I have a separate repo where I have kept all the code away from the integration. This is nearly the same code which has been integrated in the code base. Here is the layout of the repo which can be found [here](https://github.com/kskash/gazebo-robocomp):

```
gazebo-robocomp
├── CMakeLists.txt
├── gazebo_plugins
│   ├── CMakeLists.txt
│   ├── include
│   └── src
├── gazebo_robocomp_models
├── gazebo_robocomp_msgs
├── gazebo_robocomp_worlds
├── ice-interface
│   ├── CMakeLists.txt
│   ├── include
│   └── src
├── README.md
├── slice
├── slice_cpp
│   ├── CMakeLists.txt
│   ├── include
│   └── src
└── src
```

I will be explaining the purpose of each of the component and the sequence in which I developed them.

## Plugins

My first aim was to write the gazebo plugins corresponding to sensors that could be used in the integration. The plugins had a direct access to the simulator so it was used to advertise all the data that it was able to get from the simulator to the ice interfaces using gazebo transport layer. I wrote 7-8 plugins, each one for a different purpose: `Laser`, `bumper`, `DifferentialRobot`, `Camera`, `DepthCamera`, `JointMotor`, `Motor` and `IMU`. These all had been put under the sub-directory `gazebo_robocomp_plugins`:

```
gazebo_plugins
├── CMakeLists.txt
├── include
│   ├── gazebo_robocomp_bumper.hh
│   ├── gazebo_robocomp_camera.hh
│   ├── gazebo_robocomp_DiffDrive.hh
│   ├── gazebo_robocomp_IMU.hh
│   ├── gazebo_robocomp_joint.hh
│   ├── gazebo_robocomp_jointmotor.hh
│   ├── gazebo_robocomp_laser.hh
│   └── gazebo_robocomp_RGBD.hh
└── src
    ├── gazebo_robocomp_bumper.cc
    ├── gazebo_robocomp_camera.cc
    ├── gazebo_robocomp_DiffDrive.cc
    ├── gazebo_robocomp_IMU.cc
    ├── gazebo_robocomp_joint.cc
    ├── gazebo_robocomp_jointmotor.cc
    ├── gazebo_robocomp_laser.cc
    └── gazebo_robocomp_RGBD.cc
```

I made a video for each plugin, demonstrating its working, which you can see [here](https://robocomp.github.io/web/gsoc/2018/akash_kumar_singh/post6). And, to know about the structure of the gazebo plugins which I made for this integration you can look [here](https://robocomp.github.io/web/gsoc/2018/akash_kumar_singh/post3). After I completed the plugins for all the important sensors and actuators, I tested it each one of them. I also wrote some application programs to check the working of `DifferentialRobot` plugin and `JointMotor` plugin in which are kept in the `src` directory.

## ICE interface

Then the next phase started. I started writing all the ice interface, that will act as a bridge between gazebo plugins and robocomp. For this I took the slice definitions of all the interfaces used by robocomp, modified them a little, based on what functonalities gazebo could offer. Source code for the interfaces was easy to get from the slice compiler. Then the methods in the source files were overridden, according to requirements needed to communicate with the gazebo plugins. To know more about the general code structure of slice deinition of all the interfaces one can look [here](https://robocomp.github.io/web/gsoc/2018/akash_kumar_singh/post7). The slice definitions can be found in the `slice` dir:

```
slice
├── bumper.ice
├── Camera.ice
├── CMakeLists.txt
├── CommonHead.ice
├── containers.ice
├── DifferentialRobot.ice
├── Exceptions.ice
├── GenericBase.ice
├── IMU.ice
├── JointMotor.ice
├── Laser.ice
├── Motors.ice
└── RGBD.ice
```

All the interfaces were tested and verified. They are working the way they are supposed to be. ICE interfaces are put inside the dir `ice-interface`:

```
ice-interface
├── CMakeLists.txt
├── include
│   ├── bumperI.h
│   ├── CameraI.h
│   ├── DifferentialRobotI.h
│   ├── IMUI.h
│   ├── JointMotorI.h
│   ├── LaserI.h
│   ├── MotorI.h
│   └── RGBDI.h
└── src
    ├── bumperI.cpp
    ├── CameraI.cpp
    ├── DifferentialRobotI.cpp
    ├── IMUI.cpp
    ├── JointMotorI.cpp
    ├── LaserI.cpp
    ├── MotorI.cpp
    └── RGBDI.cpp
```

## Gazbeo Messages

Gazebo plugins and ice interfaces use customized gazebo messages for communicating with each other, according to the needs of ice interfaces. Al the gazebo messages are put inside the directory `gazebo_robocomp_msgs`:

```
gazebo_robocomp_msgs
├── CMakeLists.txt
├── diffdrive_cmd.proto
├── diffdrive_state.proto
├── jointmotor_params.proto
├── jointmotor_state.proto
├── laser_data.proto
├── motor_goal_position.proto
├── motor_goal_pos_list.proto
├── motor_goal_vel_list.proto
├── motor_goal_velocity.proto
├── motor_params_list.proto
└── motor_state_list.proto
```

## Gazebo Models and Scenarios

In order to test all the plugins I needed to have a setup to test on. I added a number of models and worlds to the integration inorder to provide a varied number of models and situations for the devloper to test their code. There are number of useful models which is provided by the gazebo model database. All the models are included in `gazebo_robocomp_models` dir.

```
gazebo_robocomp_models
├── createROS
├── follower_vehicle
├── ground_plane
├── husky
├── irobot_hand
├── kinect
├── my_robot
├── noisy_imu
├── noisy_laser
├── person_standing
├── person_walking
├── pioneer2dx
├── pr2
├── ragdoll
├── robonaut
├── simple_arm_gripper
├── sun
├── turtlebot3_burger
├── turtlebot3_waffle
├── turtlebot3_waffle_pi
├── turtlebotROS
└── velodyne_hdl32
```

The different scenarios are kept under the dir `gazebo_robocomp_worlds`. There are a couple of them which are similar to scenarios provided by robocomp.

```
gazebo_robocomp_worlds
├── bumper.sdf
├── camera.sdf
├── DepthCamera.sdf
├── DiffDrive.sdf
├── IMU.sdf
├── joint.sdf
├── laser.sdf
├── my_world2.sdf
├── my_world3.sdf
├── my_world4.sdf
├── my_world5.sdf
├── my_world6.sdf
└── my_world7.sdf
```

## Structuring the code

Right after completing the above things and testing it, I wanted to reorganize the whole code in a proper way. First, I made a separate directory for `slice` definitions of interfaces with a `CMakeLists.txt` to produce source code from the `.ice` files and put it in the `slice_cpp`directory. `CMakeLists.txt` inside `slice_cpp` compiles the source code. All the customized gazebo messages are put inside the directory `gazebo_robocomp_msgs` and `CMakeLists.txt` inside it generates the necessary headers so that we can use the customized messages. Other application are included inside the `src` directory which were used to test plugins and interfaces. It also a keyboard controller plugin which enables to control a model by keyboard.

Most imortantly, it contains the `server` through which we one can actually connect with gazebo. It also consisted of a sample `client` just for testing the `server`. The demo video was shared [here](https://robocomp.github.io/web/gsoc/2018/akash_kumar_singh/post5). The main `CMakeLists.txt` in the project root directory includes all the dependencies of the integration.

## Testing the integration

To test the whole setup I made a robocomp with `Laser` only. Built it and the changed the address in the config file which contained the end point of `Laser` ice interface in the integration. It was not yet merged with the main code base, but it was nearly the same thing to do it this way.

## Merging with RoboComp code base

The final task was to merge the integration with the main code base of robocomp. It was not very tough to do it, if you knew what to do. I just put the whole `gazebo-robocomp` repo into the tool section in robocomp root directory, under the name of `gzserver`. Then I made a couple of changes in robocomp's dependencies to include the dependencies of the integration. Then I built the whole integration and it was successful. Then I installed it with the new tool being `gazeboserver`. I tested the whole integration with the robocomp component that I had described above, which can be found [here](https://github.com/ksakash/laserComp).

## Installing the Dependencies

Next I had to figure out how to install the dependencies of the integration. They were two major dependencies: `ice-3.6` and `gazebo-7`. Ice-3.6 can be installed using `sudo apt-get install` but to install the binaries for `gazebo-7`, it is more that. The installation for gazebo can be found [here](http://gazebosim.org/tutorials?tut=install_ubuntu&cat=install). This is the tentative method that is going to be used to installed `gazebo-7`.