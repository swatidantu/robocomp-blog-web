# InnerModel and PyBullet

In this post we will talk about the features needed by the InnerModel lib and features provided by the
PyBullet lib. We will analysis the kind of control that the PyBullet lib provides, how many different
ways we can render something, how a multilink body is organised in its APIs, how the compromises
have to be made because of some features which pybullet can not provide

- As I had already described in the last post, InnerModel lib is C++ library, used to represent
  an innermodel scene describes as an xml file. InnerModel C++ uses openscene graph lib for rendering
  all the graphics

- The features that innermodel C++ provides:
  - control of the robot through joints
  - giving access to the camera from different points of view
  - providing access to a debug window
  - point cloud
  - lasers
  - moving a body
  - joint control

- So let me talk one by one how the APIs provide PyBullet lib achieves these requirements
  - One of the first challenges we face is how to represent a body, because in PyBullet only after
    creating a body one can render anything in PyBullet. The other way is to feed a urdf file, which
    is completely different case. `createMultiBody()` is the API used to form a body. It needs various
    attributes to render the body but two of the most important ones are `collisionShapeIndex` and
    `visualShapeIndex` which is created by `createVisualShape()` and `createCollisionShape()` which
    takes in 3D mesh files are argument.

  - So from above we can infer that creating a body is the first and the most important thing we require
    in PyBullet. So how do we read separate different bodies from an `xml` file. The manner in which
    `xml` for innermodel is written is particularly different from the likes of ROS's `urdf` or `sdf`
    where there are tags which differentiate between parent link and child link. So some thought has
    to be given before reading and writing the `xml`. The way it is done now is by considering the
    children of innermodel parent tag (`<innermodel>`) or transform tag with "world" as id
    (`<transform id="world">`), at the beginning of the file. Beginning of a body is always a transform
    tag (`<transform id="name">`) with name of the body as its id. After we have declared the container
    for the whole body, what can we do with it. So inside the body tag we can have mesh tag (`<mesh>`)
    to include mesh files or for simple cuboidal shape we include planes (`<plane>`). To specify
    transformation between the different component of a robot we use transform tag (`<transform>`).
    For including any sensor in the robot we just put a tag of that name (`<laser>, <camera>, etc`).

  - One of the most important sensor that a simulator has to provide is camera. PyBullet provides
    `getCameraImage()` and `getDebugVisualizerCamera()` for getting images from the simulator.
    `getDebugVisualizerCamera()` is used to get default GUI that all the simulators give. While on the
    other hand `getCameraImage()` is used to get from any point of view. The API require camera speci-
    fications like focal length, near and far distance, width and length of the image. while on the
    other hand `getDebugVisualizerCamera()` doesn't require any requirements at all.

  - Next is point cloud. PyBullet doesn't have anything direct for point cloud but we can have a work
    around which creates a very coarse point cloud but point cloud all the same. We use the position
    of the camera and where the light rays from the camera might intersect with the objects in the
    simulation to get a depth image and from that depth image we can render tiny spheres in the
    GUI to make it appear like a point cloud

  - For lasers, PyBullet does have an API which lets emulate laser rays. `rayTestBatch()` is an API
    which takes two arrays: from & to denoting source and desitnation of laser rays and outputs the
    3D points intersection points. These rays can be further visualized using `addUserDebugLine()`
    which can render a line of any color from a source and a destination.

  - The innermodel lib can also support IMU and that can be easily implemented in PyBullet as it has
    an API `getBaseVelocity()` which outputs velocity of a body, from which we can derive the accln.

  - The next most important thing we want in a simulator is control. How can we change position of a
    body? There are two ways we can exert control on a body in PyBullet, either move the whole
    body or just control the joints of the body. `resetBasePositionAndOrientation()` resets the position
    and orientation of the base of a body taking two arguments of reset position and reset orientation.
    The other way through joint is by `setJointMotorControl2()` through which we can set target position
    target velocity and force as arguments which can also vary the parameters of position gain,
    velocity gain, etc.







