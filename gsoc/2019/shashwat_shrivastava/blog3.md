# Dynamic Object Addition, Object Properties Alteration and Linking scene and tree to highlight corresponding object that are selected in tree and vice versa 
July 22, 2019

RCInnerModelSimulator had the option to add object of box shape and sphere shape with any specifications. User can also view the tree of the scene and can also change the texture of the floor. Now user can also add object of cone and cylinder shape.

Manytimes user wants to change the properties of already existing objects in the scene. Therefore functionality to edit existing objects/nodes has been provided. Accompanying this feature a must have feature is to highlight selected object in the scene that is selected in the tree as user should know whose property is getting changed is also added to the simulator.

## Change Object properties dynamically
Previously users had no idea of how the object will look in the scene when added. Thus there were chances that the object added by user will not be what he/she wanted or thought. Therefore, I have added a feature where users can edit the properties of the object he/she added. Users can change the texture, dimensions, position and rotation of the object dynamically. This feature not only works for objects such as plane or transform type rather it works for everything that is present in the scene from camera to robot.

## Add object after preview	
But even after adding this feature it was a bit frustrating for the user to not able to see what exactly will be added when he/she inputs dimensions, position and texture of the object. Therefore my Mentor Pilar Ma'am suggested me to modify object addition in such a way that we have default values in dimensions, position and texture of the object and that object gets added in first place when we select **type of object** option. Thereafter user can dynamically change the properties of object and finally added the object of his choice. Here as before in object addition user will get all the fields to change the properties of the object. 

To accomplish this task of dynamically changing properties of node changes were made to innerModelviewer file in innerModel library.

![alt](pic1_e2.png "Select object in tree and corresponding object getting highlighted ")
*Preview option - Object getting added when selecting 'type of object' with some default values*
![alt](pic2_e2.png "Preview option - Object getting added when selecting type of object with default values")
*Select object in tree and corresponding object getting highlighted in the scene*


## Linking tree and scene in order to find corresponding objects in scene that are selected in tree and vice versa 
When a user wants to change the properties of an object in the scene he/she should know which object he has selected in the scene before changing it's properties. Therefore a node in the scene will get highlighted when a corresponding node is selected in the tree and the same also works vice versa.

RGBD window removal still need to be completed and remove node feature will be implemented. To smoothen the user experience drag and drop feature will be also added and many more things will be added to provide user a wonderful experience of using the simulator. :)
