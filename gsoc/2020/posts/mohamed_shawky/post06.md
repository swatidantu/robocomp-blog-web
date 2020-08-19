# Final Grasping Results and Integration with DSR

_DATE : August 7, 2020_

In this post, I show the final results of object grasping, using the entire pipeline. Also, I share our integration strategy with DSR graph and the new architecture. 

## Final Grasping Results (Second Demo)

In the previous post, I showed the complete system integration and the results of path planning using the estimated poses. However, the system should be tested on object grasping and manipulation, as well. Consequently, I managed to extend the embedded Lua scripts with gripper control functions. Then, `viriatoGraspingPyrep` component was updated to call these scripts using PyRep API. This way, we have a complete grasping pipeline in `viriatoGraspingPyrep` component, which goes as follows :
-   `viriatoGraspingPyrep` component opens the arm gripper through embedded Lua scripts.
-   `viriatoGraspingPyrep` component captures the RGBD signal from the shoulder camera and passes it to pose estimation components.
-   Pose estimation components estimate objects' poses and send them back to `viriatoGraspingPyrep` component.
-   `viriatoGraspingPyrep` component, then, creates a dummy with the estimated pose and calls the embedded Lua scripts to perform path planning.
-   The arm gripper is, then, closed and thus the object is grasped.
-   From there, we can create other dummies for the arm to manipulate or move the object to another position.

Following this procedure, I managed to integrate the full grasping pipeline and create a full demo for grasping using DNN-estimated poses. I used an ensemble of both RGB and RGBD estimated poses to perform pose estimation. Also, I included multiple objects in the scene to provide more challenge for both pose estimation and grasping.

<div align="center">
<a href="https://www.youtube.com/watch?v=lKk0_k8bjbY"><img src="https://img.youtube.com/vi/lKk0_k8bjbY/0.jpg" alt="IMAGE ALT TEXT"></a>
</div>

<div align="center">
Figure(1): Video of grasping second demo.
</div><br>

<div align=center><img width="60%" height="60%" src="assets/demo2_pred_pose.png"/></div>

<div align="center">
Figure(2): Visualization of the DNN-estimated pose in second demo.
</div><br>

## DSR Integration Strategy

<div align=center><img width="60%" height="60%" src="assets/components_structure_refined.png"/></div>

<div align="center">
Figure(3) : Simplified schema for grasping and pose estimation integration with DSR.
</div><br>

As shown in the figure, the components workflow goes as follows :

-   `viriatoPyrep` component streams the RGBD signal from CoppeliaSim simulator using PyRep API and publishes it to the shared graph through `viriatoDSR` component.

-   `graspDSR` component reads the RGBD signal from shared graph and passes it `objectPoseEstimation` component.

-   `objectPoseEstimation` component, then, performs pose estimation using DNN and returns the estimated poses.

-   `graspDSR` component injects the estimated poses into the shared graph and progressively plans dummy targets for the arm to reach the target object.

-   `viriatoDSR` component, then, reads the dummy target poses from the shared graph and passes it to `viriatoPyrep` component.

-   Finally, `viriatoPyrep` component uses the generated poses by `graspDSR` to progressively plan a successful grasp on the object.

## Important Dates

-   __August 2, 2020 :__

Finish the whole grasping pipeline and create a complete demo.

Commit : https://github.com/robocomp/grasping/commit/e503dd4ef2afd8b1b351bdc684df0cda54c73529

-   __August 3, 2020 :__

Merge the two pose estimation components into `objectPoseEstimation` component for integration with DSR.

Commit : https://github.com/robocomp/grasping/commit/affe68dbe0a0866e25c39608c96e1b02b453e8a0

## Upcoming Work

-   Start working on `graspDSR` component.

-   Test the grasping pipeline through the new architecture.

-   Write a full documentation on integration with DSR.

-   Final evaluation and code submission.

__Mohamed Shawky__
