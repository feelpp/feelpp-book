Development FAQ
===============

# How to print from expressions?

Q: I would like to know what the values taken by expressions and sub-expressions in Feel++.

A: There is a `print(expr,"text")` function that can wrap expressions and print their values when the expressions are evaluated.

```cpp
auto val1 = integrate(_range=elements(mesh),_expr=print(idv(myScalar),"myScalar") );
auto val2 = integrate(_range=markedfaces(mesh,"markerName"),_expr=print(idv(myScalar),"myScalar") );
auto val2 = integrate(_range=markedfaces(mesh,"markerName"),_expr=print(trans(idv(myVector)),"myVectorTrans")*print(idv(myVector),"myVector") );
```

# 
