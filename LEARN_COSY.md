# LEARN THE COSY INFINITY

[TOC]



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

## VARIABLE

VARIABLE < name > < expression > { < expression > } ;

Arguments :

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

# REFERENCES

1.  [An Introduction to Beam Physics.pdf](An Introduction to Beam Physics.pdf) 
2.  [COSY INFINITY v8.1.pdf](COSY INFINITY v8.1.pdf) 
3.  [COSY_INFINITY_version_81_programming_manual.pdf](COSY_INFINITY_version_81_programming_manual.pdf) 
4.  [cosy.fox](cosy.fox) 
