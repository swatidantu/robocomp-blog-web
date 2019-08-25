# Deletion of object, undo and lot more 
August 25, 2019

## Deletion functionality
Addition of new object is important for an interactive simulator in the way deletion of object is also very important. Hence I implemented object deletion. The preview option also requires hidden deletion functionality in case the user decides to add object and goes in the preview mode but realises he does not want to add and goes out of the preview option then the object added for preview purpose must be deleted internally.

## Addition of all types of object
Sparsh Sir asked me to implement addition of all types of object for example camera, mesh, laser, imu, rgbd and joint. Now simulator has options to add all types of object as mentioned above apart from box, sphere, cylinder and cone that was already there.

## Drag and Drop functionality
Just to easy the user experience drag and drop functionality for objects is added. User can drag any object present in the scene and can place it anywhere dynamically. To drag an object user should press q and right click together over an object to drag it.

## Removal of RGBD window
The toughest part of the project was to remove the previously opened RGBD window whenever the world reloads.
Removal of RGBD was accomplished successfully during this coding period.

## Undo functionality
The last hurdle was to implement Undo functionality. If the user deletes an object by mistake or regrets his/her decision of deleting the object he/she will have the option to undo the deletion. Undo functionality can also get the object back to its initial position after doing undo few times, if the object was dragged to a new position.
 
In the future hover functionality can be improved, redo option can be provided and reset too in the simulator. 
