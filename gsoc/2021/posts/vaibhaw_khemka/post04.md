# FINAL DEPTH ESTIMATION RESULTS IN SIMULATED WORLD 
https://user-images.githubusercontent.com/46538042/129046230-2305ee52-9609-4ef5-b81c-8d21989ff2da.mp4

# FINAL DEPTH ESTIMATION RESULTS IN REAL WORLD


# INTEGRATION WITH DSR 
## DSR INTEGRATION PROCESS
The process of integrating depth estimation and DSR goes as follows :
* First, I have completed the depthEstimation component which is [] . This component uses RGBD images and output the depth of the frames. But it needs to be integrated with DSR shared graph for reading the RGBD images from G(Graph).
* Simultaneously, a component is developed as an interface between depthEstimation component and shared graph known as depthDSR[],which is a DSR agent responsible for reading the RGBD data from the shared graph, feeding it to the depthEstimation component and injecting the depth values of frames in the shared graph.
![DSR_Integration](https://user-images.githubusercontent.com/46538042/129082533-9757bbce-733b-4ae9-9ab0-0ea577c0efa3.png)
<br/> Fig(3): DSR Integration Pipeline  

## WORKFLOW
* Complete the depthEstimation component by incorporating the trained model MobDepth[] to estimate depth
* Read RGBD data from Graph by building depthDSR agent and testing it in coppeliaSim[].
* Integrate depthEstimation component with depthDSR for passing RGBD data into the model and displaying depth Map through the agent. 

## ISSUES FACED
* 

