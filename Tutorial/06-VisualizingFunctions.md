Visualizing functions over a mesh {#TutorialVisualize}
======================================
<!-- toc -->


The next step is to visualize function over the mesh. The source code that generate our output is
available in [myexporter.cpp](code/05-myexporter.cpp), presented in the previous section. 

# Reading saved data 

You can visualize data via :
- [ensight](https://www.ceisoftware.com/),
- [paraview](www.paraview.org/),
- [gmsh](http://geuz.org/gmsh).

The results files are in 
- `$HOME/feel/myexporter/np_1` or 
- `$FEELPP_WORKDIR/feel/myexporter/np_1`.

We discriminate output directories based on the name of the simulation (the parameter `_name` in 
the environment), the number of process (`mpirun -np ...`) and the type of the chosen exporter
(`--exporter.format={ensight|ensightgold|gmsh|...}`).
