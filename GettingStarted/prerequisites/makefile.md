##MAKEFILES

**Compiling by hand :**   
The trivial way to compile our files and obtain an executable, is by running the command:
```sh
g++ main.cpp
g++ operation.cpp
g++ operation.h
```   
Or simply

```sh
g++ main.cpp operation.cpp opertation.h  -o operation
```

Compiling our source code files can be tedious, especially when you want to include several source files and have to type the compiling command everytime you want to do it.
Makefiles are special format files that together with the make utility will help you to auto-magically build and manage your projects.

It is recommended (actually mandatory for Feel++) to separate source code and build directory.
###Creating a Makefile
A Makefile typically starts with some variable definitions which are then followed by a set of target entries for building specific targets (typically .o & executable files in C and C++, and .class files in Java) or executing a set of command associated with a target label.

####The basic Makefile

The basic *makefile* is composed of:
```makefile
target: dependencies
[tab] system command
```
The following is the generic target entry form :
```makefile
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

Below is an example of a simple Makefile in c++ for files named operation.cpp,main.cpp and operation.h of a dummy mini project (operation) :(click [here](https://github.com/wkyoshe/stageM1/tree/master/src)  to see the dummy mini project source codes)
```makefile
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
The `make` command will look for a file named `Makefile` in the current directory, and execute the `main` target.

If you have several makefiles, then you can execute them with the command: `make -f MyMakefile`

There are several other switches to the make utility. For more info, ``` man make ```.

####Build Process

  1. Compiler takes the source files and outputs object files
  2. Linker takes the object files and creates an executable
  

Visit [GNU make](http://www.gnu.org/software/make/manual/make.html) for more informations about makefile

