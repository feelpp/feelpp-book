# Mesh iterators {#iterators}

The following table describes free-functions that allow to define mesh region over which to operate. `MeshType` denote the type of `mesh` passed to the free functions in the table.

> **Note** `MeshType` can be a pointer, a shared_pointer or a reference to a mesh type. for example
```cpp
auto mesh = loadMesh( _mesh=Mesh<Simplex<2>>);
auto r1 = elements(mesh); // OK
auto r2 = elements(*mesh); // OK
```


|Type|Function|Description|
|---|---|
|elements_t\<MeshType\>|elements(mesh)|All the elements of a mesh|
|markedelements_t\<MeshType\>|markedelements(mesh, id)|All the elements marked by marked id |
| boundaryelements_t\<MeshType\>| boundaryelements(mesh) |All the elements of the mesh which share a face with the boundary of the mesh.|
| internalelements_t\<MeshType\>| internalelements(mesh) |All the elements of the mesh which share a face with the boundary of the mesh.|
|pid_faces_t\<MeshType\>| faces(mesh) |All the faces of the mesh.|
|markedfaces_t\<MeshType\>| markedfaces(mesh) |All the faces of the mesh which are marked.|
|boundaryfaces_t\<MeshType\>| boundaryfaces(mesh) |All elements that own a topological dimension one below the mesh. <br>For example, if you mesh is a 2D one, `boundaryfaces(mesh)`  will return all the lines (because of dimension $$2-1=1$$).<br>These elements which have one dimension less, are corresponding to the boundary faces.|
|internalfaces_t\<MeshType\>| internalelements(mesh) |All the elements of the mesh which are stricly within the domain that is to say they do not share a face with the boundary.|
| edges_t\<MeshType\>| edges(mesh) | All the edges of the mesh.|
| boundaryedges_t\<MeshType\> | boundaryedges(mesh) |All boundary edges of the mesh.|
