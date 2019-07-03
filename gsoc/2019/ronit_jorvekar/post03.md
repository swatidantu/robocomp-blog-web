# Adding pytorch geometric support to client-side and features to the server

July  3, 2019

## Features added to server
Hello, this is an update to the previous post. So according to the previous post, we set up a REST service to parallelise the training of the models with different hyperparameters. The server-side code was pretty basic. Now i have added a feature to recycle the configurations. I have also written a script to visualize the loss against each hyperparameter for valid results.

### Recycling configurations:
This feature helps us to send such configurations to the clients for which no result was received. So all the configurations are tested and no results are lost.

### Visualization against hyperparameter:
This helps us to gain insights from the results on the impact of hyperparameters on the loss. We can design new hyperparameters based on these results and fine tune to achieve better results.

## Pytorch geometric support

[PyTorch Geometric](https://pytorch-geometric.readthedocs.io/en/latest/) is a geometric deep learning extension library for PyTorch. Basically, it provides support for developing deep learning models on graph-like data structures. It has implemented some of the state-of-the-art supporting layers. The work to be done here was to develop the models using the various layers provided. I implemented and tested 4 models namely GAT, RGCN, GCN, and Gated GraphNN. Also, I had to adapt the training script by converting the data to the format required by pytorch geometric. This was because previously the baseline models were implemented using [dgl](https://www.dgl.ai/).   

* * *
*Ronit Jorvekar*
