
# Linear Algebra (Review/Introduction)

Representation of linear equations:

1. $5x_{1}+3x_{2} =1$

2. $x_{1}+2x_{2}+3x_{3} =2$

3. $x_{1}+x_{2}+x_{3} =3$

in matrix form:

$\left[ \begin{array}{ccc}
5 & 3 & 0 \\
1 & 2 & 3 \\
1 & 1 & 1 \end{array} \right]
\left[\begin{array}{c} 
x_{1} \\ 
x_{2} \\
x_{3}\end{array}\right]=\left[\begin{array}{c} 
1 \\
2 \\
3\end{array}\right]$

$Ax=b$

### Vectors 

column vector x (length of 3):

$\left[\begin{array}{c} 
x_{1} \\ 
x_{2} \\
x_{3}\end{array}\right]$

row vector y (length of 3):

$\left[\begin{array}{ccc} 
y_{1}~ 
y_{2}~ 
y_{3}\end{array}\right]$

vector of length N:

$\left[\begin{array}{c} 
x_{1} \\ 
x_{2} \\
\vdots  \\
x_{N}\end{array}\right]$

The $i^{th}$ element of x is $x_{i}$


```octave
x=[1:10]
```

    x =
    
        1    2    3    4    5    6    7    8    9   10
    



```octave
x'
```

    ans =
    
        1
        2
        3
        4
        5
        6
        7
        8
        9
       10
    


### Matrices

Matrix A is 3x3:

$A=\left[ \begin{array}{ccc}
5 & 3 & 0 \\
1 & 2 & 3 \\
1 & 1 & 1 \end{array} \right]$

elements in the matrix are denoted $A_{row~column}$, $A_{23}=3$

In general, matrix, B, can be any size, $M \times N$ (M-rows and N-columns):

$B=\left[ \begin{array}{cccc}
B_{11} & B_{12} &...& B_{1N} \\
B_{21} & B_{22} &...& B_{2N} \\
\vdots & \vdots &\ddots& \vdots \\
B_{M1} & B_{M2} &...& B_{MN}\end{array} \right]$


```octave
A=[5,3,0;1,2,3;1,1,1]
```

    A =
    
       5   3   0
       1   2   3
       1   1   1
    


## Multiplication

A column vector is a $1\times N$ matrix and a row vector is a $M\times 1$ matrix

**Multiplying matrices is not commutative**

$A B \neq B A$

Inner dimensions must agree, output is outer dimensions. 

A is $M1 \times N1$ and B is $M2 \times N2$

C=AB

Therefore N1=M2 and C is $M1 \times N2$

If $C'=BA$, then N2=M1 and C is $M2 \times N1$


e.g. 
$A=\left[ \begin{array}{cc}
5 & 3 & 0 \\
1 & 2 & 3  \end{array} \right]$

$B=\left[ \begin{array}{cccc}
1 & 2 & 3 & 4 \\
5 & 6 & 7 & 8 \\
9 & 10 & 11 & 12 \end{array} \right]$

C=AB

$[2\times 4] = [2 \times 3][3 \times 4]$

The rule for multiplying matrices, A and B, is

$C_{ij} = \sum_{k=1}^{n}A_{ik}B_{kj}$

In the previous example, 

$C_{11} = A_{11}B_{11}+A_{12}B_{21}+A_{13}B_{31} = 5*1+3*5+0*9=20$


Multiplication is associative:

$(AB)C = A(BC)$

and distributive:

$A(B+C)=AB+AC$


```octave
A=[5,3,0;1,2,3] 
B=[1,2,3,4;5,6,7,8;9,10,11,12]
```

    A =
    
       5   3   0
       1   2   3
    
    B =
    
        1    2    3    4
        5    6    7    8
        9   10   11   12
    



```octave
C=zeros(2,4)
C(1,1)=A(1,1)*B(1,1)+A(1,2)*B(2,1)+A(1,3)*B(3,1);
C(1,2)=A(1,1)*B(1,2)+A(1,2)*B(2,2)+A(1,3)*B(3,2);

C=A*B
```

    C =
    
       0   0   0   0
       0   0   0   0
    
    C =
    
       20   28   36   44
       38   44   50   56
    



```octave
Cp=B*A
```

    error: operator *: nonconformant arguments (op1 is 3x4, op2 is 2x3)


## Representation of a problem with Matrices and Vectors

If you have a set of known output, $y_{1},~y_{2},~...y_{N}$ and a set of equations that
relate unknown inputs, $x_{1},~x_{2},~...x_{N}$, then these can be written in a vector
matrix format as:

$y=Ax=\left[\begin{array}{c} 
y_{1} \\ 
y_{2} \\
\vdots  \\
y_{N}\end{array}\right]
=
A\left[\begin{array}{c} 
x_{1} \\ 
x_{2} \\
\vdots  \\
x_{N}\end{array}\right]$

