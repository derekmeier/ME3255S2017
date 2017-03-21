# Homework #5
## due 3/28/17 by 11:59pm

*Include all work as either an m-file script, m-file function, or example code included
with \`\`\` and document your code in the README.md file*

1. Create a new github repository called 'linear_algebra'. 

    a. Add rcc02007 and pez16103 as collaborators.

    b. Clone the repository to your computer.

2. Create an LU-decomposition function called `lu_tridiag.m` that takes 3 vectors as inputs
and calculates the LU-decomposition of a tridiagonal matrix. The output should be 3
vectors, the diagonal of the Upper matrix, and the two off-diagonal vectors of the Lower
and Upper matrices. 

    ```[ud,uo,lo]=lu_tridiag(e,f,g);```

3. Use the output from `lu_tridiag.m` to create a forward substitution and
back-substitution function called `solve_tridiag.m` that provides the solution of
Ax=b given the vectors from the output of [ud,uo,lo]=lu_tridiag(e,f,g). *Note: do not use
the backslash solver `\`, create an algebraic solution*

    ```x=solve_tridiag(ud,uo,lo,b);```

4. Test your function on the matrices A3, A4, ..., A10 generated with `test_arrays.m`
Solving for `b=ones(N,1);` where N is the size of A.  In your `README.md` file, compare
the norm of the error between your result and the result of AN\b. 

```
| size of A | norm(error) |
|-----------|-------------|
|  3 | ... |
| 4 | ... |
```

![Spring-mass system for analysis](spring_mass.png)

5. In the system shown above, determine the three differential equations for the position
of masses 1, 2, and 3. Solve for the vibrational modes of the spring-mass system if k1=10
N/m, k2=k3=20 N/m, and k4=10 N/m. The masses are m1=1 kg, m2=2 kg and m3=4 kg. Determine
the eigenvalues and natural frequencies. 

6. The curvature of a slender column subject to an axial load P (Fig. P13.10) can be
modeled by 

$\frac{d^{2}y}{dx^{2}} + p^{2} y = 0$

where $p^{2} = \frac{P}{EI}$

where E = the modulus of elasticity, and I = the moment of inertia of the cross section
about its neutral axis.  

This model can be converted into an eigenvalue problem by
substituting a centered finite-difference approximation for the second derivative to give
$\frac{y_{i+1} -2y_{i} + y_{i-1} }{\Delta x^{2}}+ p^{2} y_{i}$ 

where i = a node located at a position along the rod’s interior, and $\Delta x$ = the
spacing between nodes. This equation can be expressed as $y_{i-1} - (2 - \Delta x^{2}
p^{2} )y_{i}  y_{i+1} = 0$ Writing this equation for a series of interior nodes along the
axis of the column yields a homogeneous system of equations. (See 13.10 for 4
interior-node example)

Determine the eigenvalues for a 5-segment (4-interior nodes), 6-segment (5-interior
nodes), and 10-segment (9-interior nodes). Using the modulus and moment of inertia of a
pole for pole-vaulting (
[http://people.bath.ac.uk/taf21/sports_whole.htm](http://people.bath.ac.uk/taf21/sports_whole.htm))
E=76E9 Pa, I=4E-8 m^4, and L= 5m. 

Include a table in the `README.md` that shows the following results:
What are the largest and smallest eigenvalues for the beam? How many eigenvalues are
there? 

```
| # of segments | largest | smallest | # of eigenvalues |
| --- | --- | --- | --- |
| 5 | ... | ... | ... |
| 6 | ... | ... | ... |
| 10 | ... | ... | ... |
```

If the segment length ($\Delta x$) approaches 0, how many eigenvalues would there be?
