#set(CMAKE_CXX_COMPILER /usr/bin/clag++ 3.6.0)
cmake_minimum_required(VERSION 2.8.9 FATAL_ERROR)
project(operation)

# Create a library called "operationlib" which includes the source file "operation.cxx".
# The extension is already found. Any number of sources could be listed here.

option(USE_SHARED "use a shared library" OFF)
            
if(USE_SHARED)
add_library(operationlib SHARED operation.cpp operation.h)  
# Make sure the compiler can find include files for our operation library
# when other libraries or executables link to operation
target_include_directories (operationlib PUBLIC ${CMAKE_CURRENT_SOURCE_DIR})

else()
add_library(operationlib STATIC operation.cpp operation.h)
target_include_directories (operationlib PUBLIC ${CMAKE_CURRENT_SOURCE_DIR})
endif()

# Add executable called "operation" that is built from the source files "operation.cxx"". The extensions are automatically found.
add_executable(operation main.cpp)

# Link the executable to the operation library. Since the operation library has public include directories we will use those link directories when building operation
target_link_libraries(operation LINK_PUBLIC operationlib)   
