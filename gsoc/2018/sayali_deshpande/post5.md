# ~~Problems~~ Solved

5th August, 2018

My previous post described a number of problems that persisted in the trained model. My mentor, Pilar Bachiller, helped me tackle each problem that came along. I can't thank her enough for her constant support and guidance.

**Problem 1:**

The component was unable to correctly recognize emotions when the faces were tilted sideways by some angle.

*Solution:*

Alignment of the faces using facial landmarks: For every input face, it would first be aligned vertically before feeding it to the emotion classifier. This improved the results drastically! The recognition became much more stable.


**Problem 2:**

The component was unable to correctly recognize emotions under low light or uneven illumination conditions.

*Solution:*

Adding adaptive histogram equalization helped improve the results slightly.

**Problem 3:**

The component was unable to correctly recognize emotions when the head was turned towards left or right. Changing the camera position also gave inaccurate results.

*Solution:*

The reason for the problem was the small size of the dataset on which the model was trained. It mostly consisted of frontal face images. The solution was to use a bigger and better dataset. That is when Pilar suggested [AffectNet](http://mohammadmahoor.com/affectnet/). It is a huge 122 GB dataset, containing both, manually and automatically annotated images. The dataset is available on request. It took a few days before my request was accepted and I could start working on it. I only used a part of this dataset for training the model. My training set consisted of 18750 images, validation set of 4000 images and testing set of 4000 images. Although the accuracy recorded on this dataset was 57%, this trained model gives great results in practice.

The emotion recognition component can now recognize 5 emotions: Happiness, Sadness, Surprise, Anger, Neutral; with good accuracy, robustness and reliability.


* * *
Sayali Deshpande
