# Graph Convolutional Networks for Emotion Recognition
 
August 24, 2020

Facial expressions for emotions are not consistent for each image in a video. There are intermediate frames during a transition between emotions. Such facial expressions are very difficult to classify as they don't belong to any particular class. This is also one major reason why models trained on image datasets for facial emotion recognition perform poorly on videos. In order to circumvent this obstacle, I used a Spatio-Temporal Graph Convolutional Neural Networks for our task.

## Dataset preparation

For these networks I used a video dataset Aff-Wild2. I used the 5 basic emotion categories: Happy, Sad, Neutral, Anger, Surprise. The cleaned dataset consisted of 1200 training samples and 586 validation samples. Each sample consisted of 45 frames representing the same emotion class with varying intensity and transition frames. In order to create this dataset, for each video sample, I computed the 68 dimensional facial landmarks for the 45 frames. This represents our feature vector of the shape 45 X 68 X 2 as our input to the GCN model. Such a feature vector allows us to capture both the spatial and temporal changes over the video.

### ST-GCN

Next we define the graph where each 2D facial landmark represent a graph node and natural connectivity in the facial structure represents the graph edges. In order to capture the temporal dynamics of the facial expressions we also define edges between same joints across the consecutive frames. The input to the ST-GCN is therefore the joint
coordinate vectors on the graph nodes. This can be considered as an analog to image based CNNs where the input is
formed by pixel intensity vectors residing on the 2D image grid. Then we pass this through the multiple layers of spatial-temporal graph convolution as defined in [ST-GCN paper](https://github.com/yysijie/st-gcn) followed by a softmax layer for classification. With this model we got an accuracy of 58.27% on the validation set.

### RA-GCN

Further inspired by [RA-GCN](https://arxiv.org/pdf/1905.06774.pdf) we also tried a multi-stream ST-GCN with same dataset and graph structure. However this model overfitted to the training set due to a smaller dataset large number of model parameters. We achieved a low accuracy of 44.93% on the Aff-Wild2 dataset.

## Limitations and Future Work

The domain of Facial Emotion Recognition in videos is very challenging due to the lack of large scale datasets and inconsistent facial expressions for different emotion categories. However, spatio-temporal networks similar to ones discussed in this post open new paths in this domain and can be explored further.

**Palash Agarwal**