##MAKEFILES

**Compiling by hand :**   
The trivial way to compile our files and obtain an executable, is by running the command:
```sh
g++ main.cpp
g++ operation.cpp 
```   
Or simply

```sh
g++ main.cpp operation.cpp  -o operation
```

Compiling our source code files can be tedious, especially when you want to include several source files and have to type the compiling command everytime you want to do it.
Makefiles are special format files that together with the make utility will help you to auto-magically build and manage your projects.

It is recommended (actually mandatory for Feel++) to separate source code and build directory.
###Creating a Makefile
A Makefile typically starts with some variable definitions which are then followed by a set of target entries for building specific targets (typically .o for executable files in C and C++, and .class files in Java) or executing a set of command associated with a target label.

####The basic Makefile

The basic *makefile* is composed of:
```makefile
target: dependencies
[tab] system command
```

Here is a simple makefile to compile our files from our simple project.
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
The ```make ```
command will look for a file named `Makefile` in the current directory, and execute the `main` target.

If you have several makefiles, then you can execute them with the command:   
```sh 
make -f MyMakefile
```

There are several other switches to the make utility. For more info, ``` man make ```.


Visit [GNU make](http://www.gnu.org/software/make/manual/make.html) for more informations about makefile

