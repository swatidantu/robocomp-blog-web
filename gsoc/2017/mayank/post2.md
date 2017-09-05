# 10th June, 2017

# Adding pan support

Today seems to be a nice day to write about what I have been doing, since my last blog post. The first and foremost milestone for almost every GSoC candidate is understanding the part of the codebase which he/she will be contributing to, and it was no different for me.

I spent a few days learning about the existing code for rcmanager. It went smoothly because of some of my prior understanding of this tool, and this [awesome blog post](/web/gsoc/2016/basil/page2) by BasilMVarghese, a former GSoC candidate with RoboComp. I urge the readers to go through the post to get an overview of the basic components of rcmanager.

My first task was related to the main window of rcmanager, which displays the entire component graph and lets users interact with it through the GUI. More specifically, I had to work on the QGraphicsView subclass named "ComponentTree", and add support for panning the graph horizontally and vertically. Panning is an indispensable feature when working with large component graphs which do not fit entirely in one window.

I tried a couple of ways to implement the core functionality. One was to use the translate() function of QGraphicsView to move the graph along X and Y axes. Unfortunately, the function seems to have flaws in it, as many online sources mentioned, although similar transformation functions like scale(), rotate(), etc. which are also packaged with QGraphicsView, seem to work fine.

The second method was also suggested by an online source. To understand this, we may first look at QGraphicsView. QGraphicsView uses another Qt object, known as QGraphicsScene, as a kind of canvas beneath it, on which it draws its component graph. The idea is to enlarge this canvas to a very large dimension, say 1000 times its original size, which will automatically bring up the horizontal and vertical scroll bars. The scroll bars can then be scrolled appropriately to shift the component graph along both the axes. The size used should be so huge that practically no user would have a component graph that massive and the need to pan away to the edge of the scene. This technique worked fine.

After getting pan to work, the next task was to assign a nice hotkey to this functionality. There are many choices for this, say Middle mouse button, Ctrl + Left mouse button, Ctrl + Right mouse button, Shift + some keys, etc. This thing requires a lot of thought, since it directly affects user experience, and as my mentor Dr. Pablo quotes - "Panning and zooming must be really comfortable and intuitive since they are very common functions". I took reference from the already existing conventions, in softwares like Inkscape, and am still to decide which hotkey to finally go forward with.

Apart from this, I had a few fixes to add to rcmanager like centering the component graph on startup, modifying the refresh graph function, resolving a few merge conflicts, which arose because a few of my former pull requests to rcmanager got merged  :smile: :smile: :smile:. Over the next week, I will be working on the auto positioning algorithm and its implementation, and will surely describe these things in detail in my next blog post. Stay tuned.

* * * 
[Mayank Kumar](https://github.com/Kmayankkr/)

Email - kr.mayank1997@gmail.com