$A=
\left[\begin{array}{cccc} 
| & | &  & | \\ 
a_{1} & a_{2} & ... & a_{N} \\ 
| & | &  & | \end{array}\right]$

or 

$y = a_{1}x_{1} + a_{2}x_{2} +...+a_{N}x_{N}$

where each $a_{i}$ is a column vector and $x_{i}$ is a scalar taken from the $i^{th}$
element of x.

Consider the following problem, 4 masses are connected in series to 4 springs with K=10 N/m. What are the final positions of the masses? 

![Springs-masses](mass_springs.svg)

The masses haves the following amounts, 1, 2, 3, and 4 kg for masses 1-4. Using a FBD for each mass:

$m_{1}g+k(x_{2}-x_{1})-kx_{1}=0$

$m_{2}g+k(x_{3}-x_{2})-k(x_{2}-x_{1})=0$

$m_{3}g+k(x_{4}-x_{3})-k(x_{3}-x_{2})=0$

$m_{4}g-k(x_{4}-x_{3})=0$

in matrix form:

$\left[ \begin{array}{cccc}
2k & -k & 0 & 0 \\
-k & 2k & -k & 0 \\
0 & -k & 2k & -k \\
0 & 0 & -k & k \end{array} \right]
\left[ \begin{array}{c}
x_{1} \\
x_{2} \\
x_{3} \\
x_{4} \end{array} \right]=
\left[ \begin{array}{c}
m_{1}g \\
m_{2}g \\
m_{3}g \\
m_{4}g \end{array} \right]$


```octave
k=10; % N/m
m1=1; % kg
m2=2;
m3=3;
m4=4;
g=9.81; % m/s^2
K=[2*k -k 0 0; -k 2*k -k 0; 0 -k 2*k -k; 0 0 -k k]
y=[m1*g;m2*g;m3*g;m4*g]

x=K\y
```

    K =
    
       20  -10    0    0
      -10   20  -10    0
        0  -10   20  -10
        0    0  -10   10
    
    y =
    
        9.8100
       19.6200
       29.4300
       39.2400
    
    x =
    
        9.8100
       18.6390
       25.5060
       29.4300
    


## Matrix Operations

Identity matrix `eye(M,N)` **Assume M=N unless specfied**

$I_{ij} =1$ if $i=j$ 

$I_{ij} =0$ if $i\neq j$ 

AI=A=IA

Diagonal matrix, D, is similar to the identity matrix, but each diagonal element can be any
number

$D_{ij} =d_{i}$ if $i=j$ 

$D_{ij} =0$ if $i\neq j$ 

### Transpose

The transpose of a matrix changes the rows -> columns and columns-> rows

$(A^{T})_{ij} = A_{ji}$

for diagonal matrices, $D^{T}=D$

in general, the transpose has the following qualities:
  
1. $(A^{T})^{T}=A$

2. $(AB)^{T} = B^{T}A^{T}$

3. $(A+B)^{T} = A^{T} +B^{T}$ 

All matrices have a symmetric and antisymmetric part:

$A= 1/2(A+A^{T}) +1/2(A-A^{T})$

If $A=A^{T}$, then A is symmetric, if $A=-A^{T}$, then A is antisymmetric.


```octave
(A*B)'

B'*A' % if this wasnt true, then inner dimensions wouldn;t match

A'*B' == (A*B)'
```

    ans =
    
       20   38
       28   44
       36   50
       44   56
    
    ans =
    
       20   38
       28   44
       36   50
       44   56
    
    error: operator *: nonconformant arguments (op1 is 3x2, op2 is 4x3)


## Square matrix operations

### Trace

The trace of a square matrix is the sum of the diagonal elements

$tr~A=\sum_{i=1}^{N}A_{ii}$

The trace is invariant, meaning that if you change the basis through a rotation, then the
trace remains the same. 

It also has the following properties:

1. $tr~A=tr~A^{T}$

2. $tr~A+tr~B=tr(A+B)$

3. $tr(kA)=k tr~A$

4. $tr(AB)=tr(BA)$


```octave
id_m=eye(3)
trace(id_m)
```

    id_m =
    
    Diagonal Matrix
    
       1   0   0
       0   1   0
       0   0   1
    
    ans =  3


### Inverse

The inverse of a square matrix, $A^{-1}$ is defined such that

$A^{-1}A=I=AA^{-1}$

Not all square matrices have an inverse, they can be *singular* or *non-invertible*

The inverse has the following properties:

1. $(A^{-1})^{-1}=A$

2. $(AB)^{-1}=B^{-1}A^{-1}$

3. $(A^{-1})^{T}=(A^{T})^{-1}$


