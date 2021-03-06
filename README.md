MiniPascal
==========

MiniPascal as a Racket language
-------------------------------

This is the `minipascal' package. It provides MiniPascal
as a new #lang language.

After installation (see later) the following program will run
as is in DrRacket.

    #lang minipascal
    program fib;
    type 
      int=integer;
    function fib(n:int):int;
      begin
        if n=0 then
          fib:=1
        else
          fib:=n*fib(n-1)
      end;
    begin
      writeln(fib(10));
    end.

See `mini-pascal-grammar.rkt` for a complete grammar.

Features
--------

The following features are supported:
  - constant definitions
  - type definitions
  - function and procedure declarations
  - nested functions and procedures
  - base types: integer, boolean, char,
  - arrays 
  - strings (in the for of arrays of char)
  - integer and char can be used as index ranges

Compilers
---------
  
MiniPascal comes with two compilers. The simple one
in "semantics-simple.rkt" translates directly from
Pascal to Racket without any (compile time) type 
checking. This compiler is written in the same
spirit as the example in the Ragg tutorial. In
other words it "compiles by macro expansion".

The other compiler in "semantics.rkt" demonstrates
how scoping and type checking can by implemented. 
The compiler more traditional, it expands the whole 
Pascal program in one go.

To switch from the full compiler to the simple one,
add 'simple' to the #lang line. That is, the lines:
    #lang minipascal
    #lang minipascal simple
use the full and simple compiler respectively.

Exercises
---------
  - Add mod as an operator
  - Add repeat
  - Add case
  - Add enumerated types  
  - Add real numbers
  - Add records
  - Add files
  
Installation
------------

Install this package with:

    raco pkg install minipascal

or, by evaluating:

    #lang racket
    (require planet2)
    (install "minipascal")

Use the Racket package manager to install:

 raco pkg install minipascal

References
----------
Pascal ISO 7185 from 1990:
http://pascal-central.com/docs/iso7185.pdf
