# GSoC'22 RoboComp project: Development on OSRF’s traffic editor

13th June 2022

## Getting Started
As I was only familiar with the traffic-editor, I sought to further understand Robocomp as a framework. What better way to understand Robocomp than to actually try it!

### Installation
From following the instructions on the ```README.md```, the installation was quite smooth.

I will further document my Robocomp starting tutorials in the future...


## Traffic Editor moving to Rust!
On a side note, it came to my attention that the good folks at Open Robotics have been shifting their development of traffic-editor to be [Rust-based!](https://github.com/open-rmf/rmf_sandbox) This will completely change how I'll contribute to this tool - instead of using C++/QT, I'll need to learn Rust/Bevy, an exciting new language and game engine.

Based on my interactions with OSRC, the main motivations for moving to Rust/Bevy are to maximize the __reusability__ of the work we're doing, and the *Entity-Component-System* design of Bevy would allow users to develop the editor features as "systems". These will be able to be mixed-and-matched and extended by downstream users to add more functionality than whatever current developers have in mind.

I'll be testing it out and documenting the new features in my next update!

__Samuel Ang__
