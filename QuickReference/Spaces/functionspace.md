Function Spaces
===============

Function spaces support is provided by the `FunctionSpace` class

The `FunctionSpace`  class

 -  constructs the table of degrees of freedom which maps local (elementwise) degrees of
  freedom to the global ones with respect to the geometrical entities,
 -  embeds the definition of the elements of the function space allowing for a
  tight coupling between the elements and their function spaces,
 -  stores an interpolation data structure (\eg region tree) for rapid
  localisation of point sets (determining in which element they reside).

|Function         | C++ Type | Function Space |
|-----------------|------|----------------|
|`Pch<N>(mesh)`   | `Pch_type<MeshType,N>`  | $$P^N_{c,h}$$ |
|`Pchv<N>(mesh)`  | `Pchv_type<MeshType,N>` | $$[P^N_{c,h}]^d$$|
|`Pdh<N>(mesh)`   | `Pdh_type<MeshType,N>`  | $$P^N_{d,h}$$ |
|`Pdhv<N>(mesh)`  | `Pdhv_type<MeshType,N>` | $$[P^N_{d,h}]^d$$|
|`THch<N>(mesh)`  | `THch_type<MeshType,N>` | $$[P^{N+1}_{c,h}]^d \times P^N_{c,h}$$|
|`Dh<N>(mesh)`    | `Dh_type<MeshType,N>`   | $$\mathbb{R}\mathbb{T}_h$$|
|`Ned1h<N>(mesh)` | `Ned1h_type<MeshType,N>`| $$\mathbb{N}_h$$|

Here are some examples how to define function spaces with Lagrange basis functions.
```cpp
// Mesh with triangles
using MeshType = Mesh<Simplex<2>>;
// Space spanned by P_3 Lagrange finite element
FunctionSpace<MeshType,bases<Lagrange<3>>> Xh;
// is equivalent to (they are the same type)
Pch_type<MeshType,3> Xh;

// using the auto keyword
MeshType mesh = loadMesh( _mesh=new MeshType );
auto Xh = Pch<3>( mesh );
// is equivalent to 
auto Xh = FunctionSpace<MeshType,bases<Lagrange<3>>>::New( mesh );
auto Xh = Pch_type<MeshType,3>::New( mesh );
```


The most important feature in `FunctionSpace`  is that it embeds the
definition of element which allows for the strict definition of an
`Element` of a `FunctionSpace`  and thus ensures the correctness of the
code.  An element has its representation as a vector - also in the
case of product of multiple spaces. - The vector representation is
parametrized by one of the linear algebra backends. Other supported
operations are interpolation and extraction of components - be it a
product of function spaces element or a vectorial/matricial element:

```cpp
FunctionSpace<Mesh<Simplex<2> >,
  bases<Lagrange<3,Scalar, Continuous> > > P3ch;
// get an element from P3ch
auto u = P3ch.element();
FunctionSpace<Mesh<Simplex<2> >,
 bases<Lagrange<2,Vectorial>, Lagrange<1,Scalar>,
       Lagrange<1,Scalar> > > P2P1P1;
auto U = P2P1P1.element();
// Views: changing a view changes U and vice versa
// view on element associated to P2
auto u = U.element<0>();
// extract view of first component
auto ux = u.comp(X);
// view on element associated to 1st P1
auto p = U.element<1>();
// view on element associated to 2nd P1
auto q = U.element<2>();
```

Finally Feel++ provides the Lagrange, $$\mathcal{I}_c^{\mathrm{lag}}, \mathcal{I}_d^{\mathrm{lag}}$$, Crouzeix-Raviart, $$\mathcal{I}^{\mathrm{cr}}$$,
Raviart-Thomas, $$\mathcal{I}^{\mathrm{RT}}$$ and N&eacute;d&eacute;lec, $$\mathcal{I}^{\mathrm{N}}$$ global interpolation operators.
In abstract form, they read
$$
  \mathcal{I} : \mathbb{X} \ni v \mapsto \sum_{i=1}^{\mathrm{dim}\mathbb{X}} \ell_i(v) \phi_i
$$
where $$\mathbb{X}$$ is the infinite dimensional space, $$(\ell_i)_{i=1,...,\mathrm{dim}\mathbb{X}}$$ are
the linear forms and $$(\phi_i)_{i=1...\mathrm{dim}\mathbb{X}}$$ the basis function associated
with the various approximations.

# Function Space helper functions

