Introduction

As stated in the introduction, AGM has not been maintained for a long time. That is why several problems have appeared during the installation process. 
In this post we will talk about them.

Robocomp Installation:

To install robocomp, we follow the installation instructions that appear on the robocomp github itself (https://github.com/robocomp/robocomp). 
After completing all the steps, there were still some errors to fix when trying to run it.

The first error that came up was that rich lib could not be found, and we fixed it simply by installing rich lib. So we had to fix a second error by also installing promp_toolkit. 
After this Robocomp was working correctly.

AGM installation:

After installing Robocomp, the next step was to install AGM. For this, the tutorial that comes on AGM's own github (https://github.com/ljmanso/AGM) was followed. 
It is once this tutorial is completed where our project itself begins.

As stated above, AGM has not been updated in a long time. This is why it has been necessary to fix several errors and make some changes to the 
program to get it started (even using python 2).
 
First, some libraries had to be installed on the computer (libboost, libxml2 and pyside). 
Once installed, two independent pips had to be installed, so that when using the pip command we used python 2 and when using pip3 we used python 3. 
In this way we know that if the program works correctly in python 2, any error is due to the differences between python 2 and python 3 and therefore fixing it is part of the port.

After having our two independent pips (pip and pip3) we had to download an old version of osgQT, since AGM uses libraries that do not exist in the new version of osgQT.
Also, since AGM was intended for an older version of robocomp, it was also necessary to take some .ice files from an older version of robocomp and add them to our working 
version of robocomp. Luckily it was not necessary to make any more changes to robocomp, just add those files.

After doing all this, AGM began to work correctly in python 2, and therefore the installation and set-up was completed, and the port process will begin our next step.

