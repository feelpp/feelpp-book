# Algebra Backends {#backends}

Non-/Linear algebra backends are crucial components of Feel++. They provide a uniform interface between Feel++ data structures and underlying the linear algebra libraries used by Feel++.

## Libraries 

Feel++ interfaces the following libraries:
 - PETSc : Portable, Extensible Toolkit for
Scientific Computation
 - SLEPc : Eigen value solver framework based on PETSc
 - Eigen3

## Backend

Backend is a template class parametrized by the numerical type providing access to
 - vector
 - matrix : dense and sparse
 - algorithms : solvers, preconditioners, ...

PETSc provides sequential and parallel data structures
whereas Eigen3 is only sequential.

To create a Backend, use the free function `backend` which has the following interface:
```cpp
backend(_name="name_of_backend", 
        _rebuild=true|false,
        )
```
