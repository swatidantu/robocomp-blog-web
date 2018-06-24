## Adding new features in Tool

After adding "creating new node" feature in tool, I had to work on user convenience.
I added 2 new features for that :

1. Highlighting node which user has currently selected.(In scene tree).
2. Able to see live changes in width, height, depth and texture of objects while editing corresponding properties.

For demo Video you can check [here](https://drive.google.com/file/d/1wgS0mN0rlc_GR3sbTW5ElMo4nOFE2Kki/view?usp=sharing).

**Now** I will discuss approach, difficulties faced during this work and how I resolved them. In talking with my mentor, he suggested to look on innermodelviewer files for improving editing features of tool. Then I started reading and understanding most of innermodel library files. After getting familiar with innermodel codebase, I first noticed that in RCInnerModelEditor width, height and texture of objects in any scene are not changing spontaneously while user change them in properties tab. For seeing changes user has to save file first and then reload it. After peeking into problem I noticed that InnerModel is updating fine but innermodelviewer is not upadting correctly. There was no function written for updating width, height, depth and texture of InnerModelviewer. After I wrote function then texture was updating correctly but size of objects was still not changing spontaneously. After some search I found out that dirtying display list was not done correctly due to which time for bringing changes in scene was taking extra time. So I included that feature.
After that I worked on highlighting the node feature. As I had done changes in innermodelviewer for updating texture spontaneously, so doing this task was somewhat less tiresome. For this I have to write one function "highlight node" in RcInnerModelEditor. In highlight node, node on which user is currently working is highlighted with blue texture. Once user change any property of node then it comes to original texture.

**After** implementing above features I implemented one of the main feature "removing current node". For demo you can click [here](https://drive.google.com/file/d/16Fv-Vo0qKZjMp78t3NnILn-tstXXaWOU/view?usp=sharing).
There was already a function named "removeNode" in innermodel.cpp which I thought would be sufficient. Like I have to just call the function from RCInnerModelEditor and it will remove node. But not all things can work fine for anyone. Initially I just called the function and result was a familiar name "Segmentation fault". After getting error I First tried to change my RcinnerModelEditor code as I thought that there must be some problem with overlapping signals in my code. But no after a number of tries I figured out that problem is with "removeNode" function in innerModel.cpp file. 
First problem was that function was only removing specific node, not its children.
Second problem(that took much time) was that function was deleting node and removing it from hash table. But not from its parent data. Means node's parent still have that node as its child but node does not exist. So when innerModel file is updated then node's parent call that node but as it is "NULL" so result is segmentation fault.
But seriously while identifying second problem I got frequent with innerModel codebase.
Now after removing node there were still some problems like unsynchronizing of "highlight node" and "remove current node" function, disconnecting some signals while removing nodes. But solutions to these problems were identifiable, hence solved.

Now, I'll work on adding feature of making "new innerModel files from scratch".
You can clone my fork of robocomp for using RCinnerModelEditor. If you notice any issue please share. 