```octave
A=rand(3,3)
```

    A =
    
       0.5762106   0.3533174   0.7172134
       0.7061664   0.4863733   0.9423436
       0.4255961   0.0016613   0.3561407
    



```octave
Ainv=inv(A)
```

    Ainv =
    
       41.5613  -30.1783   -3.8467
       36.2130  -24.2201   -8.8415
      -49.8356   36.1767    7.4460
    



```octave
B=rand(3,3)
```

    B =
    
       0.524529   0.470856   0.708116
       0.084491   0.730986   0.528292
       0.303545   0.782522   0.389282
    



```octave
inv(A*B)
inv(B)*inv(A)

inv(A')

inv(A)'
```

    ans =
    
      -182.185   125.738    40.598
      -133.512    97.116    17.079
       282.422  -200.333   -46.861
    
    ans =
    
      -182.185   125.738    40.598
      -133.512    97.116    17.079
       282.422  -200.333   -46.861
    
    ans =
    
       41.5613   36.2130  -49.8356
      -30.1783  -24.2201   36.1767
       -3.8467   -8.8415    7.4460
    
    ans =
    
       41.5613   36.2130  -49.8356
      -30.1783  -24.2201   36.1767
       -3.8467   -8.8415    7.4460
    


### Orthogonal Matrices

Vectors are *orthogonal* if $x^{T}$ y=0, and a vector is *normalized* if $||x||_{2}=1$. A
square matrix is *orthogonal* if all its column vectors are orthogonal to each other and
normalized. The column vectors are then called *orthonormal* and the following results

$U^{T}U=I=UU^{T}$

and 

$||Ux||_{2}=||x||_{2}$

### Determinant

The **determinant** of a matrix has 3 properties

1. The determinant of the identity matrix is one, $|I|=1$

2. If you multiply a single row by scalar $t$ then the determinant is $t|A|$:

$t|A|=\left[ \begin{array}{cccc}
tA_{11} & tA_{12} &...& tA_{1N} \\
A_{21} & A_{22} &...& A_{2N} \\
\vdots & \vdots &\ddots& \vdots \\
A_{M1} & A_{M2} &...& A_{MN}\end{array} \right]$

3. If you switch 2 rows, the determinant changes sign:


$-|A|=\left[ \begin{array}{cccc}
A_{21} & A_{22} &...& A_{2N} \\
A_{11} & A_{12} &...& A_{1N} \\
\vdots & \vdots &\ddots& \vdots \\
A_{M1} & A_{M2} &...& A_{MN}\end{array} \right]$

4. inverse of the determinant is the determinant of the inverse:

$|A^{-1}|=\frac{1}{|A|}=|A|^{-1}$

For a $2\times2$ matrix, 

$|A|=\left|\left[ \begin{array}{cc}
A_{11} & A_{12} \\
A_{21} & A_{22} \\
\end{array} \right]\right| = A_{11}A_{22}-A_{21}A_{12}$

For a $3\times3$ matrix,

$|A|=\left|\left[ \begin{array}{ccc}
A_{11} & A_{12} & A_{13} \\
A_{21} & A_{22} & A_{23} \\
A_{31} & A_{32} & A_{33}\end{array} \right]\right|=$

$A_{11}A_{22}A_{33}+A_{12}A_{23}A_{31}+A_{13}A_{21}A_{32}
-A_{31}A_{22}A_{13}-A_{32}A_{23}A_{11}-A_{33}A_{21}A_{12}$

For larger matrices, the determinant is 

$|A|=
\frac{1}{n!}
\sum_{i_{r}}^{N}
\sum_{j_{r}}^{N}
\epsilon_{i_{1}...i_{N}}
\epsilon_{j_{1}...j_{N}}
A_{i_{1}j_{1}}
A_{i_{2}j_{2}}
...
A_{i_{N}j_{N}}$

Where the Levi-Cevita symbol is $\epsilon_{i_{1}i_{2}...i_{N}} = 1$ if it is an even
permutation and $\epsilon_{i_{1}i_{2}...i_{N}} = -1$ if it is an odd permutation and
$\epsilon_{i_{1}i_{2}...i_{N}} = 0$ if $i_{n}=i_{m}$ e.g. $i_{1}=i_{7}$

![Levi-Cevita rule for even and odd permutations for an $N\times N$
determinant](even_odd_perm.svg)

So a $4\times4$ matrix determinant,

$|A|=\left|\left[ \begin{array}{cccc}
A_{11} & A_{12} & A_{13} & A_{14} \\
A_{21} & A_{22} & A_{23} & A_{24} \\
A_{31} & A_{32} & A_{33} & A_{34} \\
A_{41} & A_{42} & A_{43} & A_{44}  \end{array} \right]\right|$

