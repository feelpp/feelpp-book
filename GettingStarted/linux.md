Feel++ on Linux
===============
<!-- toc -->

# Debian

Debian is the platform of choice for Feel++, it was developed mainly
on it. The commands to install Feel++ on Debian are

```
  sudo apt-get update
  sudo apt-get install feel++-apps libfeel++-dev feel++-doc
```

The interested user is encouraged to follow the Feel++ PTS page
* Feel++ [Debian Packages Tracking System](http://packages.qa.debian.org/f/feel%2B%2B.html)

At the moment Feel++ compiles and is available on the following Debian
platforms:
* Feel++ [Build results](https://buildd.debian.org/status/package.php?p=feel%2b%2b)

#  Ubuntu
Feel++ has its own PPA, checkout [feelpp ppa for Trusty, Saucy and Precise](https://launchpad.net/~feelpp/+archive/ppa).

The interested user might want to look at the following Ubuntu Launchpad Feel++ page [Ubuntu Source
  Page for all Ubuntu versions](https://launchpad.net/ubuntu/+source/feel++)

## precise Ubuntu Precise - 12.04
This section is outdated
```
	sudo add-apt-repository -y ppa:feelpp/ppa
	sudo add-apt-repository -y ppa:feelpp/petsc
	sudo add-apt-repository -y ppa:mapnik/boost-backports-1-54
	sudo add-apt-repository -y ppa:kalakris/eigen
	sudo apt-get -qq update
	sudo apt-get install -qq libboost1.54-all-dev mpi-default-dev mpi-default-bin libeigen3-dev libpetsc3.4.2-dev libcln-dev petsc-dev libxml2-dev gmsh bison flex doxygen doxygen-latex transfig imagemagick libtbb-dev libann-dev libglpk-dev automake libtool
	sudo apt-get install feel++-apps libfeel++-dev
```


It allows us also to provide a recent version to compile the Feel++ projects on [Travis-ci](https://travis-ci.org/feelpp/feelpp), which is a continuous integration tool.
The installation procedure is currently [as follows](https://github.com/feelpp/feelpp/blob/develop/.travis.yml).

## Ubuntu Trusty - 14.04
<!--
```
	sudo add-apt-repository ppa:feelpp/ppa
	sudo apt-get -qq update
	sudo apt-get install feel++-apps libfeel++-dev
```
-->
### Configuration
First of all, you have to install dependencies
```
 sudo apt-get install git libboost1.55-all-dev petsc-dev libgmsh2 libgmsh-dev paraview gcc-4.9 clang-3.6  libopenmpi1.6 libopenmpi-dev libcln-dev libxml2-dev automake libtool cmake cmake-curses-gui libgoogle-glog-dev 
 ```
 ### Cmake
 Then, in your chosen build directory, you have to run the cmake process.
```sh
cmake /where/is/feelpp/ -DCMAKE_CXX_COMPILER=`which clang++-3.6` -DCMAKE_C_COMPILER=`which clang-3.6` -DFEELPP_MINIMAL_CONFIGURATION=ON -DFEELPP_ENABLE_NLOPT=OFF
```
### Compilation
And at last, the compiling process.
```sh
make
```
You should consider running parallel compilation (`make -j 12` for example).
#### Optional: installation
The one that want Feel++ installed in his system can use `make install`. For more information, we refer to the cmake do