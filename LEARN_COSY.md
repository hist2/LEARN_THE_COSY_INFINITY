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

# REFERENCES

1.  [An Introduction to Beam Physics.pdf](An Introduction to Beam Physics.pdf) 
2.  [COSY INFINITY v8.1.pdf](COSY INFINITY v8.1.pdf) 
3.  [COSY_INFINITY_version_81_programming_manual.pdf](COSY_INFINITY_version_81_programming_manual.pdf) 
4.  [cosy.fox](cosy.fox) 
