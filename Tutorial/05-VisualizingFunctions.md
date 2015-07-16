Visualizing functions over a mesh {#TutorialVisualize}
======================================



The next step is to visualize function over the mesh. The source code is
available in `myexporter.cpp`

# Loading a Mesh in 2D {#load}

Here, we generate a second order mesh (mesh) and one of first order (meshp1).   
!CODEFILE "code/myexporter.cpp"   



# Constructing a function space {#fs}

here, we generate a second order function space,   
space   
!CODEFILE "code/myexporter.cpp" 

# Defining a (scalar) function over the function space {#scal}   
function   
!CODEFILE "code/myexporter.cpp"   


# Exporter {#exp}

We create now three exporter:
- once generated on the P1 mesh
- once generated on the P2 mesh
- once generated on a P1 mesh extracted from P2 mesh   

exporter   
!CODEFILE "code/myexporter.cpp" 

# Adding function to save {#add}

Here we save the function many times.
That is here not relevant but you may want to simulate process over time.   adding   
!CODEFILE "code/myexporter.cpp"

# Actually saving {#save}   

save   
!CODEFILE "code/myexporter.cpp" 


#  Complete code {#TutorialExprCode}

The complete code reads as follows   

all   
!CODEFILE "code/myexporter.cpp" 

to compile just type
```cpp
make feelpp_tut_myexporter
```
to execute just type
```cpp
./feelpp_tut_myexporter
```


# Reading saved data {#read}

You can visualize data via
- [ensight](https://www.ceisoftware.com/),
- [paraview](www.paraview.org/),
- [gmsh](http://geuz.org/gmsh).

The results files are in \c $HOME/feel/myexporter/np_1 or \c $FEELPP_WORKDIR/feel/myexporter/np_1
