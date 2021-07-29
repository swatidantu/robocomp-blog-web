# GSoC'21 RoboComp project: Sign language recognition

17th July 2021

## Current process:
I have finished to build and test pytorch code for:
+ BodyHandDetector model -> ONNX, tensorRT.
+ ImageBasedGestureRecognition -> ONNX, tensorRT.
+ PoseBasedGestureRecognition -> ONNX, tensorRT.

Besides, the robocomp component for all of them have already coded:
+ BodyHandDetector + BodyHandDetectorClient (Tested + still improving)
+ ImageBasedGestureRecognition (Testing)
+ PoseBasedGestureRecognition (Debugging)

I will soon merge the code of these component into Robocomp lib after GSoC phase 1.

Some problems I find out in Robocomp library:
+ when import default components and generate code py robocompdsl for cdsl for python.
Some library can not be imported, for example: rcportchecker lib
  => add this line sys.path.append('/opt/robocomp/python/') into /usr/local/bin/robocompdsl.py , line 16
  
+ The install process may face bugs, if not install robocomp lib in home/user_name/ folder. Because, the base code of 
  robocomp lib use static links. And if change the clone folder, the install process may fail.

  
## Current issue:
+ I have some problem with Qcore thread in my component, and it slow down my inference process in pose detection.
+ Need a strategy to do real-time inference for image based and pose based


## Works in 2nd phase:
+ debug all remain components. 
+ improve the inference speed. 
+ code the unsupervised component.

