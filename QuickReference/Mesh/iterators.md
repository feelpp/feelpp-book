# Mesh iterators {#iterators}

The following table describes free-functions that allow to define mesh region over which to operate. MeshType denote the type of mesh passed to the free functions in the table.

> **Note** MeshType can be a pointer, a shared_pointer or a reference to a mesh type. for example
```cpp
auto mesh = loadMesh( _mesh=Mesh<Simplex<2>>);
auto r1 = elements(mesh); // OK
auto r2 = elements(*mesh); // OK
```


|Type|Function|Description|
|----|---|---|
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


Feel++ allows also to select an extended sets of entities from the mesh, you can extract entities which belongs to the local process but also ghost entities which satisfy the same property as the local ones. Actually you can select both or one one of them thanks to the enum data structure entity_process_t which provides the following options

| entity_process_t | Description |
|------------------|-------------|
| LOCAL_ONLY | only local entities |
| GHOST_ONLY | only ghost entities |
| ALL | both local and ghost entities |

|Type|Function|Description|
|----|--------|-----------|
|ext_elements_t\<MeshType\>|elements(mesh,entity_process_t)|all the elements of mesh associated to entity_process_t.|
|ext_elements_t\<MeshType\>|markedelements(mesh, id, entity_process_t)|all the elements marked id of mesh associated to entity_process_t.|
|ext_faces_t\<MeshType\>|faces(mesh,entity_process_t)|all the faces of mesh associated to entity_process_t.|
|ext_faces_t\<MeshType\>|markedfaces(mesh, id, entity_process_t)|all the faces marked id of mesh associated to entity_process_t.|
|ext_edges_t\<MeshType\>|edges(mesh,entity_process_t)|all the edges of mesh associated to entity_process_t.|
|ext_edges_t\<MeshType\>|markededges(mesh, id, entity_process_t)|all the edges marked id of mesh associated to entity_process_t.|

> **Note** the type of the object returned for an entity is always the same, for elements it is ext_elements_t\<MeshType\> whether the elements are marked or not. The reason is that in fact we have to create a temporary data structure embedded in the range object that stores a reference to the elements which are selected.
