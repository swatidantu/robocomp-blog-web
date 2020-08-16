# GSoC'20 RoboComp project: Human recognition (identification) using multi-modal perception system

18th July 2020

Multiple human tracking is the process of locating multiple persons over a sequence of frames (video). The MHT problem can be viewed as a data association problem where the goal is to associate detections across frames in a video sequence.

MHT can be divided into 3 steps: 

- **Detection**: In each frame of the video we need to find the bounding box for each person present

- **Multiple Object Tracking**: Multiple Object Tracking is the problem of automatically identifying multiple objects in a video and representing them as a set of trajectories with high accuracy.

- **Person re-identification(ReID)**: Reid is associating images of the same person taken from different cameras or from the same camera at different points in time. Usually, re-identification is constrained to a small time period and a small area covered by cameras 

 
### Technologies
a) **[CenterTrack](https://github.com/xingyizhou/CenterTrack)** 
    presents a simultaneous detection and tracking algorithm that is simple, faste, and accurate. Their tracker, applies a detection model to a pair of images and detections from the prior frame to localizes objects and predicts their associations.

b) **[Torch-reid](https://github.com/KaiyangZhou/deep-person-reid)**
    Torchreid is a library for deep-learning person re-identification, written in PyTorch.    

[Back To The Top](#table-of-contents)

---

## References
- CenterTrack 
    > [**Tracking Objects as Points**](http://arxiv.org/abs/2004.01177),            
    > Xingyi Zhou, Vladlen Koltun, Philipp Kr&auml;henb&uuml;hl,        
    > *arXiv technical report ([arXiv 2004.01177](http://arxiv.org/abs/2004.01177))*  

- Torchreid
    > [**Tracking Objects as Points**](http://arxiv.org/abs/2004.01177),            
    > Xingyi Zhou, Vladlen Koltun, Philipp Kr&auml;henb&uuml;hl,        
    > *arXiv technical report ([arXiv 2004.01177](http://arxiv.org/abs/2004.01177))*  
--- 
Shubh Maheshwari