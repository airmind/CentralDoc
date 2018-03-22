# Concepts

Central includes 2 major technologies, the MindSkin framework, and the DroneTag technology.

## The MindSkin Frame Work

Central is built on top of QGC project, which is a pure Qt based system. To introduce native user experience platform-dependent programming languages need to be introduced into Qt, like Obj-C, java, or Swift. The MindSkin framework defines 2 abstract layers between QGC and other application components written in other language.  

The TAG-Core layer is an abstraction of the exchange of data between UI to QGC core classes. On top of TAG-Core layer is the MindSkin layer. The MindSkin layer is an abstraction of control and data flows in native programming model, which brings in extensive native user interface in while still following the same framework interface. Developers build their own native UI above the MindSkin layer. Developers can choose to build Android native UI, iOS native UI, MAC native UI, etc. The native UIs can be configured in parallel with the original Qt UI.



![](/assets/Screen Shot 2018-03-21 at 10.25.40 PM.png)



An important concept in Central is the application of DroneTag. DroneTag is a technology that allowing an user to access UAV components in a contactless or cable free style, and provide telemetry feedback over-the-air, through radios including but not limited to BLE/Wifi/RFID.

## TAG-Core layer

The TAG-Core layer is mainly implemented in Qt C/C++. It isolates Central application into 2 spaces: the Qt space, and the native space. Developers add their code into corresponding space depends on the targets and features they want to achieve. 

![](/assets/Screen Shot 2018-03-22 at 4.45.06 PM.png)

For UI customization or native platform enhancement developers, native space is mostly the space they work on. For core feature enhancement developers, Qt space will be the most appropriate space to work on so the efforts can maintain cross-platform. With the evolution of QGC core classes, this layer may also evolves accordingly. 

## MindSkin layer

MindSkin provides native programming APIs to developers, so they do not need to access Qt classes. For example, Android developers can use Java API to add UI components, and iOS developers can use Obj-C API to build iOS specific UI components.  

## Native space design pattern

![](NativeEnhPattern.png)

## DroneTag API

DroneTag is set of protocols between users/pilots and managed UAV/components that allow users to access/configure drone components over-the-air using near-fielding sensing technology.

