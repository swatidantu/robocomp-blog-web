## Intro:

After the first phase, I had moved to going through the LapDepth paper, which is one of the state-of-the-art models for monocular depth estimation as required in our use case. 


### Depth Network - LapDepth:
The depth network, LapDepth incorporates a Laplacian Pyramid sceme into the decoder part of the encoder-decoder structure. This helps the network to better estimate the depth. It is also preferred as the lapdepth model also returns the metric depth. So, we can directly use the metric depth in our further computations, instead of worrying too much about the scale. We have experimented with the following two pretrained models:
1. Trained with KITTI using data_loss+gradient_loss
2. Trained with NYU using data_loss.

Of these we gotten the best results for the model Trained with KITTI using data_loss+gradient_loss.

### Result of the LapDepth Network for our Data:

Here are the better depth estimation results for a scene:

![](assets/image_gif.gif)
<br>
![](assets/depth_gif.gif)

### Stats
-  Inference Time: 0.5-0.6 secs per image roughly. A dataset of 125 images takes about a minute.

## What Next?
- Now, that the core part of the project is done and working well, We move on to the image stictching module where we get images from 2 cameras with orientations such that they have a partial overlap in the region being captured. In such a scenario, the images are stiched together and the 3d positions are estimated.

---

#### References

> [**YOLOv3: An Incremental Improvement**](https://arxiv.org/abs/1804.02767)

> [**Monocular Depth Estimation Using Laplacian Pyramid-Based Depth Residuals**](https://ieeexplore.ieee.org/document/9316778)

> [**Lapdepth Official Repository**](https://github.com/tjqansthd/LapDepth-release)
---
