Using Feel++
============

> **todo** rewrite this file entirely. It should present how to use Feel++ in a project

# Introduction

We now consider the case where Feel++ has been installed on your system
either via a package manager or via Feel++ build system.

# Configure

In order to take care of that various situation, here is provided a default `CMakeLists.txt` to be put at the top of your project directory:
```cmake
cmake_minimum_required(VERSION 2.8)
if ( ${CMAKE_SOURCE_DIR} STREQUAL ${CMAKE_CURRENT_SOURCE_DIR} )
 FIND_PATH(FEELPP_CMAKE_MODULES FindFeel++.cmake
      PATH  /usr/share/feel/cmake/modules/
         /usr/local/share/feel/cmake/modules/
         /where/I/have/installed/feel++ )
 if ( FEELPP_CMAKE_MODULES )
  set(CMAKE_MODULE_PATH ${FEELPP_CMAKE_MODULES})
 else()
  message(FATAL_ERROR "Feel++ does not seem to have been installed on this platform")
 endif()
 Find_Package(Feel++)
endif()
feelpp_add_application(
 applicationName
  SRCS file.cpp file1.hpp file2.hpp
  GEO geoFile1 geoFile2
  DEFS A_DEF=2
  CFG cfgFile1.cfg cfgFile2.cfg )
```

```sh
 cmake /root/directory \
  -DCMAKE_CXX_COMPILER=/usr/bin/clang++ \
  -DCMAKE_C_COMPILER=/usr/bin/clang \
  -DCMAKE_BUILD_TYPE=RelWithDebInfo
```

# Compile

```cpp
 cmake -DCMAKE_CXX_COMPILER=/usr/bin/clang++ /root/directory
 make -n 2 feelpp_applicationName
 cd where/is/my/app
 ./feelpp_applicationName
```
