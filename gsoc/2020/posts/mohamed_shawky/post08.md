# Final Project Submission

_DATE : August 24, 2020_

This is the final post of `DNN’s for precise manipulation of household objects` project. Here, I show the work done and the results of the project. Also, I discuss some future improvements and link to all my contributions during the project.

## Brief Description

The ability of a robot to detect, grasp and manipulate objects is one of the key challenges in building an intelligent collaborative humanoid robot. In this project, I, __Mohamed Shawky__, worked with __RoboComp__ and my mentor, __Pablo Bustos__, to develop fast and robust pose estimation and grasping pipeline using the power of RoboComp framework and recent advances in Deep Learning. I used two recent DNN architctures, which are `Segmentation-driven 6D Object Pose Estimation` and `PVN3D` to build pose estimation component that estimates objects poses from RGBD images. Also, I was able to integrate the work done with Kinova Gen3 arm with PyRep API for a fast and robust path planning and grasping workflow. Finally, I worked on the integration of pose estimation and grasping into CORTEX archiecture (based on _Deep State Representation_ (DSR) and implemented using _Real-time Pub/Sub_ (RTPS) and _Conflict-Free Replicated Data Type_ (CRDT)).

## Completed Work

Here is a summary of all the work done through each period of the project.

### Community Bonding Period

-   [x] Communicated with my mentor, __Pablo Bustos__, to discuss the previous work on the grasping problem and form detailed project workflow.

-   [x] Familiarized myself more with RoboComp framework and 6D object pose estimation literature.

-   [x] Started working on `Segmentation-driven 6D Object Pose Estimation` network implementation based on open-source inference code.

### First Coding Period

-   [x] Completed a full implementation of `Segmentation-driven 6D Object Pose Estimation` network.

-   [x] Trained the network on `YCB-Videos` dataset, which is one of the most diverse open-source datasets.

-   [x] Tested the trained network on `YCB-Videos` dataset and data collected from `CoppeliaSim` environments.

-   [x] Implemented a Python data collector using _PyRep API_, _Open3D_ and _CoppeliaSim_ to collect more data for augmentation.

-   [x] Retrained the network on augmented dataset.

### Second Coding Period

-   [x] Improved the implementation of `Segmentation-driven 6D Object Pose Estimation` network through using focal loss and fixing some training issues.

-   [x] Retrained the network on the final settings.

-   [x] Investigated further improvements of pose estimation pipeline, which led me to `PVN3D` network.

-   [x] Studied `PVN3D` network and integrated its open-source implementation to a new RoboComp component.

-   [x] Completed two pose estimation components. One for RGB inference using `Segmentation-driven 6D Object Pose Estimation` network and another for RGBD inference using `PVN3D` network.

-   [x] Adapted the previous work with Kinova Gen3 arm to PyRep API, where I added _embedded Lua scripts_ to the arm's model and called them, remotely, through PyRep API. Thus, we have a fast and robust workflow for path planning and grasping.

-   [x] Implemented `viriatoGraspingPyrep` component, which integrates and tests the whole pose estimation and grasping pipeline.

### Third Coding Period

-   [x] Created the first complete grasping demo of Kinova Gen3 arm.

-   [x] Studied the workflow of the new DSR architecture through installation, testing and code review.

-   [x] Discussed the process of pose estimation and grasping integration into DSR with my mentor, __Pablo Bustos__.

-   [x] Merged both RGB and RGBD pose estimation components into one component, named `objectPoseEstimation`, for DSR integration.

-   [x] Implemented an object detection component that uses `RetinaNet` to improve object tracking in DSR.

-   [x] Implemented `graspDSR` C++ agent, which is an interface between `objectPoseEstimation` component and the shared graph (a.k.a. _G_). Also, it plans the dummy targets for the robot arm to reach the required object.

-   [x] Tested the validity of the arm's _embedded Lua scripts_ using DSR.

-   [x] Helped debugging and improving some features of DSR Core API.

-   [x] Wrote a detailed documentation about DSR integration and its problems.

-   [x] Improved visualization and memory allocation in pose estimation components.

-   [x] Revisited all the previous work and improved some documentation.

## Results and Demonstrations

<p align="middle">
  <img src="assets/collected_data_color.png" width="24%" />
  <img src="assets/collected_data_depth.png" width="24%" /> 
  <img src="assets/collected_data_label.png" width="24%" />
  <img src="assets/collected_data_viz.png" width="24%" />
