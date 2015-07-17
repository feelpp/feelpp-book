Spaces and elements {#TutorialSpaces}
============================



You've learned how to discretize the space you want to compute on.
You now have to learn how to define and use function spaces and elements of functions spaces.

The source code is available in `myfunctionspace.cpp`
(The listing is given at the end).

# Loading a Mesh in 2D {#load}

We recall how to load a mesh :   

mesh   
!CODEFILE "code/myfunctionspace.cpp" 


# Constructing a function space {#fs}

For basic function spaces, we have predetermined constructors:   

space   
!CODEFILE "code/myfunctionspace.cpp" 

One can also use :
- `Pdh<ORDER>(mesh)` : Polynomial Discontinuous
- `Pvh<ORDER>(mesh)` : Polynomial Continuous Vectorial
- `Pdhv<ORDER>(mesh)` : Polynomial Discontinuous Vectorial
- `Pchm<ORDER>(mesh)` : Polynomial Continuous Matrix
- `Ned1h<ORDER>(mesh)` : Nedelec function spaces

# Defining an element {#elem}

Elements are basically defined and created like that :    

element   
!CODEFILE "code/myfunctionspace.cpp" 

# Code with other features {#code}   
all   
!CODEFILE "code/myfunctionspace.cpp" 
