# ICE Interface

Following my previous blog on slice, this post will be about using the source files generated from the slice definition. So, with our previous example, we had two files generated from `Printer.ice` file: `Printer.h` and `Printer.cpp`. The `Printer.h` header file contains C++ type definitions that correspond to the Slice definitions for our `Printer` interface. This header file must be included in both the `client` and the `server` source code. The `Printer.cpp` file contains the source code for our `Printer` interface. The generated source contains type-specific run-time support for both clients and servers. So, the source files contain all the middleware stuff: libraries, communication interfaces, etc., so that we don't have to deal with the generic and repeating code. 

Then we come to the next phase: using the source code `Printer.h` and `Printer.cpp` and customizing the definitions to our own needs. For example: let say we have bumper.h from bumper.ice, so we make another class from the abstract class defined in the slice definition and then override the functions according to our needs and later those customized classes can be included in server and client to carry the necessary task which bumper.ice was meant for.

## Bumper Interface: Gazebo-RoboComp Ice Interface

In the last post I had given a sample code for the slice definition of bumper, here I will show how to use the generated souce files and a general structure of the interfaces used in the integration. So, here are the code snippets of the derived class `bumperI`.

```
#include <Ice/Ice.h>
#include "bumper.h"
```
`Ice.h` contains the definition of Ice runtime. `bumper.h` contains the definition of base class `bumper`.

```
#include <gazebo/gazebo.hh>
#include <gazebo/transport/transport.hh>
#include <gazebo/common/Time.hh>
#include <gazebo/common/Plugin.hh>
#include <gazebo/common/Events.hh>
#include <gazebo/transport/TransportTypes.hh>
#include <gazebo/msgs/msgs.hh>
```
These are the necessary gazebo includes, so to get information from the gazebo topics and send commands to gazebo plugins.

```
bumperI(int argc, char **argv);
~bumperI();
```

These are the `contructor` and `destructor` of `bumperI` class. Constuctor is used to initialize all the gazebo transportation services like gazebo `Node`, `Publisher` and `Subscriber`, topic names, etc. Here is the definition of constructor:

```
gazebo::client::setup(argc, argv);
this->device_name_ = "gazebo_robocomp_bumper";
this->topic_name_ = "";
this->gazebo_node_ = gazebo::transport::NodePtr(new gazebo::transport::Node());
this->gazebo_node_->Init();
this->laser_scan_sub_ = this->gazebo_node_->Subscribe(topic_name_, &bumperI::callback, this);
```

Now comes the functionality which we need to achieve from our interface, the member functions. In this case, of a sensor, it helps to get data from the sensor in gazebo simulator and also checks whether it is active or not.

```
virtual void enable(const Ice::Current&) override;
virtual void disable(const Ice::Current&) override;
virtual bool isEnabled(const Ice::Current&) override;
virtual void reset(const Ice::Current&) override;
virtual SensorStateMap getSensorData(const Ice::Current&) override;
```

Nearly every interface has a callback function which receives a call when something is published on gazebo topics, which are the primary source of communication between the ice interface and gazebo plugins. 

```
void callback(ConstContactsPtr &_msg);
```
Next are necessary data members which are needed to store some of the crucial information about the interface.

```
gazebo::transport::NodePtr gazebo_node_;
gazebo::transport::SubscriberPtr laser_scan_sub_;
std::string topic_name_;
string device_name_;
```

And then these interfaces are ready to go. You just need to include these inside your server to use the object and serve the client.

* * *
*Akash Kumar Singh*