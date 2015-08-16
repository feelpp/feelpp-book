Development FAQ
===============

# How to print values taken by expressions in, say, variational formulations?

Q: I would like to know what the values taken by expressions and sub-expressions in Feel++.

A: There is a `print(expr,"text")` function that can wrap expressions and print their values when the expressions are evaluated.

Here is an example:
```cpp
auto val1 = integrate(_range=elements(mesh),_expr=print(idv(myScalar),"myScalar") );
auto val2 = integrate(_range=markedfaces(mesh,"markerName"),_expr=print(idv(myScalar),"myScalar") );
auto val2 = integrate(_range=markedfaces(mesh,"markerName"),_expr=print(trans(idv(myVector)),"myVectorTrans")*print(idv(myVector),"myVector") );
```

# How to debug testsuite applications?

Q: Feel++ testsuite uses the Boost.Test framework. When used in a debugger and an exception is triggered, the debugger won't catch the exception and provide the backtrace. It is actually Boost.Test that catches all exception which were uncaught which means that the debugger will stop with no backtrace to be displayed. eventually some texts that an exception was thrown is going to be displayed.

A: It suffices to tell the Debugger to catch events before running the Feel++ application. Start the debugger then issue the following command : `catch throw`, then the debugger will stop if an exception is thrown by Feel++ or a third party library and you get a nice backtrace to understand why the exception was thrown.
