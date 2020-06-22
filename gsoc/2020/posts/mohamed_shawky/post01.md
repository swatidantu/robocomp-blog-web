# GSoC'20 RoboComp DNN’s for precise manipulation of household objects
 
_DATE : June 1, 2020_
 
## About me
 
My name is __Mohamed Shawky__. I'm a Computer Engineering BSc. student at Cairo University. My main interest is Deep Learning. This is my first participation in GSoC. This year, I will be working on a pose estimation and grasping component with RoboComp.

- __Interests :__ Deep Learning, Computer Vision, Robotics, Reinforcement Learning and Distributed Systems.


## About the Project

In this project, we will work to integrate a pose estimation component to RoboComp using some state-of-art work in Deep Learning. The output poses will be visualized in CoppeliaSim simulator and used to drive the new Kinova Gen3 arm, in order to precisely grasp and manipulate some objects.

[Segmentation-driven 6D Object Pose Estimation](https://arxiv.org/abs/1812.02541) architecture is to be used as our primary choice for pose estimation. The network will be trained on [YCB videos dataset](https://rse-lab.cs.washington.edu/projects/posecnn/), as it's the most diverse open source-dataset for pose estimation. Other architectures can be considered too, as well as augmenting the dataset with RGBD data collected from simulator. 

The network implementation is almost finished, then we will start the training and tuning phase. Once we reach a good pose estimation model, it will be integrated in a component to test the grasping performance.

__Mohamed Shawky__
