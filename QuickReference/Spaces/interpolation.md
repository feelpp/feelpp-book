Interpolation
=============

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