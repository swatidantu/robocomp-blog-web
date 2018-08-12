## Drag and Drop 

If you read by previous post you would be knowing that I added "selecting object by mouse click" function. Now for my final evaluation my mentor pointed some parts of tool that could be improved. So firstly, I worked on those. Major improvements were making selection process of object to change (from simply right click on object to Ctrl + mouse click). Problem I faced in implementing this came when I had to merge osgview.h library with rcinnerModelEditor as all mouse events and key events were captured in osgview.h file and I had to use them in rcinnerModelEditor. For this I used flag system. Second major improvement was to close extra rgbd window which opens whenever we reload or open any other innerModel file. For that I had to see innerModelviewer file. After going through imv file I got to know that extra rgbd window was opening because the instance of cam.viewerCamera was not closing. So I added function in rcinnerModelEditor to close viewerCamera automatically. I solved some other bugs also like reload problem, texture problem, create node form cleaning etc.

Now, one major feature that could be added was **drag and drop**. My mentor instructed me that this feature will be very useful. Now exactly what this feature means. As name suggests with this feature user can easily place or change position of objects in scene with simple mouse drag. So I started implemening this feature.

Now, First thing I had to do for implementing this was to get coordinates of mouse and then convert it into 3D scene coordinates. And as I previously mentioned that all mouse and key events were captured in osgview file so , next step was to transfer captured 3D coordinates in osgview file to rcinnerModelEditor. So, for that I created one global variable in osgview that stored 3D coordinates and then made one function in rcinnerModelEditor that checked if value of that variable changes or not. After getting coordinates I updated trasnform values of selected plane to new coordinates.

**But** one problem still existed which was , while moving objects camera was also moving due to which object was not moving properly. So for that I stopped cameraManipulator while we drag and then set it to current position when we stopped dragging.

There were some other problems also like getting drag and drop function sync with whole code base of rcinnerModelEditor.

For demo video you can check [here](https://drive.google.com/open?id=1Gnh8sVMFqJtkgxIYvZhfrYdafjkjp0Ib).

Now, as tool has reached at its final goal, I will improve tools's look and add help & support feature for users.

Till then, adiós amigos.
