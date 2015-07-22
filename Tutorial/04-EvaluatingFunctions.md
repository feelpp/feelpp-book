Using function {#TutorialFunctions}
=====================



Once you  have created an element, you may want to give it a value, that can depends on a lot of parameters (mainly spaces, but others may apply).

To do so, Feel++ relies on expression.
We may use tree kind of expression :

- [Parsed](#parsed)
- [Build-in](#build)
- [Hard coded](#hc)


# Parsed {#parsed}

Thanks to [GiNaC](http://www.ginac.de), we can parse expression like that :
```sh
./feelpp_myexpression --functions.f="2*x*y+cos(x+y):x:y"
```

Step by step explanations
------------

- We start by loading a Mesh in 2D


- then we define some expression through the command line or config file: `g`  is a scalar field and `f`  is a vector field   
  


   here is an example how to enter them:   
   ```./feelpp_tut_myexpression --a=3 --functions.g="a*x*y:x:y:a"               --functions.f="{sin(pi*x),cos(pi*y)}:x:y" ```   
   Note that you can print back the expression to the screen to check that    everything is ok.   
   If you want to use as expression `a*x+b*y`, you have to define `a` and     `b` as option (either in your code, either in the library).

- then we compute the gradient of `g`  and `f`.   
  Notice that template argument are given to `grad`  to specify the shape    of  the
  gradient: in the case of $$\nabla g$$ it is $$1\times2$$ and  $$2\times    2$$ for $$\nabla f$$ since we are in 2D.
- then we compute the laplacian of `g`  and `f`   
- then we compute the divergence of `f`   
- and the curl of `f`   


Finally we evaluate these expression at one point given by the option `x`  and `y`   
 
!CODEFILE "code/myexpression.cpp"   


# Built-in {#build}

Instead of defining an expression from a string, you can use

!CODEFILE "code/myexporter.cpp"

The list of the Feel++ Keyword is [here](../QuickReference/Keywords.md).

# Hard Coded {#hc}

One other method to define function is described here.

!CODEFILE "code/myfunctor.cpp"
