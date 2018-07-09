# Gazebo-RoboComp: Integration

Development of connection between robocomp and gazebo was started approx. two months ago, with an aim to extend the capabilties of robocomp show that it can provide its developers with a simulator which has better physics engine and a large community base already using. Now it is here, `gazeboserver`, a tool to connect robocomp with gazebo. So, this post is going to go in detail about the integration.

Following from the previous two posts in which we get to know about the Slice language and Ice interface, that are actually doing the work, now it's the time to explain how these customized classes are actually used to communicate with gazebo. A general idea about the integration can be obtained from this figure.

![Integration Overview](https://raw.githubusercontent.com/ksakash/README/master/gsoc.png)

As you can see all the interfaces are included inside a `server` which is listening to the requests of any `client` that has access to the `endpoint` of the ice objects created inside the `server`. The interfaces uses the base classes generated from the slice definition of interfaces and has all the ice runtime tools needed to have a communication middleware. The classes derived from the base classes have all the transportation tools needed to communicate with gazebo plugins which in turn communicates with the simulator Gazebo. So, whenever a client makes a request, the `server` looks up to its servant object and calls the method needed to get information the interface. Interface returns the data which they have stored in their data members which is then filled from time to time inside the callback funtion, which is called when gazebo plugins publishes something on the corresponding topics. Here is an example of how it's done in the code:

```
#include <Ice/Ice.h>
#include <LaserI.h>
```
`Ice.h` for ice runtime and `LaserI.h` for the interface. 

```
Ice::CommunicatorPtr ic;
int status = 0;
try
{
    ic = Ice::initialize(argc, argv);
    auto adapter = ic->createObjectAdapterWithEndpoints("RoboCompLaserAdapter", "default -p 10000");
    Ice::ObjectPtr object = new LaserI(argc, argv);
    adapter->add(object, Ice::stringToIdentity("RoboCompLaser"));
    adapter->activate();
    ic->waitForShutdown();
}
catch(const Ice::Exception& e)
{
    cerr << e << endl;
    status = 1;
}
```

We initialize the Ice run time by calling `Ice::initialize`. The call to initialize returns a smart pointer to an `Ice::Communicator` object, which is the main object in the Ice run time. We then create an object `adapter` by calling `createObjectAdapterWithEndpoints` on the `Communicator` instance. The arguments we pass are "`RoboCompLaserAdapter`" (which is the name of the adapter) and "`default -p 10000`", which instructs the `adapter` to listen for incoming requests using the default protocol (TCP/IP) at port number 10000. We ceate the servant `Laser` interface by instantiating `LaserI` object. We then register the object with adapter to notify a servant is listening at this endpoint. Then the `adapter` is activated and waits till infinite time to hear the requests from the client. Following the try block there is a catch block which handles all kinds of exception that may happen during the runtime.

Likewise in the client we do nearly the same thing: intialize the ice runtime, instantiate a `proxy` object to make a request to the `endpoint` `RoboCompLaser:default -p 10000`, then the proxy can make the request by accessing the methods provided by the `Laser` interface. Below is the code for this:

```
Ice::CommunicatorPtr ic;
try {
    ic = Ice::initialize(argc, argv);
    Ice::ObjectPrx base = ic->stringToProxy("SimplePrinter:default -p 10000");
    PrinterPrx printer = PrinterPrx::checkedCast(base);
    if (!printer)
        throw "Invalid proxy";

    printer->printString("Hello World!");
} catch (const Ice::Exception& ex) {
    cerr << ex << endl;
    return -1;
}

if (ic)
    ic->destroy();
```

The client is destoryed in the end, when the its purpose is fulfilled which also stops the server.
