# GSoC'20 RoboComp project: Human recognition (identification) using multi-modal perception system

11th June 2020
 
### Benchmarking methods for face analysis 

Facial analysis is used to automatically label an individualin by retrieving it's face features. It can be divided into 2 steps: 

### Detection 

In each frame of the video we need to find the bounding box for each person's face. To choose the technique to integrate, we compare their performance and computation time. 

#### Top performers on [UTK](https://susanqq.github.io/UTKFace/) dataset
  1. [Mt-CNN](https://github.com/ipazc/mtcnn) 
  2. [Haar Cascade](https://www.cs.cmu.edu/~efros/courses/LBMV07/Papers/viola-cvpr-01.pdf)

![Face Detection performance](./assets/facedetection_performance.png)

![Face Detection time](./assets/facedetection_time.png)

*Based on these results, we have choosen **Mt-cnn** as the face-detection model.* 



### Recognition

Face recognition is a method of identifying or verifying the identity of an individual using their face.

#### Top performers on [LFW](http://vis-www.cs.umass.edu/lfw/) dataset

1. [ArcFace](https://arxiv.org/pdf/1801.07698.pdf)
```
  2 versions of ArcFace are benchmarked. 
  - Using Resnet-100 as the backbone
  - Using MobileFacenet as the backbone 
```
2. [CosFace](https://openaccess.thecvf.com/content_cvpr_2018/CameraReady/1797.pdf)  
3. [Face-net](https://arxiv.org/abs/1503.03832)   

![Face Recognition performance](./assets/performance_face.png)
    
![Face Recognition time](./assets/time_face.png)


    
*Based on these results, we have choosen **Arcface** as the face-recognition model.* 
    
 
[Back To The Top](#table-of-contents)

---

## Current updates on the project
Please follow the following [link](https://colab.research.google.com/drive/1lgx0LabSedQi_3dUnqEgSdRJ3ru95IPq#scrollTo=385kRQXO99h_) for current evaluation of different methods of face recognition and gait recognition. 

---

#### References

> [**Deep Face Recognition: A Survey**](https://arxiv.org/pdf/1804.06655.pdf),            
> Mei Wang, Weihong Deng,       
> *arXiv technical report ([arXiv 1804.06655](https://arxiv.org/pdf/1804.06655.pdf))*

> [**A survey on deep learning based face recognition**](https://doi.org/10.1016/j.cviu.2019.102805),            
> Guodong Guo, Na Zhang,       
> Computer Vision and Image Understanding ([DOI 10.1016](https://doi.org/10.1016/j.cviu.2019.102805))*

---
Shubh Maheshwari
