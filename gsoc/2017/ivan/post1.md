# Introduction

28/05/2017

# Who I am?

Hi! My name is Iván Barbecho Delgado, I'm from Extremadura and I was born on 25.04.1994 and I'm finishingthe degree computer engineering in School of Technology of University of Extremadura. Currentlly, I'm working on a project of RoboLab, this consist in implementing a system of recognition and localization the objetcs for the robot Shelly, a robot of attention to the elderly people.

# What will I make?

First, I have studied the project learnbop. After of this, I have changed my timeline, because I thought that I should make a prototype of the user interface before of define a domain-specific language (DSL). In this way, I can define a DSL more pinpoint. Below is the prototype I've done

This prototype have 4 sections, these am "Program (With Text)", "Program (Visual)", "New Funtion" and "Existing functions".

### Program (With Text)

In this section, the user can program the Learnbot, in written form, using the funtions that have been  previously defined. This program is sent to Learnbot to be executed. On the right you can see the robot's camera.

![Image of section Program (With Text)](img/programtext.png)

### Program (Visual)

In this section, the user can program the Learnbot, in visual form, using the funtions that have been  previously defined. This funtions are show on the left, similar to Scratch. This program is sent to Learnbot to be executed.

![Image of section Program (Visual)](img/programvisual.png)

### New Funtion

In this section, the user can append other functions to the DSL in a simple way.

![Image of section New Funtion](img/NewFuntion.png)

### Existing functions

By last, In this section the user can edit the existing functions to the DSL in a simple way.

![Image of section Existing functions](img/existingfunctions.png)

Once the prototype was studied, I can start to define the DSL.

A simple structure to store the functions is save a code of function in a file, whose filename is the the name of function. These files will be saved in directories, whose directory name is a type of funtion.

This funtions will be load in a dictionary whose key will be the name of function and the will be stored the type and the code.

The next step will be make the parser of the DSL.

Finally, I will writen the documentation about all work done in GSoC.

* * *

Iván Barbecho Delgado (@ibarbech)
