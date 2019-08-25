I finished the following points from last post's target:

- Improving Feature Vector:
- [x] Quality check on PARAFAC

- Machine Learning methods for improving accuracy
- [x] Transfer Learning
- [x] Multitask Learning
- [x] Ensemblence of neural networks

- [x] Final tunning
- [ ] Implement in RoboComp

## Results:

The extraction of a feature vector using tensor decomposition method PARAFAC did not met my expecations (yet). 
It extracted a feature vector that gave only 20 % accuracy to our classifiers. 
I believe that we should continue looking for a proper feature vector,
because I believe this is an essential step to reach a perfect classification. With a proper feature vector, I suppose that almost any classifier would work correctly. An example that motivates my suposition is the Fisher's iris data set, to which any machine learning technique works well.

Transfer learning results surprised me. Due to random weight initialization, I started getting only 70 % accuracy in the living room environment! Imagine the preocuppation a felt. That proved that it has some local minima to which random initialization would. But with transfer learning, the best weight initialization, where general features had been learned, helping our neural network work properly on any environment chosen.

Ensemblence learning made my network robust. It is composed of several neural network to classify. Any random weight initialization

Also tunned.
What was left to do is to implement it in RoboComp directly, using the Astra camara, which I do not have. One of my mentors offered to provide a file that gave .

This summer was fun, and this project inspires me to continue contributing and developing a tool for active and assistive living, specially for elderly and people with neurological disorders.
the development of this project excites me and Google Summer of Code passed my expectation. It was amazing!
