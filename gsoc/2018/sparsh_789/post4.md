## Making user friendly

If you read my previous blog post, you would be knowing that I added feature to highlight node which user is currently on (in scene tree). Now, It would be great for user if he could be able to do otherway round. Means, to add a feature so that when user click on an object in scene then its properties tab is automatically listed by which user can easily edit properties of corresponding object.

**Now** I will discuss approach, difficulties faced during this work and how I resolved them. For implementing above mentioned feature, I have to use intersector feature of *osg::util* class. First I started with drawing a selection box around an object when we click on it. After I implemented this, I realised that drawing a selection box is not of much use as I already have Highlight Node feature, so we can use it instead of drawing selection box. So, I removed selection box code and started with implementing intersection. After Implementing intersection I was able to get address of *osg::Node* which is intersected in scene. Now, I had to work on getting object's key in IMV, so that I can use key to achieve my final result. For getting key, I used hash array (from key to *osg::Node*). After getting key, I have to link QMouseEvent in OsgView class to our RCinnerModelEditor. After this, my task was almost finished with some less tiresome jobs remaining.

Prime problem I faced in implementing this was taking care of when I add additional functions in OsgView class for my task, it should not affect other robocomp tools like RCinnerModelSimulator which uses OsgView class. So, I have to implement this feature by keeping this problem in mind.

For demo video you can check [here](https://drive.google.com/file/d/1ebCkUipzT525fnVzAiaQRph5aw1-JLcv/view?usp=sharing).

After this, I implemented "start new model" feature. This feature will enable user to make a new model file from scratch. 

I also solved some bugs like improving "create new node" feature. Now, user will not have to save file for viewing new node insertion. Also, I improved synchronization between highlight node feature and rest of the tool.

**Now**, I'll be working on adding features to make tool more convenient for user to use.

Till then, adiós amigos.
