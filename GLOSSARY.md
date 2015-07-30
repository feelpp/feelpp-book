# rank
MPI local rank of a data structure

# globalRank
MPI global rank of a data structure

# marker
Marker for mesh element, faces, edges or point. Element marker are often associated to material properties

# marker2
Marker for mesh element, faces, edges or point. It is used for example to iterate over element thanks to a particular piecewise constant field

# marker3
Marker for mesh element, faces, edges or point. It is used for example to iterate over element thanks to a particular piecewise constant field

# elements

free-function to apply to a mesh to retrieve the iterators over the elements of the mesh stored on the current processor

# markedelements

free-function to apply to a mesh to retrieve the iterators over marked elements (by a string or an integer id) of the mesh stored on the current processor

# marked2elements

free-function to apply to a mesh to retrieve the iterators over marked elements (by a string or an integer id) with marker2 of the mesh stored on the current processor

# marked3elements

free-function to apply to a mesh to retrieve the iterators over marked elements (by a string or an integer id) with marker3 of the mesh stored on the current processor

# boundaryelements

free-function to apply to a mesh to retrieve the iterators over  elements touching the boundary of the mesh stored on the current processor with an face, edge or point.

# internalelements

free-function to apply to a mesh to retrieve the iterators over  elements which are not touching with a point, edge or face the boundary of the mesh stored on the current processor

# edges

free-function to apply to a mesh to retrieve the iterators over the edges of the mesh stored on the current processor

# markededges

free-function to apply to a mesh to retrieve the iterators over marked edges (by a string or an integer id) of the mesh stored on the current processor

# faces

free-function to apply to a mesh to retrieve the iterators over the faces of the mesh stored on the current processor

# markedfaces

free-function to apply to a mesh to retrieve the iterators over marked faces (by a string or an integer id) of the mesh stored on the current processor

# boundaryfaces

Free-function to apply to a mesh to retrieve the iterators over boundary faces of the mesh stored on the current processor.

# integrate

Free-function to define integral expressions entering the definition of integrals, linear and bi-linear forms.

# project()
Free-function to project an expression over a nodal function space 