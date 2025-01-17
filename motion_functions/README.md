# Overview:

Cylinder2024 mesh motions are implemented for Python, Fortran, C, and C++ in the files cylinder2024.py, cylinder2024.f90, 
(cylinder2024.c,cylinder2024.h), and (cylinder2024.cpp,cylinder2024.hpp), respectively.


## Approach:

The complex-step method was utilized for computing temporal and spatial derivatives of the prescribed motion 
functions. As such, in some cases you may need to provide inputs as complex types with zero imaginary component.
The complex-step method and perturbations are carried out internally and not required by the user, but the user
does still need to provide inputs as complex-typed variables (except for the C++ interface, which accepts real
inputs).


## Top-level functions/subroutines:


```
coords      
    (in)  -> (alpha,xref,yref,t)     
    (out) -> (x,y)

coords_dot  
    (in)  -> (alpha,xref,yref,t)
    (out) -> (dx_dxref,dx_dyref,dx_dt,dy_dxref,dy_dyref,dy_dt)

Nomenclature:
    alpha     -> time-activation function. Either a function (python), or constant parameter (Fortran, C). See test files for examples.
    xref,yref -> (x,y) coordinate on the undeformed (reference) mesh.
    t         -> time for motion to be evaluated at
    dx_dyref  -> derivative of deformed x-coordinate with respect to undeformed (reference) y-coordinate
    dy_dt     -> derivative of deformed y-coordinate with respect to time.
```




## Python Test

```
python cylinder2024.py
```

## Fortran Test

```
gfortran cylinder2024.f90 F90test.f90
```

## C Test

```
gcc cylinder2024.c Ctest.c
```

## C++ Test

```
g++ -O3 -I. -o CPPtest CPPtest.cpp cylinder2024.cpp
```
