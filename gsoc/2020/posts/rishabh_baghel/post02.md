# Speedup in graph creation, separation of GNNs and CNNs and support for DGL and PG

## Update about the work:
We had an issue that the graph creation took a long time when training the model. Also we needed to separate the code such that we can have different files for GNNs and CNNs. 

## Speedup in graph creation:

Basically when the graph was getting created, we had two graphs, one graph which was dynamic in nature with different nodes and edges, and the other graph which was static and didn't change throughout. The issue was that the static graph was also getting created along with the dynamic graph each time, and the creation of static graph took O(n^2) time. I improved the speed of the graph formation by initializing the static graph as a class method which helped in creating the static graph only once while creating dynamic graph as required.

### Separation of GNNs and CNNs :
Previously we had a single code for the whole architecture which contained both GNNs and CNNs. I created two directory structure and separated the GNNs part from the CNNs, for reducing code cluter, increasing code modularity and code reusability.

### Support for DGL and PG :
The GNNs architectures are implemented in two different libraries, first is Deep Graph Library (DGL) and the second is PyTorch Geometric (PG). I made the training of the model in such a way that it can be done either from architectures implemented in DGL or PG, therefore using the best of both worlds.

* * *

*Rishabh*

