# Mean value of a function {#mean}

Let $$f$$ a bounded function on domain $$\Omega$$. You can evaluate the mean value of a function thanks to the mean() function :
<center>
$$ \bar{f}=\frac{1}{|\Omega|}\int_\Omega f=\frac{1}{\int_\Omega 1}\int_\Omega f $$
</center>


**Interface***
```cpp
  mean( _range, _expr, _quad, _geomap );
```

Required parameters:
* `_range` = domain of integration
* `_expr` = mesurable function

Optional parameters:
* `_quad` = quadrature to use. Default = \lstinline!_Q<integer>()!
* `_geomap` = type of geometric mapping. Default = `GEOMAP_OPT`

*Example*
From `doc/manual/stokes/stokes.cpp`
!CODEFILE "code/stokes.cpp" mean
