# GSoC'20 RoboComp project: Human recognition (identification) using multi-modal perception system

23rd June 2020
 
## Current updates on the project
Please follow the following link: https://colab.research.google.com/drive/1lgx0LabSedQi_3dUnqEgSdRJ3ru95IPq#scrollTo=385kRQXO99h_ for current evaluation of different methods of face recognition and gait recognition. 

### 1. Face recognition 

Results are shown on the following datasets 
[LFW](!http://vis-www.cs.umass.edu/lfw/) dataset (CVPR 2007)
```
  Standard dataset used to evaluate different face recognition models
  Contains 13K photos and 5K subjects. 
```
Top performers: 

1. [ArcFace](!https://arxiv.org/pdf/1801.07698.pdf)
```
  Below I discuss 2 versions of ArcFace. 
  1. Using Resnet-100 as the backbone
  2. Using MobileFacenet as the backbone 
```
2. [CosFace](!)  
3. Face-net (Currently used by Robocomp)  

![alt-text](./images/performance_face.png)

![alt-text](./images/time_face.png)


## 2 Gait Recognition 

Reasons to use gait: 
1. Unlike face it is avaible at a distance 
2. Low resolution 


Datasets: 

1. [CASIA-B](!http://www.cbsr.ia.ac.cn/english/Gait%20Databases.asp) dataset, ICIP 2011
```
  Contains 124 subjects, and the gait data was captured from 11 views. 
```

Methods: 

1. [GaitSet](!), AAAI 2019: GaitSet is a flexible, effective and fast network for cross-view gait recognition. 

2. [GEI (Gait Energy Image)](!https://ieeexplore.ieee.org/document/1561189), (TPAMI-2005)

3. [Skeleton extracted fom openpose](!https://docs.google.com/presentation/d/1PaWISX7MiiflgPgr5fwqaIj4WFN5gD5Q0GeodmvIK_U/edit?usp=sharing) 

![alt-text](./images/performance_gait.png)

![alt-text](./images/time_gait.png)


## Next tasks 
Now that we have done the literature survey. 

The next steps are to create the pipeline for our module. This would mean 
#### Integration of face recognition system: 
  1. Face detection (mt-cnn) 
  2. Face alignment 
  3. Face feature extraction (arcface & facenet) 
  4. Face database (npy/json)
  5. KNN for face identification     


#### Integration of gait recognition system: 
  1. Human detection  
  2. Human body segmentation  
  3. Mask preprocessing  
  4. GaitSet/GEI Feature extraction 
  5. KNN for gait identification    


#### Creating a video dataset for testing 
  1. Extract videos from youtube and manually annotate them 
  2. One option is to use iLID-Dataset


#### Test different methods to fuse the detection results. 


Shubh Maheshwari
