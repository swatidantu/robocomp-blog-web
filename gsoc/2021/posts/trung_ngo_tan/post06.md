# GSoC'21 RoboComp project: Sign language recognition

14th Aug 2021

## Conclusion:
Throughout this projest, three components are published: BodyHandJointsDetector, ImageBaseGestureRecognition, PoseBasedGestureRecognition. I will also code the testing client for each approach.
+ BodyHandJointsDetector: [component](https://github.com/rongtuech/robocomp-robolab/tree/sign_language_commit/components/detection/BodyHandJointsDetector) , [client](https://github.com/rongtuech/robocomp-robolab/tree/sign_language_commit/components/detection/test/bodyHandJointsDetectorClient). In this component,
I use Oenpose light model and media-pipe lib to get skeleton from image body.

+ ImageBasedRecognition: [component](https://github.com/rongtuech/robocomp-robolab/tree/sign_language_commit/components/detection/imageBasedGestureRecognition) , [client](https://github.com/rongtuech/robocomp-robolab/tree/sign_language_commit/components/detection/test/imageBasedGestureRecognitionClient). In this project, we implement [WLASL recognizer](https://github.com/dxli94/WLASL).
There are pretrained model for this dataset. Therefore, we reuse these models without any training. In the image-based approach, they use I3D model for recognition.

+ PoseBasedRecognition: [component](https://github.com/rongtuech/robocomp-robolab/tree/sign_language_commit/components/detection/PoseBasedGestureRecognition) , [client](https://github.com/rongtuech/robocomp-robolab/tree/sign_language_commit/components/detection/test/poseBasedGestureRecognitionClient).
For pose-based reocngition, we reuse Pose-TGCN (graph neural network). This model have body/hand joints input and output the gesture classes.
  

### Inference acceleration:

The inference directly from Python for Pytorch models usually performs poorly. Therefore,
I apply some techniques:

+ Using C++ code for post-processing.
+ Change the Pytorch format to ONNX format.
+ Combine trained ONNX model with NVIDIA® TensorRT.

### Pull Requests:

I have made my commits in some pull requests:
+ For all components: https://github.com/robocomp/robocomp-robolab/pull/77 
+ For IDSL files: https://github.com/robocomp/robocomp/pull/343
+ For blog: https://github.com/robocomp/web/pull/259, https://github.com/robocomp/web/pull/252, https://github.com/robocomp/web/pull/250, https://github.com/robocomp/web/pull/249, https://github.com/robocomp/web/pull/224.


## Future works:

I have just finished 3 listed components. However the accuracy of PoseBasedRecognizer is still low. Furthermore, the applying of Unsupervised model is still not used. Therefore, in the future, we would like to:
+ Improve result of Pose-based approach.
+ Apply unsupervised techniques for gesture recognition.


## Thanking Note:

The journey of GSoC 2021 is really interested. I learn a lot about: open source contribution, robocomp library, and also about sign language problem for the first time. Furthermore, I faced some challenges and it's quite fun to deal with. 

 I would like to thank Aditya Aggarwal and Kanva Gupta for patiently help me in this project.