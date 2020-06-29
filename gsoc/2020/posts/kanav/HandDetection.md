# Hand Detection in the Image Feed

June 29, 2020

Detecting hands in the image feed is essential aspect for recognizing hand gestures. In this article, I will discuss the different methods used by me to detect hand in the input image. I will also elaborate on the efficiency, accuracy and drawbacks of these models.

As one of the constraints of this project is to achieve low latency on the response, I considered two Neural Network based methods *i.e SSD + MobileNet and Mediapipe* because of their at par response times and much better accuracies when compared to other methods.

## SSD + MobileNet

SSD is a single shot detector and predicts bounding boxes and classes directly from the feature maps without making use of Region Proposal Network. This results in better latency as making use of Region Proposal Network is time consuming. Moreover, to improve on accuracy, SSD introduces:

- Small convolutional filters to predict object classes and offsets to default boundary boxes
- Separate filters for default boxes to handle the difference in aspect ratios
- Multi-scale feature maps for object detection

These properties of SSD were really useful in case of Hand Detection as size and position of hand in image feed can vary a lot when compared to other parts.

Response time of this method is 14-15 FPS (frames per second) when run on CPU (Intel i5 processor) and 30-35 FPS when run on GPU. Accuracy is also preety good but sometimes gives distorted results when there is very bright light in the background.

## Mediapipe

Mediapipe is Google’s open source framework for building multimodal, cross-platform applied ML pipelines. Mediapipe Hands is one the best techniques for hand detection and tracking. Mediapipe specifically detects palm in the image as estimating bounding boxes of rigid objects like palms and fists is significantly simpler than detecting hands with articulated fingers. Moreover, palms can be modelled using square bounding boxes, so other aspect ratios can be ignored, thus improving of the response time of the model. Along with this, an encoder-decoder feature extractor is used for bigger scene context awareness even for small objects. Mediapipe also give four palm keypoints which enabled capturing of rotaional motion of hand and the same was applied to the bounding box.

Response time of this method is around 12-13 FPS when run on CPU (Intel i5 processor). Accuracy is much better that the SSD + MobileNet model and gives excellent results even in unusual background or lighting.

Refer the below links for learning more about Mediapipe and it's use cases:

- [Mediapipe](https://google.github.io/mediapipe/)
- [Mediapipe Hands](https://google.github.io/mediapipe/solutions/hands)
- [Research article on Mediapipe's Hand Tracking](https://arxiv.org/abs/2006.10214)

## Try it out!

For experiencing this yourself, visit [handGestureClient Component](https://github.com/Kanav-7/robocomp-robolab/tree/master/components/detection/test/handGestureClient) and follow the the given instructions.

## What's Next?

Now as I have obtained the bounding box of the hand in the image, next step is to find out keypoints of this hand. This part of project will be implemented in *Hand Keypoint Component*.

***

**Kanav Gupta**
