# Work Done with DSR Integration

_DATE : August 20, 2020_

In this post, I discuss the work done with pose estimation and grasping integration with DSR and show some results and issues.

## DSR Integration Progress

Refer to the previous post for full description of pose estimation and grasping DSR workflow.

The process of integrating pose estimation and grasping with DSR goes as follows :

-   First, I had to finish a complete component of pose estimation, which is [objectPoseEstimation](https://github.com/robocomp/grasping/tree/master/components/objectPoseEstimation), a combination of both RGB and RGBD pose estimation. This component doesn't operate directly on the shared graph, however it's a separate component that is used to estimate objects' poses from RGBD to guide the grasping procedure.

-   Consequently, a component has to be developed to act as an interface between the shared graph and `objectPoseEstimation` component. That is [graspDSR](https://github.com/robocomp/dsr-graph/tree/development/components/graspDSR) component, which is a DSR agent responsible for reading the RGBD data from the shared graph, passing it to `objectPoseEstimation` component and injecting the estimated poses in the shared graph.

-   Since the final object pose can, sometimes, be hard to reach by the robot arm, `graspDSR` component has to progressively plan a set of dummy targets for the arm to follow, in order to reach the final target object. In other words, `graspDSR` component plans some keypoints on the path from current arm pose to the estimated object pose.

-   Doing so, [viriatoDSR](https://github.com/robocomp/dsr-graph/tree/development/components/viriatoDSR) agent passes the dummy targets to [viriatoPyrep](https://github.com/robocomp/dsr-graph/tree/development/components/viriatoPyrep) component, which moves the arm, using these targets, by calling the embedded Lua scripts in the arm, until the arm reaches the final target object.

-   Also, we need many DNN Python components that acts like services to the C++ agents interacting with DSR. Consequently, we created a new Github repository named [DNN-Services](https://github.com/robocomp/DNN-Services), which contains all the DNN components that serve DSR agents, including object detection and pose estimation.

-   __In conclusion,__ our DSR system consists of :
    -   An interface component that interacts with the external environment, which is real or simulated environment.
    -   The shared memory (G), which holds the deep state representation (DSR) of the environment.
    -   Agents, which are C++ components that interact with the graph through RTPS.
    -   DNN services, which are Python components that perform learning tasks, like perception and others.

-   Next, I tried the arm grasping in DSR system on simulator poses and a simple setting, in order to check the validity of the embedded Lua scripts in DSR settings. Here is a quick example :

<div align="center">
<a href="https://www.youtube.com/watch?v=83SGiT_gWkU"><img src="https://img.youtube.com/vi/83SGiT_gWkU/0.jpg" alt="IMAGE ALT TEXT"></a>
</div>

<div align="center">
Figure(1): Video of first grasping demo with DSR using simulator poses.
</div><br>

-   At the same time, I started developing `graspDSR` through the following steps :
    -   Connect `graspDSR` to `objectPoseEstimation`, where `graspDSR` reads all RGBD data from the shared graph and then calls `objectPoseEstimation` to get the estimated poses of the objects in the scene.
    -   Convert quaternions into euler angles and project the estimated poses from camera coordinates to world coordinates using `Innermodel sub-API`.
    -   Insert a graph node of the required object to be grasped and inject its DNN-estimated poses with respect to the world.
    -   Read the arm target graph node and check whether the required object is within the arm's reach.
    -   If so, plan a dummy target to get the arm closer to the object and insert that dummy target pose as the arm target pose in the graph.
    -   Repeat the previous steps, until the arm reaches the required target.

-   Finally, `viriatoDSR` reads the arm target poses and passes them to `viriatoPyrep`, which uses these poses to move the robot arm, progressively, towards the required object.

-   Thus, the pose estimation and grasping pipeline is completely integrated with DSR.

## Usage and Integration Problems

Refer to [DSR-INTEGRATION.md](https://github.com/robocomp/grasping/blob/master/DSR-INTEGRATION.md) in `robocomp/grasping` repo for detailed information about DSR usage and problems during integration. 

## Future Improvements

-   Solve the related [open issues](https://github.com/robocomp/robocomp/issues/created_by/DarkGeekMS) on `robocomp/robocomp` repo.

-   Update `viriatoDSR` to pass the arm target poses to `viriatoPyrep` from G.

-   Add grasping methods to `viriatoPyrep`, similar to `viriatoGraspingPyrep`.

-   Test the pose estimation and grasping pipeline with tracking and social navigation, once done.

## Important Dates

-   __August 16, 2020 :__

Complete the related DNN services (pose estimation and object detection with RetinaNet).

Commit : https://github.com/robocomp/DNN-Services/commit/8b7297fe1b211c65092039ac3a8a367836f075a6

-   __August 19, 2020 :__

Complete integration with DSR documentation

Commit : https://github.com/robocomp/grasping/commit/73afc5d211a1b34c1656b8310890fa70beed5661

-   __August 20, 2020 :__

Complete `graspDSR` component.

PR : https://github.com/robocomp/dsr-graph/pull/8

__Mohamed Shawky__
