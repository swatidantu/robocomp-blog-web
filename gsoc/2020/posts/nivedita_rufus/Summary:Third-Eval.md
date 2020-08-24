The last task left for me to do according to my proposal is the integration to the RoboComp architecture.    
The ability to configure an application's properties externally provides a great deal of flexibility. One can use any combination of command-line options and configuration files to achieve the desired settings, all without having to modify source code of the application. Ice is a handy tool to use in this respect because at it run time automatically loads a configuration file during the creation of a property set, which is an instance of the `Ice::Properties` interface. So, on the same note, I have created a RoboComp Component [PeopleCounter_SSDCNET](https://github.com/niveditarufus/human-detection/tree/gsoc/components/peopleCounter_SSDCNet) which uses the SS-DCNet architecture for counting people in a video feed.  
The config file requires 6 parameters to be initialised:  
1. **save_results:** set this to true if you want the output to be saved on the system
2. **filer:** It should be set to one of three options(None, kf(Kalman filter) or mavg(Moving average). This will vary from video to video.
3. **model:** This should set to one of the three options(model1, model2, model3). This will vary from video to video.
4. **skip_frames:** No. of frames that need to be skipped.
5. **stitch:** Set this to true if there are multiple video feeds and you want the count values to be obtained post stitching the videos together. setting this to false will assume majority voting.
6. **video:** Path/URL of videos. You can set this None if you want to start a webcam stream.  
The structure of the code follows the Finite State machine style which can be easily understood with the following diagram:  
![]/images/fsm.png  
This style of programming ensures easy upgrades in the future without much rewriting of code. The new blocks can just be plugged into the existing modules. The final result of the People counter working from the RoboComp architecture is given below(Image Source: [SALSA dataset](https://tev.fbk.eu/salsa)).  
![]/images/counting.gif  
I have compiled all my contributions in this branch of the [Human-Detection](https://github.com/niveditarufus/human-detection/tree/gsoc) repository and made a [pull request](https://github.com/robocomp/human-detection/pull/6) for the same.  