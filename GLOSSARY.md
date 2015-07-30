# rank
MPI local rank of a data structure

# globalRank
MPI global rank of a data structure

# elements

free-function to apply to a mesh to retrieve the iterators over the elements of the mesh stored on the current processor

# markedelements

free-function to apply to a mesh to retrieve the iterators over marked elements (by a string or an integer id) of the mesh stored on the current processor

# boundaryelements

free-function to apply to a mesh to retrieve the iterators over  elements touching the boundary of the mesh stored on the current processor with an face, edge or point.

# faces

free-function to apply to a mesh to retrieve the iterators over the faces of the mesh stored on the current processor

# markedfaces

free-function to apply to a mesh to retrieve the iterators over marked faces (by a string or an integer id) of the mesh stored on the current processor

# boundaryfaces

free-function to apply to a mesh to retrieve the iterators over boundary faces of the mesh stored on the current processor. 
