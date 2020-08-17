# Porting InnerModel APIs from C++ to Python

30th June, 2020

## Change of plans

According to the intial plan we were going to expose the existing C++ APIs to python by using C++
binding libraries such `pybind11` or `boost-python` but upon little consideration and discussion we
decided to simply write the whole library from scratch which also proved to be easier than the
initial plan.

## InnerModel Library

The whole innermodel library can be divided into 4 basic components:

- `InnerModelMaths (InnerModelVector, InnerModelMatrix, InnerModelRTMat, InnerModelRotMat)`
- `InnerModelNode (InnerModelTransform, InnerModelLaser, ...)`
- `InnerModelReader`
- `InnerModelViewer`

`InnerModelMaths` is a group of fundamental math classes (derived from `np.ndarray`) which is used
by rest of the classes for basic operation. `InnerModelNode` along with `InnerModelTransform` (which
inherits `InnerModelNode`) are the base class for all the classes in innermodel lib. `InnerModelReader`
reads the `.xml` file and produces an `InnerModel` object which contains all the information of
particular scene. `InnerModelViewer` is the most important class from the point of view of this
project. The final goal of this project is provide python APIs to developers so that they can easily
visualize and make real time changes to elements and see response in the simulator.

## Current progress

As of today, we have a working prototype for the `InnerModelViewer` class which can do all the basic
things which we had aimed for: visualize an innermodel scene, get image from a prescribed view point,
changing depth map to point cloud, changing position of a body in real time, etc. But there is a lot
to be tested and polished.

**Akash Kumar Singh**
