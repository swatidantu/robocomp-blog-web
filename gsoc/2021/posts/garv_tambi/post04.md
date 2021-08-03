<p align="center">
  <img src="./assets/Robocomp.png" width="550" title="hover text">
</p>


# **Pedestrian Detection**


## Pedestrian detection using haarcascade

https://user-images.githubusercontent.com/42083679/125673350-5e65537b-077c-4f68-adcf-58c7891b2c6b.mp4

Haar Cascade Classifiers : We will implement our use case using the Haar Cascade classifier. Haar Cascade classifier is an effective object detection approach which was proposed by Paul Viola and Michael Jones in their paper, “Rapid Object Detection using a Boosted Cascade of Simple Features” in 2001.

So, let’s try to understand what these Haar Cascade Classifiers are.This is basically a machine learning based approach where a cascade function is trained from a lot of images both positive and negative. Based on the training it is then used to detect the objects in the other images.

So how this works is they are huge individual .xml files with a lot of feature sets and each xml corresponds to a very specific type of use case



Computer Vision Plays a vital role in traffic management and surveillance systems and has been an active research area in the past years. In systems like these, the detection of vehicles and also classification of the vehicle plays a major role. The datasets are traffic videos of urban environment taken from various cities around the world which were used to train the classifier hence generating a robust classifier. The proposed approach is computationally less expensive with faster processing speed. The experiments on-road prove it to be a robust and real time algorithm which is highly competitive with the existing architecture.

This System has the following Haar Cascades:
1) Haar Cascade for Car detection
2) Haar Cascade for Bus Detection
3) Haar Cascade for Two-Wheeler Detection
4) Haar Cascade for Pedestrian Detection

`import cv2
import numpy as np

# Create our body classifier
body_classifier = cv2.CascadeClassifier('Haarcascades\haarcascade_fullbody.xml')

# Initiate video capture for video file
cap = cv2.VideoCapture('image_examples/walking.avi')

# Loop once video is successfully loaded
while cap.isOpened():
    
    # Read first frame
    ret, frame = cap.read()
    #frame = cv2.resize(frame, None,fx=0.5, fy=0.5, interpolation = cv2.INTER_LINEAR)

    gray = cv2.cvtColor(frame, cv2.COLOR_BGR2GRAY)
    # Pass frame to our body classifier
    bodies = body_classifier.detectMultiScale(gray, 1.2, 3)
    
    # Extract bounding boxes for any bodies identified
    for (x,y,w,h) in bodies:
        cv2.rectangle(frame, (x, y), (x+w, y+h), (0, 255, 255), 2)
        cv2.imshow('Pedestrians', frame)

    if cv2.waitKey(1) == 13: #13 is the Enter Key
        break

cap.release()
cv2.destroyAllWindows()`




## Pedestrian detection using Yolo

https://user-images.githubusercontent.com/42083679/128036811-ad93ce8e-d14e-412a-bf2c-7fb1751d860f.mp4

Pedestrian detection in image or video data is a very important and challenging task in security surveillance. The difficulty of this task is to locate and detect pedestrians of different scales in complex scenes accurately.
To solve these problems, a deep neural network (RT-YOLOv3) is proposed to realize real-time pedestrian detection at different scales in security monitoring. RT-YOLOv3 improves the traditional YOLOv3 algorithm. Firstly, the deep residual network is added to extract vehicle features. 
Then six convolutional neural networks with different scales are designed and fused with the corresponding scale feature maps in the residual network to form the final feature pyramid to perform pedestrian detection tasks. This method can better characterize pedestrians. 
In order to further improve the accuracy and generalization ability of the model, a hybrid pedestrian data set training method is used to extract pedestrian data from VOC data set and train with INRIA pedestrian data set

https://user-images.githubusercontent.com/42083679/128036811-ad93ce8e-d14e-412a-bf2c-7fb1751d860f.mp4
