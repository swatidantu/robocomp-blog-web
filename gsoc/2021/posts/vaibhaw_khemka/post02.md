# HIGH QUALITY MONOCULAR DEPTH ESTIMATION FOR REAL-TIME
## WORKFLOW
* Challenges: 
1. Trade off between Accuracy and Speed of the model - If model accuracy is high,Speed decreases for the prediction and vice-versa. <br />
2. Training on [NYU dataset](https://cs.nyu.edu/~silberman/datasets/nyu_depth_v2.html) which involves complex indoor scenes. So, Model should be Generalizable and robust. <br />
* Evaluating on Available Pretrained Models on the basis of Depth Map Quality and Inference Time for 1 frame(on CPU)
* If Results are not good, Creating my own light-weight architecture/model for predicting High Quality Depth Map in Real-Time.
* Preparing the NYU Dataset
* Training the Model 
* Evaluating the Results on the basis of quality Depth Map and Inference Time.

## RESULTS OF AVAILABLE MODELS 
![Results-Available_Models](https://user-images.githubusercontent.com/46538042/124872284-b065da00-dfe2-11eb-9db5-a83012d5045d.png)<br />

**A) Fast Depth (REAL TIME, MID QUALITY DEPTH)**

![FastDepth](https://user-images.githubusercontent.com/46538042/124875099-20c22a80-dfe6-11eb-8c0a-dbb9835afdce.png)
 
**B) SharpNet (NOT REAL TIME, LOW QUALITY DEPTH)**

![SharpNet](https://user-images.githubusercontent.com/46538042/124875170-36375480-dfe6-11eb-8306-8a1183620554.png)

**C) Dense Depth (NOT REAL TIME, HIGH QUALITY DEPTH)**

![DenseDepth](https://user-images.githubusercontent.com/46538042/124875248-4b13e800-dfe6-11eb-86ed-6cc37cdc2241.png)

Most of the available models are trained on [KITTI dataset](http://www.cvlibs.net/datasets/kitti/) which gave bad results on indoor scenes due to its complexity in scenes.<br />
And Models trained on NYU dataset either give High Quality Depth Map or Real-Time prediction.<br />
Thus, A new model is created which will give both High Quality Depth Map and Real-Time prediction named as *MobDepth*

## RESULTS OF MY MODELS (named as MobDepth)
![Results-MobDepth](https://user-images.githubusercontent.com/46538042/124872599-18b4bb80-dfe3-11eb-90e8-fcca30171944.png)

**A) MobDepth(Without Skip Connections) (REAL TIME, HIGH QUALITY DEPTH)**

![MobDepthWithoutSkip](https://user-images.githubusercontent.com/46538042/124878395-aeebe000-dfe9-11eb-9742-8c54dffe02da.png)


**B) MobDepth(With Skip Connections) (REAL TIME, HIGH QUALITY DEPTH)**

![MobDepthWithSkip](https://user-images.githubusercontent.com/46538042/124878421-b90dde80-dfe9-11eb-9e7e-df02e6b66e8a.png)




