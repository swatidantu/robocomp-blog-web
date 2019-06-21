# First weeks

It has been 3 weeks since the coding time started and this is what we have done until now:

The first thing to do was to update the python version of robocompdsl-gui main file from Python2 and PySide to Python3 with PySide2. Every file that we're developing in the future will be written in these new versions in order to adjust our system to the most updated technologies.

The second thing to do was related to the checker that we want to develop. So the first task we have done is to test the current parser deeply and detect the requirements of our new parser, as well as wich restrictions have to be considerer.

# Parser/checker

We have identified two different levels in the development of a checker. The first one, syntactic level, is almost completly done according to our tests and thank to the parseCDSL files. The second level, the semantical one, has to be writen from the beggining.

The requirements of the first level are the following:

 - The system should return the line where the file is not correct and the reason. In this way the user receive a hint to solve the problem.

The requirements for this second level are:

 - Check if the interfaces used in "communications" are imported correctly.
 - When "innermodelViewer" selected the only language that can be used is C++.
 - When "innermodelViewer" selected it is mandatory to use QtGui.

These requeriments are being developed at the moment.
