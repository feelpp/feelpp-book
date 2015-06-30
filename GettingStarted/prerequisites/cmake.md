##CMAKE
CMake is a tool that helps simplify the build process for development projects across different platforms. CMake automates the generation of buildsystems such as ***Makefiles*** and Visual Studio project files. CMake is controlled by writing instructions in CMakeLists.txt files. Each directory in your project should have a CMakeLists.txt file.

**Building with CMake**   
Setting up a bunch of CMakeLists.txt files will not immediately allow you to build your project. CMake is just a cross platform wrapper around more traditional build systems. In the case of linux, this means make. A quick preprocessing step will convert your CMakeLists.txt description into a traditional make build system automatically. One nice and highly recommended feature of CMake is the ability to do out of source builds. In this way you can make all your .o files, various temporary depend files, and even the binary executables without cluttering up your source tree.   

Here below is a cmake for our simple project.
```sh
set(CMAKE_CXX_COMPILER /usr/bin/clag++ 3.6.0)
cmake_minimum_required(VERSION 2.8.9 FATAL_ERROR)
project(operation)

# Create a library called "operationlibo" which includes the source file "operation.cxx".
# The extension is already found. Any number of sources could be listed here.

option(USE_SHARED 
            "use a shared library" OFF)
            
if(USE_SHARED)

add_library(operationlib SHARED operation.cpp operation.h)  
# Make sure the compiler can find include files for our operation library
# when other libraries or executables link to operation

target_include_directories (operationlib PUBLIC ${CMAKE_CURRENT_SOURCE_DIR})

else()
add_library(operationlib STATIC operation.cpp operation.h)
target_include_directories (operationlib PUBLIC ${CMAKE_CURRENT_SOURCE_DIR})
endif()
# 
# Add executable called "operatiom" that is built from the source files
# "operation.cxx"". The extensions are automatically found.
#

add_executable(operation main.cpp)

# Link the executable to the operation library. Since the operation library has
# public include directories we will use those link directories when building
# operation
#

target_link_libraries(operation LINK_PUBLIC operationlib)

# add a target to generate API documentation with Doxygen
#set OFF if you don't want doxygen to generate a documentation
option(BUILD_DOCUMENTATION "Use Doxygen to create the HTML based API documentation" ON)
if(BUILD_DOCUMENTATION)
find_package(Doxygen)
  if(NOT DOXYGEN_FOUND)
    message(FATAL_ERROR
      "Doxygen is needed to build the documentation. Please install it correctly")
  endif()
  configure_file(${CMAKE_CURRENT_SOURCE_DIR}/Doxyfile.in 
                       ${PROJECT_BINARY_DIR}/Doxyfile @ONLY)
  add_custom_target(doc ALL
             COMMAND ${DOXYGEN_EXECUTABLE} ${PROJECT_BINARY_DIR}/Doxyfile
                  COMMENT "Generating API documentation with Doxygen" VERBATIM)
  #Doxygen will be triggered every time we run make
  # IF you do NOT want the documentation to be generated EVERY time you build the project
  # then leave out the 'ALL' keyword from the above command.                
endif()
```

To use out of source builds, create a build directory in your top-level folder (technically, this can be anywhere, but the top-level project folder seems to be a logical choice). Next, change into your build directory and run cmake pointing it to the directory of the top-level CMakeLists.txt. For example, for our simple project:  
```cd src``` : takes us to the src directory( contains the source code)   
``` ls``` : displays all that is in the src directory   
```mkdir build ``` : Builds the build directory   
```cmake ..``` : Runs cmake pointing it to the src directory   

```sh
MBP-de-winsy-2:stageM1 user$ cd src
MacBook-Pro-de-winsy-2:src user$ ls	
operation.cpp   Doxyfile.in				operation.h
CMakeLists.txt				main.cpp	
MacBook-Pro-de-winsy-2:src user$ mkdir build
MacBook-Pro-de-winsy-2:src user$ ls
operation.cpp	
Doxyfile.in				operation.h
Makefile	CMakeLists.txt	build			main.cpp			
MacBook-Pro-de-winsy-2:src user$ cd build
MacBook-Pro-de-winsy-2:build user$ cmake ..
```

Then run the command. 
```sh
make
``` 

Remember to be in your build directory and point cmake only to the directory containing the top-level CMakeLists.txt file, not the file itself. If all goes well, cmake will process your CMakeLists.txt files, find the location of all libraries and include paths and spew a bunch of configuration information including a traditional ***Makefile*** in your build directory.



This only touches the surface of what CMake can do. Check out the [CMake Wiki](http://www.cmake.org/Wiki/CMake) for more info.
