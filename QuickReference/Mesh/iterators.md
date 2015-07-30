# Mesh iterators

|Feel++ Keyword|Description|
|---|---|
|elements(mesh)|All the elements of a mesh|
|markedelements(mesh, id)|The precise element defined by the id.<br>It can be any element (line, surface, domain, and so on).|
| faces(mesh) |All the faces of the mesh.|
| markedfaces(mesh) |All the faces of the mesh which are marked.|
| boundaryfaces(mesh) |All elements that own a topological dimension one below the mesh. <br>For example, if you mesh is a 2D one, `boundaryfaces(mesh)`  will return all the lines (because of dimension $$2-1=1$$).<br>These elements which have one dimension less, are corresponding to the boundary faces.|
| internalelements(mesh) |All the elements of the mesh which are stricly within the domain that is to say they do not share a face with the boundary.|
| boundaryelements(mesh) |All the elements of the mesh which share a face with the boundary of the mesh.|
| edges(mesh) | All the edges of the mesh.|
| boundaryedges(mesh) |All boundary edges of the mesh.|
