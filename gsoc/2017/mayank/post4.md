# 1st July, 2017

# QNetworkxGraph widget

Welcome back ! Things are advancing at a very steady pace because of some amazing work by [Esteban](https://github.com/orensbruli), an expert in PyQt UI designing. Remember the MVC model from the previous post ? If not, have a glance at it [here](/web/gsoc/2017/mayank/post3). Today, I am gonna briefly describe the components of viewer.py, in relation to the pivotal work done by Esteban.

According to the MVC model, the viewer.py is the only guy responsible for setting up the entire UI, which is one mammoth task. Again, writing thousands of lines of code in a single file is nothing less than pure disaster. Solution ? Further divide the code.

When you open the RCManager GUI, everything you see happens to be a widget. The initial background of the UI is designed on the Qt4 Designer. We then apply the logger (bottom section), the component graph (top-middle section in tab "Graph"), the code editor (top-middle section in tab "Text") etc. on top of this basic UI, all as independent widgets. Rather than having the codes for these widgets inside the viewer.py, we created separate .py files for each one of them, which now reside inside rcmanager/widgets. Anybody willing to add widgets can create a new file here and import into the viewer.py.

Amongst the widgets, one of the most fundamental ones is the QNetworkxGraph widget, which was developed by Esteban. Since it is a really large component in itself, we decided to have a folder for it. Amongst the many files inside the QNetworkxGraph folder, you may want to take a look at QNetworkxGraph.py. 

The QNetworkxGraph.py is responsible for drawing the nodes and edges in the UI. It contains three class definitions -
1) **QEdgeGraphicItem**
2) **QNodeGraphicItem**
3) **QNetworkxWidget**

The class names are pretty self-explanatory. QEdgeGraphicItem handles drawing of the edge between the nodes, whatever be the spatial position of the nodes. QNodeGraphicItem provides for the shape, color, and the properties (like context menus) for the nodes. QNetworkxWidget uses the above classes to build a graph, based on the information stored in the model.py, and defines the properties of the background of the component graph (color, context menus etc.).

One very innovative paradigm used by Esteban is to allow the usage of CSS type stylesheets for configuring node designs. These stylesheets are nothing but .json files that describe attributes like fillColor, borderWidth etc for a node. You may find some of these stylesheets in the QNetworkxGraph/styles folder. The QNetworkxStylesManager.py is responsible for loading these styles into the QNetworkxGraph.py, from where the developer can use it onto a target node. There are a couple other files in this folder, which make this widget a bit complex to understand. This blog is intended only at providing a very simplistic, high-level description of this widget. Feel free to contact me via GitHub or e-mail, if you need any support.

* * * 

[Mayank Kumar](https://github.com/Kmayankkr/)

Email - kr.mayank1997@gmail.com