$=\epsilon_{1234}\epsilon_{1234}A_{11}A_{22}A_{33}A_{44}+
\epsilon_{2341}\epsilon_{1234}A_{21}A_{32}A_{43}A_{14}+
\epsilon_{3412}\epsilon_{1234}A_{31}A_{42}A_{13}A_{24}+
\epsilon_{4123}\epsilon_{1234}A_{41}A_{12}A_{23}A_{34}+...
\epsilon_{4321}\epsilon_{4321}A_{44}A_{33}A_{22}A_{11}$

### Special Case for determinants

The determinant of a diagonal matrix $|D|=D_{11}D_{22}D_{33}...D_{NN}$. 

Similarly, if a matrix is upper triangular (so all values of $A_{ij}=0$ when $j<i$), the
determinant is 

$|A|=\left|\left[ \begin{array}{cccc}
A_{11} & A_{12} &...& A_{1N} \\
0 & A_{22} &...& A_{2N} \\
0 & 0 &\ddots & \vdots \\
0 & 0 &...& A_{NN}\end{array} \right]\right|=A_{11}A_{22}A_{33}...A_{NN}$


```octave
D=[1,0,0,0;0,2,0,0;0,0,3,0;0,0,0,4]
A=[1,2,3,4;0,2,3,4;0,0,3,4;0,0,0,4] % upper triangular matrix (4x4)
```

    D =
    
       1   0   0   0
       0   2   0   0
       0   0   3   0
       0   0   0   4
    
    A =
    
       1   2   3   4
       0   2   3   4
       0   0   3   4
       0   0   0   4
    



```octave
det(D)
det(A)
```

    ans =  24
    ans =  24



```octave
A(1,:)=2*A(1,:)
```

    A =
    
       2   4   6   8
       0   2   3   4
       0   0   3   4
       0   0   0   4
    



```octave
det(A)
```

    ans =  48



```octave
det(inv(A))
```

    ans =  0.020833



```octave
1/48
```

    ans =  0.020833



```octave
r1=A(1,:)
r2=A(2,:)
A(1,:)=r2
A(2,:)=r1
```

    r1 =
    
       2   4   6   8
    
    r2 =
    
       0   2   3   4
    
    A =
    
       0   2   3   4
       0   2   3   4
       0   0   3   4
       0   0   0   4
    
    A =
    
       0   2   3   4
       2   4   6   8
       0   0   3   4
       0   0   0   4
    



```octave
det(A)
```

    ans = -48


## Working with matrices (or arrays)

When you need a row of your matrix, use `A(1,:)`

When you need a column of your matrix, use `A(:,1)`


```octave
B=rand(10,8)
```

    B =
    
     Columns 1 through 6:
    
       9.3678e-02   6.6083e-01   8.6163e-01   2.4581e-01   3.2483e-01   6.9693e-01
       4.5401e-01   5.6867e-01   1.4516e-01   9.5440e-02   6.8525e-01   6.1453e-03
       5.4096e-01   9.6443e-01   8.2454e-02   1.8644e-01   7.0369e-01   2.9403e-03
       8.3509e-01   1.1006e-01   5.8880e-01   4.9634e-01   9.3148e-02   8.3110e-01
       5.9499e-01   8.8513e-01   6.5640e-01   5.3244e-01   2.9278e-01   7.6347e-02
       1.5456e-01   3.1275e-01   4.5873e-01   7.2297e-01   3.6996e-01   1.2478e-01
       4.7960e-01   1.8491e-01   6.1816e-01   3.3450e-01   5.9307e-01   8.9796e-01
       9.2872e-01   3.8687e-01   8.3991e-01   8.8064e-01   6.0058e-01   3.5300e-01
       7.3063e-01   2.0543e-01   7.0693e-01   5.0973e-01   7.1647e-01   1.3979e-01
       2.3365e-01   3.5988e-01   4.8453e-01   9.6969e-01   9.8916e-01   2.7608e-02
    
     Columns 7 and 8:
    
       8.8934e-01   1.7184e-01
       2.5948e-03   7.2273e-01
       1.1076e-01   9.3209e-01
       8.3082e-01   3.6414e-01
       9.6406e-01   2.4431e-01
       2.6633e-04   9.9584e-01
       4.4733e-01   4.2158e-01
       1.2252e-01   8.7513e-01
       5.2620e-01   8.7209e-01
       5.8721e-02   9.7262e-01
    



```octave
B(:,3) % print 3 column of matrix B
```

    ans =
    
       0.861626
       0.145156
       0.082454
       0.588799
       0.656403
       0.458729
       0.618158
       0.839911
       0.706933
       0.484532
    



```octave
B(5,:)
```

    ans =
    
     Columns 1 through 7:
    
       0.594987   0.885135   0.656403   0.532440   0.292784   0.076347   0.964064
    
     Column 8:
    
       0.244310
    


How to determine, determinant numerically?
'' , inverse of matrices
'' , solutions , what is x_1, x_2, ...
