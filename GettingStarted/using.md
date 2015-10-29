Using Feel++
============

# Introduction

We now consider the case where Feel++ has been installed on your system
either via a package manager or via Feel++ build system.

# Checking out your project

First, get a clone of your current project or create a directory and put your code in it.

# Configure

In order to configure your project to use Feel++, you will have to use CMake and add a `CMakeLists.txt` file in the root directory of your sources. To detect your Feel++ installation and configure your application you can use the following file example:
```
cmake_minimum_required(VERSION 2.8)

# This will check for the installed Feel++ library
# If you did not install it in a standard system path,
# you need to specify the FEELPP_DIR variable to the root
# of your installation directory or add the path of your 
# installation in the PATHS section
if ( ${CMAKE_SOURCE_DIR} STREQUAL ${CMAKE_CURRENT_SOURCE_DIR} )
    find_package(Feel++ 
        PATHS $ENV{FEELPP_DIR}/share/feel/cmake 
            /usr/share/feel/cmake 
              /usr/local/share/feel/cmake 
              /opt/share/feel/cmake
    )
endif()

# Then you can add your application and the associated hpp, cpp, geo, msh and cfg files
feelpp_add_application(
 applicationName
  SRCS file.cpp file1.hpp file2.hpp
  GEO geoFile1 geoFile2
  DEFS A_DEF=2
  CFG cfgFile1.cfg cfgFile2.cfg )
```

<!-- Kept for further use
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

-->

Then create a separate build directory (to keep your code separate from build data) and configure your application:

```sh
# Create a build directory
mkdir -p /path/to/build/directory
cd /path/to/build/directory

# Configure your project
cmake /path/to/source/directory \
 -DCMAKE_CXX_COMPILER=/usr/bin/clang++ \
 -DCMAKE_C_COMPILER=/usr/bin/clang \
 -DCMAKE_BUILD_TYPE=RelWithDebInfo
```

# Compile your project

Eventually, you can build your application: 

```cpp
# Build your project, you can use concurrent jobs by
# adding the -j flag, this will reduce the compilation time
make -j 2 feelpp_applicationName
cd ./where/is/my/app
./feelpp_applicationName
```
