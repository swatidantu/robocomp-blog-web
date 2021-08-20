# Final Project Submission
This is the final post of `Monocular Depth Estimation using RBG signals` project.I will present all the work done and results of the project with link to all my contributions and issues that needs to resolved along with future extensions.<br/>

## Brief Description
Depth Estimation is one of the attractive research areas in computer vision. The motivation of this project is to estimate depth without the use of LIDAR sensors or any other related costly setups. And it also makes the robot more robust and efficient to carry out any task using the crucial depth information.<br/>

In this project, Myself, **Vaibhaw Khemka**, worked with RoboComp and my mentor, **Mohamed Shawky**,to develop real-time depth estimation pipeline using latest research and advances in Deep Learning. I have build a Deep Neural Network(DNN) architecture (named `MobDepth`) which is integrated to `depthEstimation` component built on RoboComp Framework. It gives high quality depth estimation in both real and simulated world and works well with complex indoor scenes.Finally, I worked in integration of depth estimation component into CORTEX architecture(based on Deep State Representation) by building `depthDSR` agent.


## Project Details
Summary of all the tasks done in each period :<br/>
## Community Bonding Period
<!-- Remove this hint: these checkboxes can be checked like this: [x]. -->
- [x] Communicated with my mentor, **Mohamed Shawky**, about the project plan and workflow.

- [x] Set up my development environment and started familiarizing more with RoboComp Frameworks.

- [x] Identified different challenges that exist in the project like:
      * Trade off between Accuracy and Speed of the model.
      * Model should be Generalizable and robust.
   
- [x] Started working on implementing different literatures for building depth estimation neural network.  
### First Coding Period
<!-- Remove this hint: these checkboxes can be checked like this: [x]. -->
- [x] Results obtained on existing literatures for depth estimation were not good as it didn't satisfy both real-time and high quality estimation of depth.

- [x] Started building my own architecture(`MobDepth`) using Transfer Learning on MobileNet architecture to meet the requirement of real-time and high quality depths.

- [x] Trained on `NYU dataset`, which consist of complex indoor scenes to make it more generalizable.

- [x] Tested on real world scenarios and added skip connections in the model which gave a very good result.

- [x] Prepared the dataset using python [data collector](https://github.com/robocomp/grasping/tree/master/data-collector) from coppeliaSim for model to also work in a simulated world and augmented it with `NYU dataset`.

- [x] Retrained/Fine-Tuned the network on augmented dataset. 

### Second Coding Period
<!-- Remove this hint: these checkboxes can be checked like this: [x]. -->
- [x] Build `depthEstimation` component and interfaces in consistent with RoboComp Framework.

- [x] Integrated and tested the trained depth estimation model with the component. 

- [x] Started familiarizing with CORTEX architecture(based on Deep State Representation) and discussed with my mentor, **Mohamed Shawky** to gain more exposure on this.

- [x] Studied DSR architecture through installation and tested different agents like - [graspDSR](https://github.com/robocomp/dsr-graph/tree/development/components/graspDSR),  [yolov4-detector](https://github.com/robocomp/dsr-graph/tree/development/components/yolov4-detector) etc.

- [x] Implemented `depthDSR` C++ agent which acts as an interface between `depthEstimation` component and shared graph(G). It takes RGB image from Graph and estimate depth using `depthEstimation` component.

- [x] Wrote a detailed documentation about DSR integration and its problems.

- [x] Faced multiple issues and problems while integration With DSR.

- [x] Resolved most of the issues with help of my mentor, **Mohamed Shawky**. But there are still some issues while connecting with `depthEstimation` component.

- [x] Updated and improved the documentation of all components and agents.   

## Results and Demonstrations
Fig-1: Depth Map for Real world Scenes <br />

![MobDepthWithSkip](https://user-images.githubusercontent.com/46538042/124878421-b90dde80-dfe9-11eb-9e7e-df02e6b66e8a.png)

Fig-2: Depth Map before and after Fine-Tuning  <br />
![Before_Fine-Tuning1](https://user-images.githubusercontent.com/46538042/125087934-92839c80-e0ea-11eb-9aa6-8469804482d7.png)
![After_Fine-Tuning1](https://user-images.githubusercontent.com/46538042/125087929-90b9d900-e0ea-11eb-8f46-6e4a276785c2.png)

![Before Fine-Tuning2](https://user-images.githubusercontent.com/46538042/125088053-afb86b00-e0ea-11eb-9613-407b64aa1a5f.png)
![After Fine-Tuning2](https://user-images.githubusercontent.com/46538042/125088045-adeea780-e0ea-11eb-9b9c-3e58aa109fee.png)

Fig-3: Demo of depthEstimation component in simulated world <br />

https://user-images.githubusercontent.com/46538042/129046230-2305ee52-9609-4ef5-b81c-8d21989ff2da.mp4

## Contributions Summary
|       Repo    | Commits       |     PRs         | Issues        | 
| ------------- | ------------- |  -------------- | ------------- | 
| [robocomp/DNN-Services](https://github.com/robocomp/DNN-Services)  | [link](https://github.com/robocomp/DNN-Services/commits?author=vaibhawkhemka)  |  [link](https://github.com/robocomp/DNN-Services/pulls?q=is%3Apr+author%3Avaibhawkhemka)   | - | 
| [robocomp/robocomp](https://github.com/robocomp/robocomp)   | [link](https://github.com/robocomp/robocomp/commits?author=vaibhawkhemka) |  [link](https://github.com/robocomp/robocomp/pulls?q=is%3Apr+author%3Avaibhawkhemka)   | [link](https://github.com/robocomp/robocomp/issues?q=is%3Aissue+author%3Avaibhawkhemka) | 
| [robocomp/dsr-graph](https://github.com/robocomp/dsr-graph)   | [link](https://github.com/robocomp/dsr-graph/commits?author=vaibhawkhemka)  |  [link](https://github.com/robocomp/dsr-graph/pulls?q=is%3Apr+author%3Avaibhawkhemka)   | [link](https://github.com/robocomp/dsr-graph/issues?q=is%3Aissue+author%3Avaibhawkhemka) | 
| [robocomp/web](https://github.com/robocomp/web)   | [link](https://github.com/robocomp/web/commits?author=vaibhawkhemka)  |  [link](https://github.com/robocomp/web/pulls?q=is%3Apr+author%3Avaibhawkhemka)  | - | 

## Future Works and Improvements 
The work with the project has been completed successfully with demos and documentation except the issue of `depthDSR` while connecting with `depthEstimation` component.So,Summary of future improvements are as follows:
* Resolve the issue of `depthDSR` while connecting with `depthEstimation` component.
 
* Extend the depth estimation model to work better even for outdoor scenes as well.
 
* Build `Collision-detector` component with help of depth estimated from the agent.
 
* Update and maintain the components in consistent with RoboComp regularly. 

* Explore more applications of depth estimation which can be integrated with RoboComp.

**Vaibhaw Khemka**

