# Robocomp components creation

Aug 20, 2019

The final step of the project is the creation of the component for Robocomp for human activity recognition. The resulting setup actually involves 4 components, 1 of them (camera component) is an existing Robocomp component, three others have been developed in the course of this project. 
![Components communication diagram](HAR_interaction.png)

## Skeletons extraction

Our activity recognition models have been trained on joints data, therefore extraction of poses is one of the steps in our HAR process. The datasets used for training were usually captured with MS Kinect sensor, which offered possibility for real-time skeleton tracking but which however is not officially available anymore. Given its discontinuation, one of the alternatives was to introduce an additional component to produce pose estimation on the frames received from camera. The problem with RGB-D cameras is that component has to be hardware specific and in this sense doing pose estimation on RGB input makes the use of the whole HAR pipeline easier as it can be run with any type of camera even with a simple webcam. Moreover, sticking with RGB input was dictated by the availability of ready-for-use open source pose estimators, which produce good performance. 
  

## Components

As illustrated in the above communication diagram, all 4 components have to be started. It can be done manually by running each component, but I also provide a shell script in the activityRecognitionClient, which starts the whole group. activityRecognition client get frames from the camera component and sends it to the poseEstimation component to receive skeletons. Both 3D and 2D skeletons are returned, 3D skeletons are used for activity prediction, whereas 2D data is used to visualization of the estimated poses as the feedback to the user. activityRecognitionClient is responsible for this visualization. It also calls addSkeleton() method of the activityRecognition component once per second. The function call return a boolean, which is True, once activityRecognition has sufficient number of skeletons to run a prediction. If [ready] predicate is satisfied (addSkeleton return True), the Client calls getCurrentActivity() on the activityRecognition component and outputs the predicted label.  


***
MF
