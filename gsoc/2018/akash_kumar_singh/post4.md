# How can we export the resources of gazebo without using plugin

// how can we use SDF library to parse the sdf file and generate sdf element pointer

// use that element pointer to get the pointer to all the entities present in a simulation

// topics published by default

Gazebo provides a very simple way to export its resources, which are plugins, so we may ask why we need to know about any other things. Plugins are awesome and very handy, which makes it very easy for users to connect to the simulator. But there are other ways besides plugins which, we are pretty cool and provides a deeper understanding about the gazebo's apis, utilities and also can make our applications more flexible.     

```
// check arguments
  if (argc < 2)
  {
    std::cerr << "Usage: " << argv[0]
              << " <sdf-path>" << std::endl;
    return -1;
  }
  const std::string sdfPath(argv[1]);

  // load and check sdf file
  sdf::SDFPtr sdfElement(new sdf::SDF());
  sdf::init(sdfElement);
  if (!sdf::readFile(sdfPath, sdfElement))
  {
    std::cerr << sdfPath << " is not a valid SDF file!" << std::endl;
    return -2;
  }

  ```

  ```

  // start parsing model
  const sdf::ElementPtr rootElement = sdfElement->Root();
  if (!rootElement->HasElement("model"))
  {
    std::cerr << sdfPath << " is not a model SDF file!" << std::endl;
    return -3;
  }
  const sdf::ElementPtr modelElement = rootElement->GetElement("model");
  const std::string modelName = modelElement->Get<std::string>("name");
  std::cout << "Found " << modelName << " model!" << std::endl;
```
```
  // parse model links
  sdf::ElementPtr linkElement = modelElement->GetElement("link");
  while (linkElement)
  {
    const std::string linkName = linkElement->Get<std::string>("name");
    std::cout << "Found " << linkName << " link in "
              << modelName << " model!" << std::endl;
    linkElement = linkElement->GetNextElement("link");
  }
```
```
  // parse model joints
  sdf::ElementPtr jointElement = modelElement->GetElement("joint");
  while (jointElement)
  {
    const std::string jointName = jointElement->Get<std::string>("name");
    std::cout << "Found " << jointName << " joint in "
              << modelName << " model!" << std::endl;

    const sdf::ElementPtr parentElement = jointElement->GetElement("parent");
    const std::string parentLinkName = parentElement->Get<std::string>();

    const sdf::ElementPtr childElement = jointElement->GetElement("child");
    const std::string childLinkName = childElement->Get<std::string>();

    std::cout << "Joint " << jointName << " connects " << parentLinkName
              << " link to " << childLinkName << " link" << std::endl;

    jointElement = jointElement->GetNextElement("joint");
```

This way gazebo actually do things at the startup. Creates a pointer and use the sdf element ptr from the sdf file to get all the information about the world and then use the physics engine to populate and intiate the world. We don't need to use it, because the gazebo does it automatically at the startup, but it doesn't hurt us to know sommething new, things that go beyond the scene.

```
 sdf::ElementPtr worldElem = _elem->GetElement("world");
 physics::WorldPtr world = physics::create_world();
 physics::load_world(world, worldElem);
 public: ModelPtr ModelByName(const std::string &_name) const;
```

```
JointControllerPtr GetJointController ();
const Joint_V & GetJoints () const;
const WorldPtr & GetWorld ();
LinkPtr GetLink (const std::string &_name="canonical") const;
const WorldPtr & GetWorld () const;
```

Sensors are little tougher to get and access. It is not like world, model or link. It is an entity not a physical thing in gazebo, so, it is generally
put by gazebo itself in the simulator. There is only object at first, and to get different sensors, we can just change the type. Gazebo basically
uses its component to generate a virtual environment. For ex: A camera is attached on a model at a particular position relative to model. So, when
we request image, gazebo use that pose to create render the world view from that point of view and show it to the user. It is just like view point which we get on screen when running gazebo. Likewise IMU data can be created just by measuring the accln, velocity and pose of the model, since gazebo has all the information about its elements in the simulation.