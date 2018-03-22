# Concepts

Central includes 2 major technologies, the MindSkin framework, and the DroneTag technology.

## The MindSkin Frame Work

Central is built on top of QGC project, which is a pure Qt based system. To introduce native user experience platform-dependent programming languages need to be introduced into Qt, like Obj-C, java, or Swift. The MindSkin framework defines 2 abstract layers between QGC and other application components written in other language: the TAG-Core layer and the MindSkin layer.

![](/assets/Screen Shot 2018-03-21 at 10.25.40 PM.png)

An important concept in Central is the application of DroneTag. DroneTag is a technology that allowing an user to access UAV components in a contactless or cable free style, and provide telemetry feedback over-the-air, through radios including but not limited to BLE/Wifi/RFID.

## TAG-Core layer

The TAG-Core layer is an abstraction of the exchange of data between UI to QGC core classes. It is mainly implemented in Qt C/C++. It is the encapsulation of set of QGC core functions to interact with upper layer of code. It isolates Central application into 2 spaces: the Qt space, and the native space. With the evolution of QGC core classes, this layer may also evolves accordingly.

Developers add their code into corresponding space depends on the targets and features they want to achieve.

## MindSkin layer

On top of TAG-Core layer is the MindSkin layer. It provides native platform programming APIs to developers, so they do not need to access Qt classes. The MindSkin layer is an abstraction of control and data flows in native programming model, which brings in extensive native user experience in while still following the same framework interface. Developers build their own native UI above the MindSkin layer. They can choose to build Android native UI, iOS native UI, MAC native UI, etc. The native UIs can be configured in parallel with the original Qt UI.

For example, Android developers can use Java API to add UI components, and iOS developers can use Obj-C API to build iOS specific UI components, while Qt fans can still use original Qt based UI.

## Pattern of development using MindSkin framework

It is important to understand the **pattern of development under MindSkin framework** when trying extend Central with native features. Central is a cross-platform, mixed languages application system, so when you bring native platform features in you need to be careful not to break the cross-platform capability of those non-native parts, as well as potential conflicts with models of other programming languages.

Here is the general codes to follow.

The Central application is divided into 'Native space' and 'Qt space'. Features of Central application are grouped into "cross-platform" features and "native" features.

For UI customization or native platform enhancement developers, native space is mostly the space they should work on. The code should \(mostly\)  be added into native space. Native developers should not degrade any cross-platform features to platform-dependent features.

For core feature enhancements developers who targets to add cross-platform capabilities, Qt space will be the most appropriate space to work on so the efforts can maintain cross-platform.The code should be added into "Qt" space mostly.  Cross-platform developers should avoid implement cross-platform features through native languages.

## ![](/assets/Screen Shot 2018-03-22 at 4.45.06 PM.png)

## 

## Native space design pattern

Native developers should follow the native space design pattern to harmony the co-existing with other components in the system. Developers should understand proxy class, delegate class, and helper class in the framework. During implementation, developers should follow the forward invocation pattern, UI synchronization pattern, and UI call back pattern. 

These patterns are detailed explained in Dev guides. 



![](/assets/Screen Shot 2018-03-23 at 1.01.07 AM.png)

## 

## DroneTag API

DroneTag is set of protocols between users/pilots and managed UAV/components that allow users to access/configure drone components over-the-air using near-fielding sensing technology.





