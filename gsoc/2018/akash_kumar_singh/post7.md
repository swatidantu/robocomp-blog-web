# Slice

In this post I wanted to write about one of the key components behind the `gazebo-robocomp` integration, **ICE** (Internet Communications Engine) and how it is used the RoboComp framework.

Creating an intelligent robot having autonomous behavior is like creating an artificial mind. It requires a large and complex software architecture which can produce all levels of behavior and reasoning needed to achieve intelligence. And that is what robocomp aims to do as a framework, to create a robotic software fast and effeciently. The problem with building these large software models is the time that it requires in writing the code and troubleshooting it. Most of the time in building these softwares goes in writing the generic code which is needed in every case and sometimes feels redundant to do that.

RoboComp tries to solve this problem. RoboComp helps in building component based software architecture using two **Domain Specific Languages (DSLs)** that have been created to define a component at a very high level of abstraction: **IDSL** (Interface Definition Specific Language) and **CDSL** (Component Definition Specific Language). IDSL helps you write the data structures and functions that a component can implement, require, subscribe to or publish and is a subset of Slice. And here the role of ICE's interface language, Slice, kicks in.

For the people who don't know about ICE, The **Internet Communication Engine** is an object-oriented middleware platform. Fundamentally, this means that Ice provides tools, APIs, and library support for building object-oriented `client-server` applications. Ice applications are suitable for use in heterogeneous environments: client and server can be written in different programming languages, can run on different operating systems and machine architectures, and can communicate using a variety of networking technologies. The source code for these applications is portable regardless of the deployment environment.

**Slice** stands for Specific Language for Ice. It is the fundamental abstraction mechanism which slice uses for separating object interfaces from their implementations. Slice establishes a contract between client and server that describes the types and object interfaces used by an application. This description is independent of the implementation language, so it does not matter whether the client is written in the same language as the server.

## Slice Compiler

A Slice compiler produces source files that must be combined with application code to produce client and server executables. For example, let say we have slice definition of a `Printer` interface, `Printer.ice`. The Slice compiler generates two files from a Slice definition `Printer.ice`: a header file (`Printer.h`) and a source file (`Printer.cpp`). These interfaces are built with everything at hand: libraries, objects, threads, sockets, lambda functions, etc. Everything communication middleware that is necessary to build the software.

## Slice definition: General Structure

Slice defintion of an interface basically contains a layout of the functionalities that you are expecting from an interface, the data types that you will be using, data structures, interfaces, classes, etc. It is like any ordinary cpp files with certain change in keywords. 

**Preprocessor Directives:** Slice supports the same `preprocessor` directives as C++, so you can use directives such as `#include` and `macro` definitions. Slice permits `#include` directives at the beginning of a file. 

```
// File Clock.ice
#ifndef _CLOCK_ICE
#define _CLOCK_ICE

// #include directives here...
// Definitions here...

#endif _CLOCK_ICE
```

**Modules:** Slice provides the `module` construct to alleviate this problem. It is just like a namespace in cpp.

```
module ZeroC {
    module Client {
        // Definitions here...
    };
    module Server {
        // Definitions here...
    };
};
```

A `module` can contain any legal Slice construct, including other module definitions. Using modules to group related definitions together avoids polluting the global namespace and makes accidental name clashes quite unlikely. (You can use a well-known name, such as a company or product name, as the name of the outermost module.)

**Basic Types:** Slice provides a number of built-in basic types: `bool`, `byte`, `short`, `int`, `long`, `float`, `double`, `string`, etc., which can be easily associated with cpp also.

**Structure:** Slice supports `structures` containing one or more named members of arbitrary type, including user-defined complex types. For example:

```
struct TimeOfDay {
    short hour;         // 0 - 23
    short minute;       // 0 - 59
    short second;       // 0 - 59
};
```

**Interface:** One can think of an `interface` definition as the equivalent of the public part of a C++ class definition or as the equivalent of a `Java interface`, and of operation definitions as (virtual) member functions. The only difference is that only operation definitions are allowed to appear inside an interface definition. In particular, you cannot define a type, an `exception`, or a data member inside an `interface`. This does not mean that your object implementation cannot contain state — it can, but how that state is implemented (in the form of data members or otherwise) is hidden from the `client` and, therefore, need not appear in the object's interface definition.

```
interface Clock {
    TimeOfDay getTime();
    void setTime(TimeOfDay time);
};
```

**Classes:** In addition to `interfaces`, Slice permits the definition of `classes`. `Classes` are like `interfaces` in that they can have operations and are like structures in that they can have data members. This leads to hybrid objects that can be treated as interfaces and passed by reference, or can be treated as values and passed by value.

```
class Time {
    short hour;
    short minute;
    short second;
    TimeOfDay getTime();
    void setTime(TimeOfDay time);
};
```
These were some of the common elements of `Slice` which are majorly present in every `slice` definition file.

## Code

```
#ifndef BUMPER_ICE
#define BUMPER_ICE

module RoboCompBumper {

  struct SensorState {
    int idNumber;
    int state;
  };
  dictionary<string,SensorState> SensorStateMap;

  struct SensorParams{
    string name;
    int idNumber;
    float x;
    float y;
    
  };
  sequence<SensorParams> SensorParamsList;

  interface Bumper {
    void enable();
    void disable();
    bool isEnabled();
    void reset();
    SensorStateMap getSensorData();
  };

};

#endif
```

This is the code of `bumper.ice`, one of the interfaces that is used in the integration.
