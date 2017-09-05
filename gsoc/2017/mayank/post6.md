# 24th July, 2017

# Ice ping for component monitoring

My [last blog post](/web/gsoc/2017/mayank/post5) explained how we can start/stop components through the RCManager GUI, by linking it with Yakuake. One missing piece in this functionality is the ability to tell whether the component is already running or not, before trying to kick start it.

The scenario is as follows. The users require that the RoboComp components be started by firing commands either on the local machine or some remote pc. RoboComp features another nifty tool named RCRemote to support remote execution, wherein the ip address, port etc. information is supplied by the upCommand attribute. We should hence be able to monitor components even if they are not located in the local system. **I highly recommend a quick glance at [this wonderful tutorial](https://github.com/robocomp/robocomp/blob/master/tools/rcremote/README.md) to get a basic understanding of the client-server model used by RoboComp.**

Each of the robotic components acts as a server, which can respond to ping requests. Communications in RoboComp are handled using the ZeroC ICE library. To monitor a component, we perform continuous ice\_ping and wait for a reply from it. A succesful reply indicates that the component is active. Following are some details of the implementation.

**Endpoints**
Open up any sample RoboComp component folder. You may find many of them inside robocomp/components/. cd into the src folder of the component to find a few .py files. Open up <component\_name>.py. Search for the following lines in the .py file:

```python
adapter = ic.createObjectAdapterWithEndpoints("CommonBehavior", "default -p 11000")
adapter.activate()
```

This lines will give the endpoint of the component, which can be understood as its identity. Now lets take a look at a sample component graph xml which involves the use of this component. Notice the opening tag of each component:

```xml
<node endpoint="default: tcp -h localhost -p 11000" alias="com1">
```

The endpoint attribute is the same as denoted above, only with an extra -h parameter, which specifies the IP address of the machine where the component is running. We require the correct endpoint to ice\_ping the component. If you try to ping a component which is down, you will get an Ice.ConnectionRefusedException. An otherwise succesful ping indicates that the component is running fine. This functionality is implemented in the ComponentChecker class inside model.py. We create a separate thread object for each component at initialization, each of which continuously ice\_ping their components and update their status (node color). Stay tuned for more articles on RCManager.

* * * 

[Mayank Kumar](https://github.com/Kmayankkr/)

Email - kr.mayank1997@gmail.com
