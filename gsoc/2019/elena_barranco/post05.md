# **Custom interfaces list widget**

One of the most important aspects in which we have been working is in the handling of interfaces. The first step we took was to make a new algorithm to load the interfaces in a dictionary correctly.

Once this dictionary is loaded, we have used it to fill in the widget list of our graphical interface. In this way, the user only has to select a communication type from the combo box and click on one of the interfaces to add the communication to the text editor. The corresponding “imports” are added automatically.

But the own Qt list widget presented one important limitation: it was not possible to add the same element several times so we could not add the same interface with a certain communication type. For that reason, we have developed a new class that represents a custom list widget suitable for our purpose. It works this way:

 - Clicking on an interface with the left mouse button adds it to the cdsl text editor.
 - Pressing Ctrl and clicking different interfaces with the left mouse button adds a list of interfaces to the cdsl text editor.
 - Clicking on an interface that is already clicked with the left mouse button increases the interface counter and adds the same number of interfaces to the text editor.
 - Clicking on an interface that is already clicked with the right mouse button decreases the interface counter and adds the same number of interfaces to the text editor.
 - Clicking a new interface with the left mouse button without pressing Ctrl adds the corresponding interface with the counter set to 1.

**Other issues fixed**

Besides having solved the list widget issue we have also been able to solve the following ones:

 - The main window and its elements are better resizable now. Some layouts were modified and spacers were added. The list widget, main text edit, and console can be expanded and reduced.
 - The first implementations of “reset”, “create” and “generate” buttons were developed.
 - Other minor problems related to the checkboxes, appearance and other functionalities.

Our next step is to improve the behavior of the main text editor to manage errors with the console.

The new graphical interface version with our custom list widget is attached below.

![robocompdslgui_v2](https://github.com/elebarr/web/blob/master/gsoc/2019/elena_barranco/robocompdslgui_v2.png)

