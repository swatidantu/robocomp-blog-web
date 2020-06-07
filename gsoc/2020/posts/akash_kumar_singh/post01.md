# GSoC'20 RoboComp project: Python3 bindings for InnerModel lib

07th June, 2020

## About me

I am a pre-final year student in the Department of Electrical Engineering at the Indian Institute of Technology (IIT), Kanpur, India. I am a Robotics enthusiast, an avid developer and have a plethora of experience with development in C++ and Python. I have above-par knowledge of robotics frameworks like RoboComp, ROS, OpenCV, etc. having worked with them for the past couple of years.


## About the Project

**InnerModel** library is a group of C++ classes, in RoboComp's code base, which helps in describing the world and everything in it. It stores information provided by the `.xml` file in classes called `InnerModelNodes` & `InnerModelTransforms` and provides APIs to access and manipulate those nodes. `InnerModel` class in the innermodel lib can be considered as the core class which stores information in the form of tree data structure where each node can describe a mesh, sensor, geometric transformation, etc.

C++ as a programming language comes in handy in case of performance-oriented applications, for example, a simulator. But when it comes to rapid prototyping of applications and ease of use of APIs, it lags behind other languages like python which is one of the most widely used languages just because of this reason and also due to the plethora of libraries that it provides. So, porting all the C++ APIs to python can be helpful in extending the use of innermodel lib to beginner developers with minimal knowledge of programming. One can rapidly prototype an application by using python APIs. We are using `NumPy` lib for base classes for the math classes to have low latency on math operations. We are `Pybullet` lib, which is python binding for Bullet3 physics engine in C++, to render a scene and handle all the physics.

Akash Kumar Singh
