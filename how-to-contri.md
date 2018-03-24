## How to contribute

Developers needs to clearly identify which space the contribution belongs to, i.e., the native space or the Qt space. The contribution needs to follow the code for each space.

* Contribution to native space should \(mostly\)  be build upon mindskin framework, using targeted native programming language API. 
* Native contributions should not degrade any cross-platform features to platform-dependent features.
* Native contribution should follow the native space design pattern as much as possible.
* Cross-platform features, like computational task, or vehicle working process, should be in first priority be considered contributing into Qt space, using Qt C/C++ mostly.  
* Cross-platform developers should avoid implement cross-platform features through native languages as much as possible.
* Cross-platform contributions should also provide corresponding TAG-core class and helper class for native space access.





