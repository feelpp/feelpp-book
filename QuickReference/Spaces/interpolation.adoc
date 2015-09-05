Interpolation
=============

Feel++ has a very powerful interpolation framework which allows to seamlessly in parallel:
 - transfer functions from one mesh to another
 - transfer functions from one space type to another.

The framework provides a set of C++ classes and C++ free-functions enabled  short, concise and expressive handling of interpolation.

# De Rahm Diagram

$$
    \begin{array}{ccccccccccc}
      \mathbb{R}& 
      \overset{id}{\longrightarrow}&
      H_1(\Omega)&
      \overset{\nabla}{\longrightarrow}&
      H_{\mathrm{curl}}(\Omega)&
      \overset{curl}{\longrightarrow}&
      H_{\mathrm{div}}(\Omega)&
      \overset{div}{\longrightarrow}&
      L_2(\Omega)&
      \overset{0}{\longrightarrow} \{0\} \\
      ~ &
      ~ & 
      \left\downarrow\rule{0cm}{0.3cm}\right.\pi_h&
      \cdot & 
      \left\downarrow\rule{0cm}{0.3cm}\right.\pi_h&
      ~ &
      \left\downarrow\rule{0cm}{0.3cm}\right.\pi_h&
      ~ &
      \left\downarrow\rule{0cm}{0.3cm}\right.\pi_h&
      ~ &
      ~ \\
      \mathbb{R}& 
      \overset{id}{\longrightarrow}&
      U_h&
      \overset{\nabla}{\longrightarrow}&
      V_h&
      \overset{curl}{\longrightarrow}&
      W_h&
      \overset{div}{\longrightarrow}&
      Z_h&
      \overset{0}{\longrightarrow} \{0\} \\
    \end{array}
    $$