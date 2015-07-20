#  cmakeLists.txt; 
#
#  Author(s): Ahmed Bachir <albachirou@gmail.com>
#             Kyoshe Winstone <wkyoshe@gmail.com>
#       Date: 2015-07-20
#
#  Université de Strasbourg.
#
# Distributed under the GPL(GNU Public License):
# This program is free software; you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation; either version 2 of the License, or
# (at your option) any later version.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#


#set the CMAKE_CXX_COMPILER
#set(CMAKE_CXX_COMPILER /usr/bin/clag++ 3.6.0)
cmake_minimum_required(VERSION 2.8.9 FATAL_ERROR)
project(feelpp)

# Create a library called "feelpplib" which includes the source file ".cxx".
# The extension is already found. Any number of sources could be listed here.

option(USE_SHARED 
            "use a shared library" OFF)
            
if(USE_SHARED)

add_library(feelpplib SHARED environment.cpp mesh.cpp mybackend.cpp myexporter.cpp myexpression.cpp myfunctionspace.cpp myfunctor.cpp myintegrals.cpp mylaplacian.cpp
mymesh.cpp mymeshfromstring.cpp mystokes.cpp
)  
# Make sure the compiler can find include files for our operation library
# when other libraries or executables link to operation

target_include_directories (feelpplib PUBLIC ${CMAKE_CURRENT_SOURCE_DIR})

else()
add_library(feelpplib STATIC environment.cpp mesh.cpp mybackend.cpp myexporter.cpp myexpression.cpp myfunctionspace.cpp myfunctor.cpp myintegrals.cpp mylaplacian.cpp
mymesh.cpp mymeshfromstring.cpp mystokes.cpp)
target_include_directories (feelpplib PUBLIC ${CMAKE_CURRENT_SOURCE_DIR})
endif()
# 
# Add executable called "operatiom" that is built from the source files
# "operation.cxx"". The extensions are automatically found.
#

add_executable(feelpp environment.cpp mesh.cpp mybackend.cpp myexporter.cpp myexpression.cpp myfunctionspace.cpp myfunctor.cpp myintegrals.cpp mylaplacian.cpp
mymesh.cpp mymeshfromstring.cpp mystokes.cpp)

# Link the executable to the operation library. Since the operation library has
# public include directories we will use those link directories when building
# operation
#

target_link_libraries(feelpp LINK_PUBLIC feelpplib)
