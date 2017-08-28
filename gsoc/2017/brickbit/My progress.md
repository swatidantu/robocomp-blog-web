# My progress in carrying out this project.
## Initial planning and conception of the robot.
Initially the robot to be constructed as it was exposed in the proposal was composed of two LED matrices, a camera, a servo so that the camera can move in different angles, a pair of motors and a system to determine the position of the Robot not defined in the proposal, to this must be added the battery and the casing, this casing should make visually more attractive the robot. The proposal specified that as part of the project the housing would be designed and each component would be programmed to function in an integrated manner in Robocomp.
![Initial proposal](https://github.com/brickbit/universidad-IP/blob/master/learnbot.jpg)

## Selection of components.
The selection of components took more time than planned because there was not a list of components of the first version of the robot and there were other versions in development so it was decided that the best thing was to try to unify the proposals as a result , the ultrasonic sensors were changed by lasers and their arrangement in the robot changed also, the LED matrices were changed by a TFT screen, the battery was changed by another two-cell LiPo battery with more capacity And as far as the processor is changed the Odroid of the first version of Learnbot by a Raspberry.

## Design.
The design of the new version of Learnbot has had slight modifications that have resulted in an extension in its characteristics and its size because now the battery is removable and has left space for elements not anticipated, this elements have appear by the changes in the components used so, we use a battery that was larger than previously expected, and we used lasers instead of ultrasonics sensors that integrate better in the design but the most drastic change was the replacement of the LED matrices by a TFT screen because we doubted if we needed to add a third matrix to represent the mouth and thus make the robot more expressive.
These changes resulted in several redesigns testing each concept until we realized that a screen would be more useful to represent the eyes, mouth and any other element of the robot that we wanted and at the same time would be easier to integrate properly in the design.
On the other hand the printing and testing of the pieces has been a big problem because at the time of printing there was at that time a printer that worked correctly so I initially used my own printer to test the pieces however, this also broke and I ended up fixing the organization's printer which meant more delays regarding the time provided to solve this part. Nevertheless the result has been quite satisfactory.

## Screen and expressions of the robot.
The installation of the screen required a series of tests because as it was proposed its installation required the use of all the pins of the Raspberry Pi which was not viable because we needed the pins to operate with other components so I searched (without Success) screen info to see what pins I needed but I did not find so I decided to try the pins myself connecting all the pins and disconnecting the pins one by one to discard unnecessary pins by trial and error.
Next I installed a version of Raspbian that supported the screen and the necessary configurations were made.
On the other hand the objective of the screen was that it showed the expressions of the robot for it was done a graphical interface in tkinter in which when starting the application gave you to choose the aspect that you wanted the robot choosing a json file or other, also the application allowed you to choose which elements of the face you wanted to be represented, eyes, eyebrows, irises, eyelashes, mouth, etc. resulting in a broadly configurable robot.
Despite this, my mentor and other members of the organization made me understand that it was better to use _qt_ concretely _pyqt_ to do these tasks because it was the one they were using regularly in robocomp so, I started working on it, I just need to configure the animations of the application so that it is ready.

## Learnbot Camera Relay 2.0
To do this task I look for solutions already realized because I understand that it does not make much sense to make a version of itself when there are many open source versions  of it so I found several solutions discarding those that were incompatible by the type of license and chose two that I especially liked one of them was streaming through vlc and the other through a web, of them I picked out the web version since the other one presented more delay in the image.

## Servomotor
To move the servomotor I used the GPIO library although the original idea was to use wiringPi since it was the library used in the first version of Learnbot to move the motors however, I have not been able to correctly run the programs that use that library because in a principle and despite installing wiringPi as indicated on the official page an import error happened, after searching for various webs I found the solution to that problem which is nothing more than adding to the "-u" installation command and putting the File in the same folder where wiringPi is installed. With the above we solved the problem of import however, every time a wiringpi-based application is run the operating system hangs, I tested it with various pins and even with code provided by Adafruit and other companies like Pololu to run servomotors with wiringpi but the result was always the same, the system hangs. So I finally adopted a solution based on the GPIO library.

## Motors
At first the idea was to take advantage of the code of the first version of Learnbot but the inability to use so far wiringpi upset the plans, however the plan has not changed and I think I will finally be able to run the program with wiringpi.However the tests with this library have taken me a long time and this is linked to an error in the voltage regulator that we had bought that did not admit the battery voltage impeded to finish this section nevertheless, I am waiting to receive a regulator that works and To advance in this section.

## Laser
In this case we used a translation to python of libraries provided by Pololu that although it works does not provide correct data so I decided not to incorporate it into the project.

## Summary
Finally, as a summary, I make a comparison of the initial objectives, the changes established and the objectives achieved.

## Conclusion:
