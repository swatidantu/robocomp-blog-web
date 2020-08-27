
# **The last post**
This is my last post regarding all the work I have done and my experience with RoboComp.

## **Summary of all the work done**
I started out by increasing the speed of graph data generation for training the GNNs, after that was done I seperated the GNNs and CNNs code for cleaner and more structured code base. 
I provided better support for both DGL and PG frameworks in the training loop. I helped in creating a GUI toolkit for collecting the robotic dataset along with that 
I helped in providing more GNN architectures as a usecase for the data collected from the toolkit.

## What I learned
GSoC'20 helped me a lot in learning things like:
1. Using PyTorch to write GNN architectures and ML models in general, I learned about PG and DGL.
2. How to write cleaner code so that everyone in the team can read it and continue help building it.
3. pub/sub communication between two processes.
4. Unix signal handling
5. PyQT and PySide to make GUIs.
6. How to collaborate with a team using git.


## **Final Work**

### **SNGNN: [Github Repository](https://github.com/robocomp/sngnn)**

  * Pull Request : [Link](https://github.com/robocomp/sngnn/pull/12)

## Future work
A thing that can be added is a second use-case to label interactions by building on top of our toolkit.

* * *
I am thankful to my mentors Ronit Jorvekar, Pilar Bachiller, Daniel Rodriguez Criado for helping me when I was stuck.
A special thanks to Luis J. Manso for helping me out in my pre-GSoC period and during GSoC.

* * *
*Rishabh*
