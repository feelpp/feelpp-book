##MAKEFILES
Compiling your source code files can be tedious, especially when you want to include several source files and have to type the compiling command everytime you want to do it.Makefiles are special format files that together with the make utility will help you to auto-magically build and manage your projects.

It is recommended to create a new directory and place all the files in there before applying the make commands.

Creating a Makefile

A Makefile typically starts with some variable definitions which are then followed by a set of target entries for building specific targets (typically .o & executable files in C and C++, and .class files in Java) or executing a set of command associated with a target label.

####The basic Makefile

The basic *makefile* is composed of:
```sh
target: dependencies
[tab] system command
```
The following is the generic target entry form :
```sh   
# comment
# (note: the <tab> in the command line is necessary for make to work) 
target:  dependency1 dependency2 ...
      <tab> command

for example:
#
# target entry to build program executable from program and mylib 
# object files 
#
program: program.o mylib.o
	gcc -o program program.o mylib.o
	```

Below is an example of a simple Makefile in c++ from the files named code.cpp,operation.cpp,main.cpp and operation.h for a dummy project(operation) :
```sh
all: operation 
operation: main.o operation.o
	g++ main.o operation.o -o operation 

main.o: main.cpp
	g++ -c main.cpp

operation.o: operation.cpp
	g++ -c operation.cpp


clean:
	rm -rf *.o 
```

####The make utility

######If you run
```sh
   make
```

this program will look for a file named makefile in your directory, and then execute it.

If you have several makefiles, then you can execute them with the command:

```sh
make -f MyMakefile
```

There are several other switches to the make utility. For more info, ``` man make ```.

####Build Process

  1. Compiler takes the source files and outputs object files
  2. Linker takes the object files and creates an executable
  


Visit [GNU make](http://www.gnu.org/software/make/manual/make.html)  for more informations about makefile

