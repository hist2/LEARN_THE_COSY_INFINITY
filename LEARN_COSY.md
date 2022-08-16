# LEARN THE COSY INFINITY

[TOC]

## OV

OV < order > < phase space dimension > < number of parameters > ;

This is the first command that sets up the DA tools and has to be called before any DA operations, including the computation of maps, can be executed.

PARAMETERS:

1. maximum order that is to occur
2. dimensionality of phase space (1, 2 or 3)
3. number of system parameters that are requested
   The number of ( system ) parameters is the number of additional quantities besides the phase space variables that he final map shall depend on.

The number of the EXPONENTS:


$$
\text{number of the exponents} =
\begin{cases}
3 \text{, (phase space dimension = 1,number of parameters = 0)}\\
3 \text{, (1,1)}\\
4 \text{, (1,2)}\\
5 \text{, (1,3)}\\
2*\text{phase space dimension}+\text{number of parameters}, \text{(phase space dimension,number of parameters)}
\end{cases}
$$




EXAMPLE:

```fortran
INCLUDE 'COSY' ;

PROCEDURE RUN ;

    VARIABLE D 100 ;

    OV 7 3 2 ;

    D := DA(1)*DA(1)*DA(2)*DA(3)*DA(4)+EXP(DA(4))*DA(5)*DA(6) ;

    OPENF 1 'NoE.txt' 'UNKNOWN' ;   {NoE: Number of Exponents}
    
    write 1 D ;
    
    CLOSEF 1 ;

ENDPROCEDURE ;
RUN ;
END ;
```

The result (NoE.txt) is 

```txt
 I  COEFFICIENT            ORDER EXPONENTS
 1   1.000000000000000       2   0 0  0 0  1 1  0 0
 2   1.000000000000000       3   0 0  0 1  1 1  0 0
 3  0.5000000000000000       4   0 0  0 2  1 1  0 0
 4   1.000000000000000       5   2 1  1 1  0 0  0 0
 5  0.1666666666666667       5   0 0  0 3  1 1  0 0
 6  0.4166666666666666E-01   6   0 0  0 4  1 1  0 0
 7  0.8333333333333333E-02   7   0 0  0 5  1 1  0 0
 --------------------------------------------------
```

## ME

ME(< phase space variable >,< element identifier >)

ME is the abbreviation of Map Element.

> It is also possible to extract individual matrix elements of transfer maps. This is achieved with the COSY function ME (<phase space variable>,<element identifier>).
> The element identifier  follows TRANSPORT notation; for example, ME(1,122) returns the momentary value of the matrix element (x,xaa).

## OPENF & CLOSEF

- Procedure OPENF ( 3 arguments ) opens a file. Parameters are unit number, filename ( string ), and status (string, same as in FORTRAN open).
- Procedure CLOSEF ( 1 argument )  close a file. Parameter is unit number.

```fortran
OPENF 1 'test.txt' 'UNKNOWN' ;
	PM 1 ;
	WM 1 ;
	WRITE 1 'Test Information' ;
	CLOSEF 1 ;
```

The status in FORTRAN is "NEW", "OLD" and "UNKNOWN". If you want to add information in the same file, do not close the file before the command of adding information.

The result of this example will be a file, whose name is 'test.txt', and the context of the file will be momentary and the 'Test Information'.

## VARIABLE

VARIABLE < name > < expression > { < expression > } ;

PARAMETERS:

1. name denotes the identifier of the variable to be declared.

2. The next expression contains the amount of memory that has to be allocated when the variable is used.

   | Type                              | Length                             | Notes           |
   | --------------------------------- | ---------------------------------- | --------------- |
   | a real or double precision number | 1                                  |                 |
   | a complex double precision number | 2                                  |                 |
   | a DA vector                       | at least the number of derivatives | **NMON**($n,v$) |
   | a CD vector                       | twice of DA vector                 |                 |

   The maximum number of detivatives through $n$th order in v variables can be obtained using the function **NMON**($n,v$)

3. If the variable is to be used with indices as an array, the next expressions have to be specify the different dimensions.
   And curly brackets denotest that the expression in them can be repeated.

EXAMPLE:

```fortran
VARIABLE X 100 5 7 ;
```

This declares X to be a two dimensional array with 5 respectively 7 entries, each of which has room for 100 memory loactions.

Note that during allocation, the type and value of the variable is set to the real and zero.

## Data Types & Operations on them

There are many types of data, which are **Real number**, **Strings**, **Logicals**, **Complex Numbers**, **Intervals**, **Vectors**, **DA vectors** and **Taylor model, RDA Objects**.

### DA or Taylor polynomials





# REFERENCES

1.  [An Introduction to Beam Physics.pdf](An Introduction to Beam Physics.pdf) 
2.  [COSY INFINITY v8.1.pdf](COSY INFINITY v8.1.pdf) 
3.  [COSY_INFINITY_version_81_programming_manual.pdf](COSY_INFINITY_version_81_programming_manual.pdf) 
4.  [cosy.fox](cosy.fox) 
