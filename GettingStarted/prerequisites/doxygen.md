##DOXYGEN
Doxygen is a tool for auto-generating API documentation, though you can also use it to generate documentation separate from an API.It can generate documentation from annotated C++ sources, but it also supports other popular programming languages such as C, Objective-C, C#, PHP, Java, Python, IDL (Corba, Microsoft, and UNO/OpenOffice flavors), Fortran, VHDL, Tcl, and to some extent D.The main advantage of Doxygen is that you can write documentation directly within the comments of your source code. Doxygen searches for source code in your tree and generates API documentation for it.   
  - It can generate an on-line documentation browser (in HTML) and/or an off-line reference manual in LaTeX  from a set of documented source files. There is also support for generating output in RTF (MS-Word), PostScript, hyperlinked PDF, compressed HTML, and Unix man pages. The documentation is extracted directly from the sources, which makes it much easier to keep the documentation consistent with the source code.   
  - You can configure doxygen to extract the code structure from undocumented source files. This is very useful to quickly find your way in large source distributions.Doxygen can also visualize the relations between the various elements by means of include dependency graphs, inheritance diagrams, and collaboration diagrams, which are all generated automatically.   
  - You can also use doxygen for creating normal documentation.

***NOTE*** : 

Doxygen is developed under Mac OS X and Linux, but is set-up to be highly portable. As a result, it runs on most other Unix flavors as well. Furthermore, executables for Windows are available.For more informations about downloading and installing Doxygen, click [here](http://www.stack.nl/~dimitri/doxygen/manual/install.html)

**So, what's the value to Doxygen?**

Some of Doxygen's output is extracted from the semantics of the source programs. Other parts are from special comments you embed in your code. The entire process requires a special configuration file that specifies exactly what you want to do. Just as your development directory usually has a *makefile* that controls the build process, you also have a *Doxyfile* that contains the options used by Doxygen. This is simply a free-form text file that has options variables and their values. Doxygen automatically generates an example Doxyfile for you on request.

The source comments can use any of three formats:   
 1. Special comments can mimic a Javadoc comment by using an extra asterisk in a multiline comment
 
 ```(/** A special comment */)```.
 - You can also use an exclamation point instead of the second asterisk 
  
 ``` (/*! Another special comment */)```.
 - Two or more single line comments ```(//)``` that have at least one extra slash or exclamation point following the comment marker also form a special comment.
 
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

We can configure our cmake system to enable Doxygen to automatically generate an API documentation when we run ```make```.    
To generate a documentation for our simple [dummy mini project](https://github.com/wkyoshe/stageM1/tree/master/src),we have to add to our CMakeLists.txt the following:

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
To generate the documentation, we have to set the   
```option(BUID_DOCUMENTATION = ON)``` and ```OFF```  if we don't desire a documentation.

*NOTE* : To reset the option initial value,use the cmake command:    
For our ummy mini project
```sh
cmake -DBUID_DOCUMENTATION=ON/OFF
```

GENERALLY:
```sh

cmake -DOPTION_NAME=NEW_VALUE
```

For detailed information about doxygen, please consult [the online doxygen documentation](http://www.stack.nl/~dimitri/doxygen/manual/index.html)




