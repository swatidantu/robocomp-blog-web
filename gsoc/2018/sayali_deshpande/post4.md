# Experimenting with Facial Landmarks

4th August, 2018

July was extremely busy. I tried out a number of different ways to achieve the best emotion recognition results. Some of them worked, some didn't. But I definitely learnt something new at each step.
Facial landmark detection was one of the notable things that I tried during this time.

## Facial Landmark Detection

The idea was to extract information about the most distinctive features from a face, that would help in clearly differentiating between the facial expressions. This would be done by detecting these facial landmarks, and using them for training a neural network.

I used the dlib library for facial landmark detection, which provided the coordinates of 68 facial landmark points, for each face. I used these landmark points in 3 different ways:

1. Calculating euclidean distances between each pair of coordinates. This gives a vector with 68*68 features, for each face in the dataset.
2. Storing the x coordinate, y coordinate, distance from center and angle with respect to the vertical, for each facial landmark point. This gives a vector of 68*4 features for each face in the dataset.
3. Using the features obtained in (2) and combining them with a CNN.

The third method worked the best among the three.

## Changing the dataset

The FER2013 dataset did not have closely cropped images of faces. Due to this, the facial landmark detection was not accurate on all images. Moreover, the resolution of the images was quite low i.e. 48x48.

So, I used 3 other facial expression datasets: [CK+](http://www.pitt.edu/~emotion/ck-spread.htm), [JAFFE](http://www.kasrl.org/jaffe.html) and [KDEF](http://www.emotionlab.se/kdef/), which had higher resolution images. The images were also quite consistent. I combined these 3 datasets to form a new dataset.

## The Results

The results of the CNN + facial landmarks model trained on this new dataset were quite impressive. The recognition was more accurate and stable.

However, some drawbacks were still present. The model could not correctly detect the emotion when the face was tilted, or from different camera angles. The recognition also did not work well in uneven illumination conditions. This was mainly due to the fact that the size of the dataset was quite small. Due to this, it could not cover different input conditions, resulting in a not-so-robust emotion recognition model.

There was a need of a new dataset which was large and had high resolution images.


* * *
Sayali Deshpande
