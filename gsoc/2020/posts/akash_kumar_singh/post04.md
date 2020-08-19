# Adding ROS2 support in robocompdsl (Design)

This post will talk about how we shifted from "Porting innermodel lib from C++ to Python" to "Adding
ROS2 support in robocompdsl (Design)" and what this project is all about. Later we will talk about
the problems that `robocompdsl` already had, problems with ROS1, and how we changed some of the design
of the component.

- So this project "Python3 binding for innermodel" was inteded to be for porting all the InnerModel
  APIs from C++ to Python using PyBullet and Numpy. We worked vigorously about 1.5 months, when we
  realised that it will be finished way before the time. So we began considering to work on other
  projects of which we choose `robocompdsl`. So, if anybody don't know what `robocompdsl` is, it is the
  most important and one of the first robocomp tools that you are going to interact with when starting
  with robocomp. `robocompdsl` is a tool to generate a component from a .cdsl file. At the time
  `robocompdsl` was quite basic, only able to generate components with ICE middleware and the parser
  was quite broken. It couldn't even do the things it was supposed to do like creating components with
  ROS middleware.

- So our aim with the new project "ROS2 support for robocompdsl" was to first fix the ROS1 support
  and then add the support for ROS2.

- One of the first things that I noticed in the initial stages of development was that many features
  of the `robocompdsl` that it was supposed to do were not working. The `.cdsl` parser was broken. We
  couldn't specify which middleware to use in the component. It wasn't working for even ICE. So I had
  to fixed that first.

- The generated code for ROS1 was not even compiling, so I had to first fix ROS1 code generation and
  then move on to the ROS2.

- For ROS2 one of the major challenges was to figure out how to compile it with cmake. Since ROS2 is
  different from ROS1 in a considerable way, and so was its build system.

- The second most important difference was the way in which ROS `msgs/srvs` are built in both ROS
  versions. In ROS1 we have a script that can generate the necessary header files for `msg` files and
  `srv` files and then built those for the `msg/srv` headers to be included in the `genericworker.h`.
  While on the otherhand it is very complicated in ROS2 to directly generate the headers file because
  of the inherent design of the ROS2 which uses 3 different implementation DDS protocol. Something
  like this cant be handled by a single python script and so cmake MACROs are used instead.

- Next problem was not with the ROS2 but with ROS1, the inconsistent design with different communi-
  cation modes (`publishes, subscribesTo, implements, requires`). For example: for `publishes` mode in
  ROS1 there is a dedicated class of publishers with the name of interface specified, while for the
  `subscribesTo` mode in ROS2 there are callbacks written inside the `GenericWorker` class which makes
  it inconsistent. So what I have done is make a class for all the modes. A single class will handle
  all the things ROS. This class is instantiated in `GenericWorker` class and can be used through it.
