## ARCHITECTURE OF MobDepth:
* Input - Camera Frame (480,640,3) , Output - Depth Map (240,320,1)
* **Design Choices:** <br />
  1. Real-Time Estimation - As the model needs to predict in real time, thus a light-weight architecture is required. <br />
     As *MobileNet* uses least Number of Parameters without compromising on the Generalization, Thus it is used as Encoder.<br />
     
     ![Pre-Trained-Models_Parameters](https://user-images.githubusercontent.com/46538042/125079484-4e3fce80-e0e1-11eb-80b2-e2898996054f.png) <br />
  2. Generalization and High-Quality Depth Map - *MobileNet* is Pre-trained on ImageNet Dataset and including *Skip-Connections* make it more generalizable, removing the problem of Vanashing Gradient.  
## SOME MORE RESULTS (on MobDepth(with skip-connections)):

## AUGMENTATION OF SIMULATOR DATA (coppeliaSim):

## FINE-TUNING USING COLLECTED SIMULATOR DATA:

     

