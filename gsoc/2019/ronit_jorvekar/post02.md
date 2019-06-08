# Getting Smart With Hyperparameter tuning Optimization!

June  8, 2019

## Update about the work:
Hello, this is an update to the work being done now. RGCN was already implemented but it was not learning. So my first task was to detect why the network was not learning. I tried testing it with various different configurations. I checked for the gradients and they were too low. According to the insights from my mentors, I tried reducing the self-edges in the network which really helped the network to learn. The network started learning and the gradients improved.

## Hyperparameter tuning Optimization:

So with 3 baseline implementations (GAT, GCN, RGCN), the next task for me was to design a REST service for hyperparameter tuning optimization. It was a client server architecture where the server assigns a configuration with hyperparameters from a pool of configurations to the client. This service helps us to implement a distributed hyperparameter tuning optimization technique. It is actually analogous to the master slave architecture. The server is the master which assigns task to clients with are analogous to slave.
### Steps :
#### 1) The client requests a task
#### 2) The server sends task ie. configuration with hyperparameters to the client
#### 3) The client trains the model with the hyperparameters and returns the best loss and model to the server
#### 4) The server saves the model and collects the result.
The server side service was developed in flask and client side code was developed with requests lib. This included setting up the service at server side. I also included the support for SSL.

### Advantages :
We can train multiple models parallelly which saves huge amount of time. Also anyone can run the client with proper support and environment, which makes it platform independent.  

 #### Problem
 A problem faced by me when actually sending big model was: the server wasn’t accepting big files. The model is saved as a file.
 #### Solution
 After doing some research for the problem, it turned out that I had to modify server side configuration to accept client size body of size more than 1 mb which is set as default by the nginx service.

* * *
*Ronit Jorvekar*
