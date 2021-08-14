# GSoC'21 RoboComp project: Sign language recognition

14th Aug 2021

## Installation:
This component requires the same environment as HandPose and ImageBasedRecognition component, 
please check this [link](/web/gsoc/2021/posts/trung_ngo_tan/post03).


## Usage:
### Pose based Sign language recognition:
The pose detector component is in robocomp-robolab/components/detection/BodyHandJointsDetector/ . 
The recognized component is in robocomp-robolab/components/detection/poseBasedGestureRecognition .
and its client is in robocomp-robolab/components/detection/test/poseBasedGestureRecognitionClient/


Copy pretrained model from this [link](https://drive.google.com/file/d/1noNAokd8a39a1_DbOjLn5Hdi9LsI4snr/view?usp=sharing)
to src/_model/ in the detector component folder.

Steps:
1) Follow the introduction in the README.md to cmake the folder, and run the component. 
2) Run the detector and recognizer before the client.

This client will get image from camera and send to detector and get back the body pose + hand joints. 
Then these poses are collected and send to recognizer to get the class of gesture.

Currently, this component is still debugging.

## Demo: 

HandBodyPoseDetector component/client:

[![handbody demo](images/handbodyPoseYoutube.png)](https://youtu.be/qpOU7or_zx8 "Video Title")


ImageBasedRecognition component/client:

[![image based recognition demo](images/imagebasedRecognitionYoutube.png)](https://youtu.be/aAywMZqqlVw "Video Title")
