# A usecase for the previously built toolkit

## Update about the work:
The basic framework for the tool kit was done in the intial phase after that some remaining future works were left that are done, namely
* Graceful exit: Each component is made to be serially killed. We used a signal handler, when the kill signal is received by each component the handler kills the component.
* Asking for the contributor’s name at startup of the GUI so the files can be saved with that name.




## The usecase:
One way we used the data collected from the toolkit is by training graph based machine learning models to predict the robot's path trajectory to navigate in the social setting.
We trained a series of Graph Neural Nets to find the best working. We tried different variations of graph convolutional network, and some combinations of different GCNs. 
* * *

*Rishabh*


