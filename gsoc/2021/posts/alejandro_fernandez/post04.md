# Setting the environment for LearnBlock and firsts steps to build the model

_9 July, 2021_

## Introduction

After selecting the possible models for the component we need to start building the component, but is necessary to setting an environment with RoboComp and LearnBlock and familiarize myself with them.

## Environment setting

Firstly, I installed [RoboComp](https://github.com/robocomp/robocomp) following the instructions of the repository. The process was longer than I expected, but more or less easy.
After that, I started to install LearnBlock and in this case wasn´t so easy. I have a some problems relate to the version of PySide, I solved these problems changing the requirements.txt, concretely putting PySide2 instead of PySide.
But the greatest problem was about dlib that it wasn´t capable of installing, so finally my tutors suggested to not install this library as is only necessary for one concrete component.

__Alejandro Fernández Camello__
