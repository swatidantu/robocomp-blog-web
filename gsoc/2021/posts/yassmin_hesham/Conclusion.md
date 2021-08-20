# GSoC'21 RoboComp project: Simultaneous path planning and following using Model Predictive Control (SPAF)


# Conclusion
MPC has the ability to systematically consider nonlinearity, future predictions and operating constraints of the control system framework. It uses a mathematical dynamic process model of the system to predict future values and optimize control process performance. 
We discussed earlier how to implement MPC using [CasADi](https://web.casadi.org/) optimizer. Both point stabilization and Path Following were implemented. Also, an additional mode was added to switch between omni-directional robot to differential robot. 

# What's next?
- ## Dynamic Obstacle Avoidance:
Dynamic Obstacle Avoidance is when the trajectory has been predetermined and the controller must be able to autonomously
avoid static obstacles on the road and can track the desired trajectory by controlling the front steering angle of the vehicle.That's why it is an important feature to be added.  

- ## Tuning Parameters:
Tuning weights is not an easy task. That's why we should reach a systematic algorithm to follow in order to reach the best values for the optimization process.


# Acknowledgement
No words can describe how grateful I am for getting through such an amazing experience. It was a great honor to participate in GSoC with Robocomp under the supervision of my mentors. I'm thankful for their guidance and support.  This topic is challenging; however, I really enjoyed learning, reading articles, and implementing the equations in code. 

# References
- All mathematical equations used in this project are included in this [paper](https://www.overleaf.com/project/60d59adc32dbeb61c43a3775).
- Model Predictive Control: Theory, Computation, and Design (2nd Edition)
- [MPC Lectures](https://www.youtube.com/watch?v=RrnkPrcpyEA&list=PLK8squHT_Uzej3UCUHjtOtm5X7pMFSgAL)
- [Runge Kutta Method](https://www.sciencedirect.com/topics/mathematics/runge-kutta-method)
- [Model Predictive Control for a Mecanum-wheeled robot in Dynamical Enviroments](https://www.researchgate.net/publication/334319114_Model_Predictive_Control_for_a_Mecanum-wheeled_robot_in_Dynamical_Environments)
- [Design and development of an autonomous omni-directional mobile robot with Mecanum wheels](https://www.researchgate.net/publication/269294739_Design_and_development_of_an_autonomous_omni-directional_mobile_robot_with_Mecanum_wheels)
- [Differential Drive Kinematics](http://www.cs.columbia.edu/~allen/F17/NOTES/icckinematics.pdf)
- [Mobile Robot Kinematics](https://www.usna.edu/Users/cs/crabbe/SI475/current/mob-kin/mobkin.pdf)
- [Predictive Path Following of Mobile Robots without Terminal Stabilizing Constraints](https://www.researchgate.net/publication/315678321_Predictive_Path_Following_of_Mobile_Robots_without_Terminal_Stabilizing_Constraints)
- [Nonlinear Model Predictive Path-Following Control](https://www.researchgate.net/profile/Timm-Faulwasser/publication/227334005_Nonlinear_Model_Predictive_Path-Following_Control/links/0046352d563915a246000000/Nonlinear-Model-Predictive-Path-Following-Control.pdf)
- [Receding Horizon Tracking Control of Wheeled Mobile Robots](https://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.65.5622&rep=rep1&type=pdf)