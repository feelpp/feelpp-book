##DOXYGEN
Doxygen is a tool for auto-generating API documentation. It generates documentation from annotated C++ sources, but it also supports other popular programming languages such as C, Objective-C, C#, PHP, Java, Python, IDL (Corba, Microsoft, and UNO/OpenOffice flavors), Fortran, VHDL, Tcl, and to some extent D.The main advantage of Doxygen is that you can write documentation directly within the comments of your source code. Doxygen searches for source code in your tree and generates API documentation for it.   
  - It can generate an on-line documentation browser (in HTML) and/or an off-line reference manual in LaTeX  from a set of documented source files. 
  - You can configure doxygen to extract the code structure from undocumented source files. This is very useful to quickly find your way in large source distributions.Doxygen can also visualize the relations between the various elements by means of include dependency graphs, inheritance diagrams, and collaboration diagrams, which are all generated automatically.   
  - You can also use doxygen for creating normal documentation.

**So, what's the value to Doxygen?**

Some of Doxygen's output is extracted from the semantics of the source programs. Other parts are from special comments you embed in your code. The entire process requires a special configuration file that specifies exactly what you want to do. Just as your development directory usually has a *makefile* that controls the build process, you also have a *Doxyfile* that contains the options used by Doxygen. This is simply a free-form text file that has options variables and their values. Doxygen automatically generates an example Doxyfile for you on request.

The source comments can use any of three formats:   
 1. Special comments can mimic a Javadoc comment by using an extra asterisk in a multiline comment
 
 ```sh
     /**
      *@brief     operation.
      *@date      june 19, 2015
      *@author:   kyoshe winstone
      *@version   1.1
       */
     ```
 - You can also use an exclamation point instead of the second asterisk 
  
 ```sh
      /*!
       *x is variable
       *y is variable too
       */
       ```
 - Two or more single line comments ```(//)``` that have at least one extra slash or exclamation point following the comment marker also form a special comment.
 ```sh
///
/// @return the x value
///
```
 
**Tags**:

Special comments can contain Doxygen tags that let you specify particulars about your program. By default, comments refer to the next lexical element, for example:
```sh
   /***
     *@brief, which provides a brief description of the function.
     *@param, which identifies a single parameter to the function (you may have more than one param tag).
     *@return, which describes the function's return value.
     *@date, which describes the date of documentation
     *@todo
     */
```

We can configure our cmake system to enable Doxygen to automatically generate an API documentation when we run ```make```   commands.    
To generate a documentation for our simple simple project using doxygen, add to our CMakeLists.txt the following:

```sh
# add a target to generate API documentation with Doxygen
#set OFF if you don't want Doxygen to generate the documentation
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
To generate the documentation, we have to set   
```option(BUID_DOCUMENTATION = ON)``` and ```OFF```  if we don't desire a documentation.

*NOTE* : To reset the option's initial value,we use the cmake command:   
 - For our project   
  ```sh
cmake -D BUID_DOCUMENTATION=ON/OFF
```   
 - GENERALLY:   
```sh
cmake -DOPTION_NAME=NEW_VALUE
```

The base situation is like this :   

doc/CMakeLists.txt file checks for Doxygen and if found, adds a doc target to the build system.
It also generates a doc/Doxyfile in the build folder, which allows cmake to substitute some variables such as version number, project name, source and destination folder etc. 
In your source tree is somewhere a Doxyfile, which you previously used to generate documentation by running doxygen in this directory. Rename this file to ```Doxyfile.in```  
After another CMake run, you can type “make doc” to have CMake run Doxygen. To keep the source tree clean in out-of-source builds, the documentation is generated in the corresponding build directory.   
 - To view the online html online documentation, we use the following command line in the source directory:   
```open html/index.html```   
 - To generate the pdf format of the documentation from the Latek files created, go to the Latex  directory and then use the command line:
  ```sh
    pdflatex   
    pdflatex fileName
    ```


For detailed information about doxygen, please consult [the online doxygen documentation](http://www.stack.nl/~dimitri/doxygen/manual/index.html)



