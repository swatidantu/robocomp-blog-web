# Face Detection and Alignment
 
July 17, 2020

In order to perform Facial Emotion Recognition, one of the prerequisites is to identify the faces in the image. This is a very crucial step in the pipeline because of the following 3 reasons:

- If the component has a high false positive rate, then every other bounding box will be characterized incorrectly as a face.
- If the component has a high false negative rate, then only partial faces will be identified in the video feed.
- The face detection model should perform real time in order to keep up with the rapidly varying facial expressions. 

Keeping these factors in consideration, I benchmarked the following 3 methods for face detection:

### Multi-task Cascaded Convolutional Networks (MT-CNN)

This framework comprised of a Proposal Network, Refine Network and Output Network. The proposal network predicted the candidate windows for the faces followed by a refine network which removeed the false positive cases. Finally the output network used non-maximum suppression algorithm and bounding box regression to predict the bounding box and facial landmarks.

This method is already included in the Robocomp codebase as part of the Face Identification Component. Although the model performs accurately, it is slow even on GPU (around 5-6 FPS) which is not suitable for our real time application.

### Dlib Implementation

Next, I looked at the dlib python library which supports state of the art Face Detection models. This model regresses over 68 facial landmarks and estimates the bounding box based on that. Although the model performs well in terms of speed (around 15 FPS), it lacks in accuracy and is not robust to varying poses and partial occlussions. 

### RetinaFace

In order to strike a balance between speed and accuracy, I turned to another state of the art method for face detection i.e. [RetinaFace](https://arxiv.org/pdf/1905.00641.pdf). This method proposes a novel pixel wise face localisation method with multi-task learning strategy to simultaneously predict face score, face box, facial landmarks etc. I use a lightweight version of this model 'RetinaNetMobileNet' which helps me achieve around 30 FPS while also maintaining a very good accuracy and tracking. 

## Face Alignment

Facial landmarks extracted from the RetinaFace are further used to align the images in the video feed. This is a very crucial data pre processing technique as it can significantly improve the performance of model in case of any downstream task related to faces. 

## Testing the component

In order to test the component, first build the component using CMake.

```
cd robocomp/components/robocomp-aston/components/detection/FacialEmotionRecognition
cmake .
make
```

Now in order to run the component follow the given steps:

```
cd robocomp/components/robocomp-aston/components/hardware/camera/camerasimple
python3 src/camerasimple.py etc/config
```

This will start the camera simple component. Now run the FacialEmotionRecognition code in another terminal.

```
cd robocomp/components/robocomp-aston/components/detection/FacialEmotionRecognition
python3 src/FacialEmotionRecognition.py etc/config
```

This will show the captured frames with a bounding box and facial emotion (currently 'UNKNOWN') on top of the bounding box. I am currently training deep learning models for the emotion recognition on the dataset 'Facial Expression in the Wild'. Further I propose to benchmark the trained models on the FER dataset to verify the transfer learning capacity of the model.

**Palash Agarwal**