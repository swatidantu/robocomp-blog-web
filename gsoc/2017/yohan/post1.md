# **A Bit About Me**
I am a second year undergraduate student studying in BITS Pilani Hyderabad, India. 
Having been an avid robotics enthusiast, deciding upon roboComp as my organization was no hard task.
Over the past week I spent my time doing the following:
>1. Familiarizing myself with the cortex and DSR architecture and the navigational algorithms they use.
>2. Getting used to rcmanager to deploy roboComp-shelly's componenets

# **A Brief Introduction To Social navigational**
In recent years, several commercial robots have been designed for deployment in hospitals and office 
buildings, typically as couriers for medications, paperwork etc. As more of these robots are being 
used in daily life, it is no longer plausible to treat humans as just some other dynamic obstacle. 
But rather plan our navigation such that robot behavior meets social norms so that the users feel more 
comfortable around the bot. 
The method which I suggested in my proposal was to add variable costs in the path planner, which to some
extent adds social behaviours like passing on the right, personal space etc. These costs are calculated by a 
gaussian function centered on the obstacle, bot, human and the intersection of two gaussian functions.
For the case of humans and the bot this function will be asymmetric as a person has a sense of face direction 
i.e his personal space would be more towards the front than the back. 
Now by changing the weights of these costs different behaviour can be observed.

Over the course of next week I plan on getting started with the implementation alongside my mentor.

* * *
Yohan M R
