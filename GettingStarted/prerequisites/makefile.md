##MAKEFILES

**Compiling by hand :**   
The trivial way to compile our files and obtain an executable, is by running the command:

```sh
g++ main.cpp operation.cpp  -o operation
```
To simplify compiling of several source files, Makefiles are special format files that together with the make utility will help you to auto-magically build and manage your projects.

It is recommended (actually mandatory for Feel++) to separate source code and build directory.
###Creating a Makefile
A  *Makefile* is composed of :
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

