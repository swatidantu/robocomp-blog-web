# Dataset Creation and other updates

August 16, 2020

In this article, I will talk about the dataset I created for training Hand Gesture Recognition models. Also, I will mention some of the other updates made in the project.

## Dataset Creation

Aim of the gesture recognition component is to recognize hand gestures from hand keypoints. Even through a lot of datasets are available that maps hand image to the American Sign Language gesture, no dataset is available which maps keypoints to the gestures. So I decided to create one by my own. For this, I used [ASL Alphabet](https://www.kaggle.com/grassknoted/asl-alphabet?) dataset available publically on Kaggle. The dataset contains 87,000 images which are 200x200 pixels. There are 29 classes, of which 26 are for the letters A-Z and 3 classes for SPACE, DELETE and NOTHING. Schematic representation of gestures is mentioned below:

![ASL Alphabets](ASL.jpg)

Then I processed this dataset using the already implemented Hand Keypoint detection component (using Mediapipe method). After passing every image through this module, I obtained required keypoints to gestures mapping, which I saved as a numpy array (which according to me will be easiest to process later).

## Update in Gesture recognition

On suggestions from mentors, to make `Hand Gesture Recognition Component` more useful and applicable, I made some changes in the implementation of this component. Now `handGesture Component` have two functions:

- Function 1 (`setClasses`): Users provides the classes from which they want to recognize classes from, and model will get modified accordingly to accomodate these changes.
- Function 2 (`getGesture`): This function will be called for every frame and will use the model trained by the above mentioned function to predict the gestures.

For now, users can only set the classes which are subsets of the ASL alphabets. We earlier thought of implementing this for any general use case, but there were some issues like:

- 2D skeleton coordinates cant be directly used as features because of high occlusion. Also we don't have any pretrained model (or related research) on Finger joints.
- Since the features are very crude we will need large training data using get gestures method which will constraint the problem to a specific datasets.

Due to time constraint, we decided to stick with ASL alphabets as superset.

## Updates in Bounding Box detection

I have updated Model used in bounding box detection to a better one. Even though the underlying method used is same (MobileNet + SSD), this model is trained on larger dataset and hence provide better accuracy.

***

**Kanav Gupta**
