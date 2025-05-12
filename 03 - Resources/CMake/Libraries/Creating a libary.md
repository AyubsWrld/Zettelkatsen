We utilize the `add_library()` function to create libraries. The resulting libraries are either: 
- **Static** : `add_library(MyLibrary STATIC source1.cpp source2.cpp)`
- **Dynamic**: `add_library(MyLibrary SHARED source1.cpp source2.cpp)`
- **Object**: `add_library(MyLibrary OBJECT source1.cpp source2.cpp)`
___
Tags : #programming #cmake