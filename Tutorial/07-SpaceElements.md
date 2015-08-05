Spaces and elements {#TutorialSpaces}
============================
<!-- toc -->

You've learned how to discretize the space you want to compute on.
You now have to learn how to define and use function spaces and elements of functions spaces.

The source code is available in [myfunctionspace.cpp](code/07-myfunctionspace.cpp), with its configuration file [myfunctionspace.cfg](code/07-myfunctionspace.cfg)

# Constructing a function space
- Loading a Mesh in 2D   
  ```c++
   auto mesh = loadMesh(_mesh=new Mesh<Simplex<2>>);
  ```

- For basic function spaces, we have predetermined constructors:   
  ```c++
  auto Xh = Pch<2>( mesh );
  ```    

- Defining an element   
  ```c++
    auto u = Xh->element( "u" );
    auto w = Xh->element( "w" );
  ```
One can also use :
- `Pdh<ORDER>(mesh)` : Polynomial Discontinuous
- `Pvh<ORDER>(mesh)` : Polynomial Continuous Vectorial
- `Pdhv<ORDER>(mesh)` : Polynomial Discontinuous Vectorial
- `Pchm<ORDER>(mesh)` : Polynomial Continuous Matrix
- `Ned1h<ORDER>(mesh)` : Nedelec function spaces   
 
# Code with other features
## Code
!CODEFILE "code/07-myfunctionspace.cpp" 
## Config file
!CODEFILE "code/07-myfunctionspace.cfg" 
