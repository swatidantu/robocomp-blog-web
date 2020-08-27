# Facial Emotion Recognition
 
August 20, 2020

In this blog, I will discuss the CNN based models that I tried on the different datasets for Facial Emotion Recognition and the milestones achieved. In order to evaluate the transfer learning ability of these models I trained the models on Expression in the Wild (EXPW) dataset and evaluated on the FER 2013 dataset. We omitted the classes 'disgust' and 'fear' because it is very difficult to express it only through facial expressions which is the reason for very few samples for these classes in the training dataset. So finally, we ended up with 45k training samples distributed over 5 classes.

### Facial Landmarks + HOG using CNN

The CNN model uses a concatenated feature vector comprising of Histogram of Gradient Orientation using a sliding window and the Facial Landmarks of the detected face. These also turned out to be the best performing features during our benchmarking of the traditional methods ([Refer to this post](HandCraftedFeatures.md)). On validation set we found an accuracy of 55.0% on EXPW dataset and 60.8% on FER 2013 dataset. This was a considerable progress considering that the model was not trained on FER dataset.

### VGG19 Feature using CNN

Our next approach was to obtain more robust and discriminative features for Facial Emotion Recognition. Hence we used a pretrained VGG19 on the facial dataset as the backbone for the features followed by a CNN. This resulted in a marginal boost of 3.8% on EXPW dataset but an increase of 11.5% on the validation set of FER 2013 dataset. This stacks our model close to some of the best performing models specifically trained on the FER 2013 dataset.

## Component Structure

Since the implementation of this component is complete, I can share the component definitions for reference.

**FacialEmotionRecognition.idsl**

```
module RoboCompFacialEmotionRecognition
{
	sequence<byte> ImgType;
	struct TImage
    {
		int width;
		int height;
		int depth;
		ImgType image;
    };

    sequence<float> ProbabilityVector;

	struct SEmotion
	{
		int x;
		int y;
		int w;
		int h;
		ProbabilityVector EmotionVector;	
		TImage FaceImage;
	};

	sequence<SEmotion> EmotionList;

	interface FacialEmotionRecognition
	{
		idempotent void getEmotionList(out EmotionList emotionL);
	};
};
```

**FacialEmotionRecognition.cdsl**

```
import "CameraSimple.idsl";
import "FacialEmotionRecognition.idsl";

Component FacialEmotionRecognition
{
	Communications
	{
		requires CameraSimple;
		implements FacialEmotionRecognition;
	};
	language Python;
};

```

So here we can see that this component takes the camera feed from `CameraSimple` component and implements a method `getEmotionList` which returns a list of the bounding box of the face and the probability vector of emotions of all the people present in the image.

## Testing the component

In order to test the component, follow the steps given in the post on [Face Detection](FaceDetection.md) This will show the captured frames with a bounding box and facial emotion on top of the bounding box. A demo video showing the results of the component can be found on this [link](https://drive.google.com/drive/u/1/folders/10r6tUu08dcc6GaLkbwss-TM0UtODcuBd).

**Palash Agarwal**