</p>

<div align="center">
Figure(1): A sample of the collected output from the Python data collector.
</div><br>

<p align="middle">
  <img src="assets/output1.jpg" width="30%" />
  <img src="assets/output3.jpg" width="30%" /> 
  <img src="assets/output4.jpg" width="30%" />
</p>

<div align="center">
Figure(2): Visualizations of the estimated poses by Segmentation-driven 6D Object Pose Estimation on YCB-Videos dataset.
</div><br>

<p align="middle">
  <img src="assets/seg_pose_out.jpg" width="30%" />
  <img src="assets/pvn3d_out.jpg" width="30%" /> 
  <img src="assets/demo2_pred_pose.png" width="30%" />
</p>

<div align="center">
Figure(3): Visualizations of the estimated poses by objectPoseEstimation component in CoppeliaSim environment.
</div><br>

<div align="center">
<a href="https://www.youtube.com/watch?v=It7z-Ujf73U"><img src="https://img.youtube.com/vi/It7z-Ujf73U/0.jpg" alt="IMAGE ALT TEXT"></a>
</div>

<div align="center">
Figure(4): Demo of path planning using the DNN-estimated poses and the embedded Lua scripts.
</div><br>

<div align="center">
<a href="https://www.youtube.com/watch?v=lKk0_k8bjbY"><img src="https://img.youtube.com/vi/lKk0_k8bjbY/0.jpg" alt="IMAGE ALT TEXT"></a>
</div>

<div align="center">
Figure(5): Complete Demo of the arm grasping and manipulation using DNN-estimated poses without DSR.
</div><br>

<div align="center">
<a href="https://www.youtube.com/watch?v=83SGiT_gWkU"><img src="https://img.youtube.com/vi/83SGiT_gWkU/0.jpg" alt="IMAGE ALT TEXT"></a>
</div>

<div align="center">
Figure(6): Test demo of the embedded Lua scripts in DSR using the simulator poses.
</div><br>

## Contributions Summary

| __Repo__  | __Commits__ | __PRs__ | __Issues__ |
|-----------|-------------|---------|------------|
| [robocomp/grasping](https://github.com/robocomp/grasping) | [link](https://github.com/robocomp/grasping/commits?author=DarkGeekMS) | - | - |
| [robocomp/dsr-graph](https://github.com/robocomp/dsr-graph) | [link](https://github.com/robocomp/dsr-graph/commits?author=DarkGeekMS) | [link](https://github.com/robocomp/dsr-graph/pulls?q=is%3Apr+author%3ADarkGeekMS) | [link](https://github.com/robocomp/dsr-graph/issues?q=is%3Aissue+author%3ADarkGeekMS) |
| [robocomp/robocomp](https://github.com/robocomp/robocomp) | [link](https://github.com/robocomp/robocomp/commits?author=DarkGeekMS) | [link](https://github.com/robocomp/robocomp/pulls?q=is%3Apr+author%3ADarkGeekMS) | [link](https://github.com/robocomp/robocomp/issues/created_by/DarkGeekMS) |
| [robocomp/DNN-Services](https://github.com/robocomp/DNN-Services) | [link](https://github.com/robocomp/DNN-Services/commits?author=DarkGeekMS) | - | - |
| [robocomp/web](https://github.com/robocomp/web) | [link](https://github.com/robocomp/web/commits?author=DarkGeekMS) | [link](https://github.com/robocomp/web/pulls?q=is%3Apr+author%3ADarkGeekMS) | - |

## Future Work and Improvements

The work with this project has been completed successfully with full documentation and a decent set of demos. However, there is still some work to be done with DSR framework to be able to completely use the implemented pose estimation and grasping pipeline through DSR. This work can be summarized as follows :

-   Solve the related [open issues](https://github.com/robocomp/robocomp/issues/created_by/DarkGeekMS) on `robocomp/robocomp` repo.

-   Update `viriatoDSR` to pass the arm target poses to `viriatoPyrep` from G.

-   Add grasping methods to `viriatoPyrep`, similar to `viriatoGraspingPyrep`.

-   Test the pose estimation and grasping pipeline with tracking and social navigation, once done.

__Mohamed Shawky__
