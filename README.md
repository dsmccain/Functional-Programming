# Functional Programming in Haskell by Examples

[Papers](papers/README.md)

<!--
@TODO: Add the creative commons public domain logo.
@TODO: Update papers repository
-->

![](images/haskellLogo.png)

The purpose of this tutorial is to illustrate functional programming concepts in the Haskell programming language by providing reusable and useful snippets of code, examples, case studies, and applications.

* Full  URL: https://github.com/caiorss/Functional-Programming
* Short URL: http://tinyurl.com/fpbyexample

Notes: 

* The code snippets with the '>' symbol were run in the interactive Haskell Shell (GHCi) and the lines below without the '>' symbol are the output.


<!-- # HASKELL BY EXAMPLE / PRACTICAL FUNCTIONAL PROGRAMMING -->

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Haskell](#haskell)
  - [Suffixes of file names for Haskell](#suffixes-of-file-names-for-haskell)
  - [Toolset](#toolset)
  - [Install Haskell Platform](#install-haskell-platform)
  - [GHCI Reference](#ghci-reference)
- [Functional Programming Concepts](#functional-programming-concepts)
  - [Overview](#overview)
  - [Functional Programming Languages](#functional-programming-languages)
  - [Pure Functions](#pure-functions)
  - [Lazy Evaluation](#lazy-evaluation)
- [Basic Syntax](#basic-syntax)
  - [Operators](#operators)
    - [Logic Operators](#logic-operators)
    - [Powers](#powers)
    - [Application Operator - $](#application-operator---$)
    - [Misc. Operators](#misc-operators)
  - [Defining Values and Types](#defining-values-and-types)
  - [Type System](#type-system)
    - [Basic Types](#basic-types)
    - [Basic Type Classes](#basic-type-classes)
    - [Standard Haskell Types](#standard-haskell-types)
    - [Standard Haskell Classes](#standard-haskell-classes)
    - [Numeric Types Conversion](#numeric-types-conversion)
    - [Haskell-Style Syntax for types:](#haskell-style-syntax-for-types)
  - [Lists](#lists)
    - [Creating Lists](#creating-lists)
    - [List Operations](#list-operations)
    - [Chekings Lists](#chekings-lists)
- [Functions](#functions)
  - [Creating functions](#creating-functions)
  - [Anonymous Functions or Lambda Functions](#anonymous-functions-or-lambda-functions)
  - [Infix Functions](#infix-functions)
  - [Infix Operators as Functions](#infix-operators-as-functions)
  - [Currying](#currying)
  - [Function Composition / Composition Operator](#function-composition--composition-operator)
  - [The $ apply operator.](#the-$-apply-operator)
  - [Recursion](#recursion)
  - [Integer Arithmetic Functions](#integer-arithmetic-functions)
  - [Mathematical Functions](#mathematical-functions)
  - [Standard Functions](#standard-functions)
  - [Higher Order Functions](#higher-order-functions)
    - [Map](#map)
    - [Filter](#filter)
    - [Higher-order predicates](#higher-order-predicates)
    - [Fold](#fold)
    - [Scanl](#scanl)
    - [Curry and Uncurrying](#curry-and-uncurrying)
    - [Flip](#flip)
    - [Iterate](#iterate)
    - [takeWhile](#takewhile)
    - [dropWhile](#dropwhile)
    - [Zip and Unzip](#zip-and-unzip)
    - [ZipWith](#zipwith)
    - [Replicate](#replicate)
    - [Other Useful higher-order functions](#other-useful-higher-order-functions)
  - [Functions to Manipulate Characters and Strings](#functions-to-manipulate-characters-and-strings)
    - [Strings Features](#strings-features)
    - [Prelude String Functions](#prelude-string-functions)
    - [Data.Char String Functions](#datachar-string-functions)
    - [Data.List.Split String Functions](#datalistsplit-string-functions)
  - [Useful notations for functions](#useful-notations-for-functions)
- [Pattern Matching](#pattern-matching)
- [](#)
- [List Comprehension](#list-comprehension)
  - [Simple List Comprehension](#simple-list-comprehension)
  - [Comprehensions with multiple generators](#comprehensions-with-multiple-generators)
  - [Function Inside List Comprehension](#function-inside-list-comprehension)
  - [Comprehension with Guards](#comprehension-with-guards)
- [Abstract Data Type](#abstract-data-type)
- [Functors, Monads, Applicatives and Monoids](#functors-monads-applicatives-and-monoids)
  - [Functors](#functors)
  - [Monads](#monads)
    - [Overview](#overview-1)
    - [Bind Operator](#bind-operator)
    - [Monad Laws](#monad-laws)
    - [Selected Monad Implementations](#selected-monad-implementations)
    - [Return - Type constructor](#return---type-constructor)
    - [Haskell Monads](#haskell-monads)
    - [Monad function composition](#monad-function-composition)
    - [Sources](#sources)
  - [Maybe Monad](#maybe-monad)
  - [List Monad](#list-monad)
  - [IO and IO Monad](#io-and-io-monad)
    - [Main action](#main-action)
    - [Read and Show](#read-and-show)
    - [Operator >> (then)](#operator--then)
    - [Basic I/O Operations](#basic-io-operations)
    - [Do Notation](#do-notation)
      - [Basic Do Notation](#basic-do-notation)
      - [Do Notation and Let keyword](#do-notation-and-let-keyword)
      - [Do Notation returning a value](#do-notation-returning-a-value)
      - [Combining functions and I/O actions](#combining-functions-and-io-actions)
      - [Executing a list of actions](#executing-a-list-of-actions)
      - [Control Structures](#control-structures)
        - [For Loops](#for-loops)
      - [mapM and mapM_](#mapm-and-mapm_)
    - [IO Examples](#io-examples)
    - [Sources](#sources-1)
- [Useful Custom Functions/ Iterators and Operators](#useful-custom-functions-iterators-and-operators)
  - [Pipelining Operators](#pipelining-operators)
  - [Iterators](#iterators)
    - [Pair Iterator](#pair-iterator)
    - [Triples Iterator](#triples-iterator)
    - [Sliding Window Iterator](#sliding-window-iterator)
    - [Enumerate Iterator](#enumerate-iterator)
  - [Applying Multiples Functions](#applying-multiples-functions)
    - [Applying a list of functions to the same argument.](#applying-a-list-of-functions-to-the-same-argument)
    - [Applying a tuple of functions to a same argument.](#applying-a-tuple-of-functions-to-a-same-argument)
    - [Control Flow Functions](#control-flow-functions)
- [Applications](#applications)
  - [Mathematics](#mathematics)
  - [Picewise Functions](#picewise-functions)
  - [Numerical Methods](#numerical-methods)
    - [Polynomial](#polynomial)
    - [Numerical Derivate](#numerical-derivate)
    - [Nonlinear Equation - Root-finding](#nonlinear-equation---root-finding)
- [     t -> Int -> (t -> t) -> (t -> t) -> t -> (t, t, Int)](#t---int---t---t---t---t---t---t-t-int)
    - [Differential Equations](#differential-equations)
  - [Statistics and Time Series](#statistics-and-time-series)
    - [Some Statistical Functions](#some-statistical-functions)
    - [Monte Carlo Simulation Coin Toss](#monte-carlo-simulation-coin-toss)
- [](#-1)
- [](#-2)
- [](#-3)
- [](#-4)
  - [Vectors](#vectors)
  - [Tax Brackets](#tax-brackets)
  - [Small DSL Domain Specific Language](#small-dsl-domain-specific-language)
    - [String Processing](#string-processing)
- [Libraries](#libraries)
  - [System Programming in Haskell](#system-programming-in-haskell)
  - [Data.Time](#datatime)
    - [System](#system)
    - [Get current year / month / day in Haskell](#get-current-year--month--day-in-haskell)
    - [Get Current Time](#get-current-time)
    - [Documentation By Examples - GHCI shell](#documentation-by-examples---ghci-shell)
      - [Date Time Manipulation](#date-time-manipulation)
      - [Difference between two dates](#difference-between-two-dates)
      - [Day in a Week/Month/Year or Week Number](#day-in-a-weekmonthyear-or-week-number)
      - [Parsing Dates and Times from Strings](#parsing-dates-and-times-from-strings)
      - [Printing a Date](#printing-a-date)
- [Miscelanious](#miscelanious)
  - [Haskell IDEs and Text Editors](#haskell-ides-and-text-editors)
  - [GHCI configuration file](#ghci-configuration-file)
  - [Troubleshooting](#troubleshooting)
    - [Importing Ambigous Modules in GHCi](#importing-ambigous-modules-in-ghci)
- [Documentation and Learning Materials](#documentation-and-learning-materials)
  - [Code Search Engine](#code-search-engine)
  - [Libraries Documentation](#libraries-documentation)
    - [Prelude](#prelude)
    - [Type Classe](#type-classe)
    - [Online Books](#online-books)
    - [Books](#books)
    - [Papers and Articles](#papers-and-articles)
    - [Selected Wikipedia Articles](#selected-wikipedia-articles)
    - [Community](#community)
    - [References by Subject](#references-by-subject)
    - [Video Lectures](#video-lectures)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->


## Haskell

* Pure Functional programming language
* Strong Static Typed Language 
* Type Inference (The Haskell compiler deduce the types for you). 
* Lazy Evaluation ( Delayed evaluation) by default
* Data Immutability/ Haskell has no variables
    * Values can be bound to a name and can only be assigned once.
    * Values can never change.
* Haskell has not for-loop, while statements.
* Algebraic Data types
* Pattern Matching
* Tail Recursions
* Compiles to native code.


### Suffixes of file names for Haskell

```
.hs    Haskell source code; preprocess, compile

.lhs   literate Haskell source; unlit, preprocess, compile

.hi    Interface file; contains information about exported symbols

.hc    intermediate C files

.x_o   way x object files; common ways are: p, u, s

.x_hi  way x interface files
```


### Toolset

|                                    |                                                      |
|------------------------------------|------------------------------------------------------|
| ghc - the Glasgow Haskell Compiler | Transforms Haskell Source code .hs into native code. |
| ghci                               | Haskell Interactive Shell/ Interpreter               |
| runghc                             | Haskell Non Interactive Interpreter                  | 
| haddock                            | Documentation tool for annotated Haskell source code |
| cabal                              | GHC Haskell Cabal package manager                    |


### Install Haskell Platform

Binaries and Installation files: 
    * https://www.haskell.org/platform/
    * [Haskell for Linux](https://www.haskell.org/platform/linux.html)

Install Haskell Libraries:

```
cabal update

cabal install <some package>
```

<!--
@TODO: Add instructions of how to install  Haskell in Linux.
-->

### GHCI Reference

GHCI Interactive Shell

| Command                     |  Description                                |
|-----------------------------|---------------------------------------------|
| :help                       |  Show help                                  |
| :load [haskell-source.hs] or :l src.hs |    Load Haskell Source Code   |
| :reload or :r                    |  Reload Code after it was edited      |
| :type [symbol]   or :t [symbol]          |  Show the Type of a Symbol   |
| :browse                    |  Gives the type signature of all functions  |
| :set +s                     |  Print timing/memory stats after each evaluation |
| :{ [code here ] :}        |    Multiline Code                            |
| :set prompt ">"             |  Change the prompt to ">"                   |
| :cd [directory]       | change the current working directory to [directory] |
| :! [shell command>]   | execute the shell command; :! pwd  print the current directory |
| :quit                 | Quit the interpreter |


See also:
* [GHCI configuration file](#ghci-configuration-file)
* [GHCI Debugger](https://downloads.haskell.org/~ghc/latest/docs/html/users_guide/ghci-debugger.html)
* [GHC and GHCI Man Page](http://manpages.ubuntu.com/manpages/trusty/man1/ghci.1.html)

## Functional Programming Concepts

<!--
@TODO: Add concepts: Function composition, Pure language, Referential Transparency.
-->

### Overview

**Functional Programming**

Functional Programming is all about programming with functions.

**Functional Programming Features**

* Pure Functions / Referential Transparency / No side effect
* Function Composition
* Lambda Functions/ Anonymous Functions
* High Order Functions
* Currying/ Partial Function Application
* Closure - Returning functions from functions

* Data Immutability
* Pattern Matching
* Lists are the fundamental data Structure

Non Essential Features:

* Static Typing
* Type Inferencing
* Algebraic Data Types

**Functional Programming Design Patterns**

* Curry/ Partial function application  - Creating new functions by holding a parameter constant
* Closure - Return functions from functions
* Function composition
* Composable functions
* High Order Functions
* MapReduce Algorithms - Split computation in multiple computers cores.
* Lazy Evaluation ( aka Delayed evaluation)
* Pattern Matching


### Functional Programming Languages


Some Functional programing languages:

|  Language     | Purity  |Evaluation | Typing   | Type Discipline | Type Inference | OO  | AGDT | Platform | Family |  Curry |  Feature                |
|---------------|---------|-----------|----------|-----------------|----------------|-----|-----|----------|--------|------|---------------------------|  
| Haskell       | Pure    | Lazy    |   Static   |  Strong         | Yes            | No  | Yes | NAT      | ML/SML |  Yes |  Concurrency/Parallelism  |
| Ocaml         | Impure  | Strict  |   Static   |  Strong         | Yes            | Yes | Yes | NAT/BC   | ML/SML |  Yes |                            |
| F# (F sharp)  | Impure  | Strict  |   Static   |  Strong         | Yes            | Yes | Yes | .NET     | ML/SML |  Yes |  .NET Platform Integration |
| Scheme        | Impure  | Strict  |   Dynamic  |  Strong         | No             | No  | No  | -        | Lisp   |  No  |   Minimalistic Educational |
| Clojure       | Impure  | Strict  |   Dynamic  |  Strong         | No             | No  | No  | JVM      | Lisp   |  No  |   Java integration    | 
| Scala         | Impure  | Strict  |   Static   |  Strong         | Yes            | Yes | Yes | JVM      |        |      |   Java integration    |
| Erlang        | Impure  | Strict  |   Dynamic  |  Strong         | ?              | ?   |  ?  |          |  ?     |  ?   |   Telecommunications/ Servers |
| R             | Impure  | Strict  |   Dynamic  |  Strong         | No             | Yes |  -  | BC       | No     |  No  |   DSL - Statics  |
| Mathematica   | Impure  | Strict  |   Dynamic  |  ??             | Yes            | ?   |  ?  | ?        | No     |  No  |   DSL - Computer Algebraic System |


```
Notes:
* AGDT   - Algebraic Data Types
* JVM    - Java Virtual Machine / Java Platform
* .NET   - Dot Net Platform
* NAT    - Native Code
* BC     - Bytecode compilation
* OO     - Object Orientated
* Curry  - Curried functions like in Haskell
* DSL    - Domain Specific Language
```

More Information: [Comparison of Functional Programming Languages](http://en.wikipedia.org/wiki/Comparison_of_functional_programming_languages)

See also: [ML Dialects and Haskell: SML, OCaml, F#, Haskell](http://hyperpolyglot.org/ml)

### Pure Functions

Pure functions:

* Are functions without side effects, like mathematical functions. 
* For the same input the functions always returns the same output.
* The result of any function call is fully determined by its arguments. 
* Pure functions don't rely on global variable and don't have internal states.
* They don't do IO, i.e .:. don't print, don't write a file ...
* Pure functions are stateless
* Pure functions are deterministic

Why Pure Functions:

* Composability, one function can be connected to another.
* Can run in parallel, multi threading, multi core, GPU and distributed systems.
* Better debugging and testing.
* Predictability

**Example of pure functions**

```python
def min(x, y):
    if x < y:
        return x
    else:
        return y
```


**Example of impure function**

* Impure functions doesn't have always the same output for the same
* Impure functions does IO or has Hidden State or Global Variables

```python
exponent = 2

def powers(L):
    for i in range(len(L)):
        L[i] = L[i]**exponent
    return L
```
The function min is pure. It always produces the same result given 
the same inputs and it does not affect any external variable.

The function powers is impure because it not always gives the same output
for the same input, it depends on the global variable exponent:

```python

>>> exponent = 2
>>> 
>>> def powers(L):
...     for i in range(len(L)):
...         L[i] = L[i]**exponent
...     return L
... 
>>> powers([1, 2, 3])
[1, 4, 9]
>>> exponent = 4 
>>> powers([1, 2, 3])  # (It is impure since it doesn't give the same result )
[1, 16, 81]
>>> 
```

Another example, purifying an impure Language:

```python

>>> lst = [1, 2, 3, 4]  # An pure function doesn't modify its arguments.
>>>                     # therefore lst reverse is impure
>>> x = lst.reverse()
>>> x
>>> lst
[4, 3, 2, 1]

>>> lst.reverse()
>>> lst
[1, 2, 3, 4]
```

Reverse list function purified:

```python

>>> lst = [1, 2, 3, 4]
>>>
>>> def reverse(lst):
...     ls = lst.copy()
...     ls.reverse()
...     return ls
... 
>>> 
>>> reverse(lst)
[4, 3, 2, 1]
>>> lst
[1, 2, 3, 4]
>>> reverse(lst)
[4, 3, 2, 1]
>>> lst
[1, 2, 3, 4]

```


### Lazy Evaluation

"Lazy evaluation" means that data structures are computed incrementally, as they are needed (so the trees never exist in memory all at once) parts that are never needed are never computed. Haskell uses lazy evaluation by default.

Example in Haskell: 

```haskell
> let lazylist = [2..1000000000]
> 
> let f x = x^6 
> 
> take 5 lazylist 
[2,3,4,5,6]
>
>
> {- Only the terms needed are computed. -}
> take 5 ( map f lazylist )
[64,729,4096,15625,46656]
> 
```

Example in Python:

* Python uses eager evaluation by default. In order to get lazy evaluation in python the programmer must use iterators or generators. The example below uses generator.

```python

def lazy_list():
    """ Infinite list """
    x = 0 
    while True:
        x += 2
        yield x


>>> gen = lazy_list()
>>> next(gen)
2
>>> next(gen)
4
>>> next(gen)
6
>>> next(gen)
8
>>> next(gen)
10
>>> 

def take(n, iterable):
    return [next(iterable) for i in range(n)]

def mapi(func, iterable):   
    while True:
        yield func(next(iterable))
        
f = lambda x: x**5

>>> take(5, lazy_list())
[2, 4, 6, 8, 10]
>>> take(10, lazy_list())
[2, 4, 6, 8, 10, 12, 14, 16, 18, 20]
>>> 

>>> take(5, mapi(f, lazy_list()))
[32, 1024, 7776, 32768, 100000]
>>> 
>>> take(6, mapi(f, lazy_list()))
[32, 1024, 7776, 32768, 100000, 248832]
>>> 

```

## Basic Syntax

### Operators


#### Logic Operators

```
  True || False ⇒ True  
  True && False ⇒ False 
  True == False ⇒ False 
  True /= False ⇒ True  (/=) is the operator for different 
```

#### Powers

```
x^n     for n an integral (understand Int or Integer)
x**y    for y any kind of number (Float for example)
```


#### Application Operator - $

The application operator '$' makes code more readable and cleaner since substitutes parenthesis.
It is also useful in higher-order situations, such as map ($ 0) xs, or zipWith ($) fs xs. 

```haskell
> f $ g $ h x = f (g (h x))
```

#### Misc. Operators

```haskell
>>=     bind
>>      then
*>      then
->      to                a -> b: a to b
<-      bind (drawn from) (as it desugars to >>=)
<$>     (f)map
<$      map-replace by    0 <$ f: "f map-replace by 0"
<*>     ap(ply)           (as it is the same as Control.Monad.ap)
$                         (none, just as " " [whitespace])
.       pipe to           a . b: "b pipe-to a"
!!      index
!       index / strict    a ! b: "a index b", foo !x: foo strict x
<|>     or / alternative  expr <|> term: "expr or term"
++      concat / plus / append
[]      empty list
:       cons
::      of type / as      f x :: Int: f x of type Int
\       lambda
@       as                go ll@(l:ls): go ll as l cons ls
~       lazy              go ~(a,b): go lazy pair a, b

_       Whatever          Used in Pattern Matching
```





### Defining Values and Types

```haskell

> let b = 100 :: Float
> let a  = 100 :: Int
> let c = 100 :: Double
> 
> b
100.0
> :t b 
b :: Float
> :t a 
a :: Int
> :t c
c :: Double
> 
> let x = 100.2323
> :t x
x :: Double
> 
> let y = [1..10]
> y
[1,2,3,4,5,6,7,8,9,10]
> 
> let z = [1, 2, 4, 5, 6] :: [Float]
> :t z
z :: [Float]

> let k = [1.2, 1.3, 1.4, 1.5 ]
> k
[1.2,1.3,1.4,1.5]
> 
> :t k
k :: [Double]
```

### Type System

* A type is a collection of related values.

* Typeclasses are sets of types.

* A class is a collection of types that support certain operations, called the methods of the class.

* Each expressions must have a valid type, which is calculated before to evaluating the expression by the Haskell compiler, it is called type inference;

* Haskell programs are type safe, since type errors can never occur during run time;

* Type inference detects a very large class of programming errors, and is one of the most powerful and useful features of Haskell.


Reference:
* [Graham Hutton Lecture](http://www.cs.nott.ac.uk/~gmh/functional.ppt)
* [Graham Hutton - University of Nottingham](http://www.cs.nott.ac.uk/~gmh/)


#### Basic Types

|            |                   |              |
|------------|-------------------|--------------|
| Char       |  'a' / 'b' / 'c'  |  Char Type   |
| [Char]     |  "String"         |  String      |
| Bool       |   True / False    |  Boolean     |
| Int        |   1, 2, 3, 4      |  Integers in a finite range.  -2^29 to (2^29 - 1) |          
| Integer    |   1, 2, 3, 4      |  Arbitrary Precision Integer |
| Float      | 1.0, 2.0, 3.0     |  32 bits float point |
| Double     | 1.0, 2.0, 3.0     |  64 bits float point |
| (Int, Char)|  (1, 'a')         | Tuples, unlike lists elements can have different types. |
| [a]        | [1, 2, 3, 4]      | List has the type [Int], [Char], [Double] |



**Selected Numeric Types**


| Type |  Description |
|------|--------------|
| Double |  Double-precision floating point. A common choice for floating-point data. |
| Float |  Single-precision floating point. Often used when interfacing with C. |
| Int |  Fixed-precision signed integer; minimum range [-2^29..2^29-1]. Commonly used. |
| Int8 |  8-bit signed integer |
| Int16 |  16-bit signed integer |
| Int32 |  32-bit signed integer |
| Int64 |  64-bit signed integer |
| Integer |  Arbitrary-precision signed integer; range limited only by machine resources. Commonly used. |
| Rational |  Arbitrary-precision rational numbers. Stored as a ratio of two Integers. |
| Word |  Fixed-precision unsigned integer; storage size same as Int |
| Word8 |  8-bit unsigned integer |
| Word16 |  16-bit unsigned integer |
| Word32 |  32-bit unsigned integer |
| Word64 |  64-bit unsigned integer |

References: 

* http://shuklan.com/haskell/lec03.html#/0/1
* http://shuklan.com/haskell/lec05.html
* http://book.realworldhaskell.org/read/using-typeclasses.html

| Class      |   Class Instance
|------------|------------------------------|
| Num        | Int, Integer, Nat, Float, Double, Complex  |
| Real       | Int, Integer, Nat. Float, Double, Complex  |
| Fractional | Float, Double, Rational, Complex  |
| Integral   | Int, Nat, Integer, Natural      |
| RealFrac   | Float, Double, Rational, Complex |
| Floating   | Float, Double, Complex    |
| RealFloat  | Float, Double, Complex |


![](images/classes.gif)

#### Basic Type Classes

|        |                  |
|--------|------------------|
| Eq     |  Equality Types  |
| Ord    |  Ordered Types   |
| Show   |  Showables Types |
| Read   |  Readable Types  |
| Num    |  Numeric Types   |
| Enum   |  Enum Types      |

Example Methods:

```haskell
(==) :: (Eq a)   => a -> a -> Bool

(<)  :: (Ord a)  => a -> a -> Bool

show :: (Show a) => a -> String

read :: (Read a) => String -> a

(*)  :: (Num a)  => a -> a -> a
```


```
Value -->  Type --> Typeclass
```

Standard Typeclasses:

* Show: Representable as String
* Enum: Enumerable in a list
* Num:  Usable as a number
* Ord:  Used for thing with total order


#### Standard Haskell Types

Credit: [The Haskell 98 Report - Predefined Types and Classes](http://www2.informatik.uni-freiburg.de/~thiemann/haskell/haskell98-report-html/basic.html)

Booleans

```haskell
data  Bool  =  False | True deriving 
                             (Read, Show, Eq, Ord, Enum, Bounded)
```

Characters and Strings

```haskell
type  String  =  [Char]
```

Lists

```haskell
data  [a]  =  [] | a : [a]  deriving (Eq, Ord)
```

The Unit Datatype ()

```haskell
data  () = () deriving (Eq, Ord, Bounded, Enum, Read, Show)
```

Other Types

```haskell
data  Maybe a     =  Nothing | Just a  deriving (Eq, Ord, Read, Show)
data  Either a b  =  Left a | Right b  deriving (Eq, Ord, Read, Show)
data  Ordering    =  LT | EQ | GT deriving
                                  (Eq, Ord, Bounded, Enum, Read, Show)
```                                  

#### Standard Haskell Classes

Credit: [The Haskell 98 Report - Predefined Types and Classes](http://www2.informatik.uni-freiburg.de/~thiemann/haskell/haskell98-report-html/basic.html)


The Eq Class

```haskell
class  Eq a  where
    (==), (/=)  ::  a -> a -> Bool

    x /= y  = not (x == y)
    x == y  = not (x /= y)
```   

The Ord Class

```haskell
  class  (Eq a) => Ord a  where
    compare              :: a -> a -> Ordering
    (<), (<=), (>=), (>) :: a -> a -> Bool
    max, min             :: a -> a -> a

    compare x y | x == y    = EQ
                | x <= y    = LT
                | otherwise = GT

    x <= y  = compare x y /= GT
    x <  y  = compare x y == LT
    x >= y  = compare x y /= LT
    x >  y  = compare x y == GT

    -- Note that (min x y, max x y) = (x,y) or (y,x)
    max x y | x <= y    =  y
            | otherwise =  x
    min x y | x <= y    =  x
            | otherwise =  y
```


The Read and Show Classes

```haskell
type  ReadS a = String -> [(a,String)]
type  ShowS   = String -> String

class  Read a  where
    readsPrec :: Int -> ReadS a
    readList  :: ReadS [a]
    -- ... default decl for readList given in Prelude

class  Show a  where
    showsPrec :: Int -> a -> ShowS
    show      :: a -> String 
    showList  :: [a] -> ShowS

    showsPrec _ x s   = show x ++ s
    show x            = showsPrec 0 x ""
    -- ... default decl for showList given in Prelude
```

The Enum Class

```haskell
class  Enum a  where
    succ, pred     :: a -> a
    toEnum         :: Int -> a
    fromEnum       :: a -> Int
    enumFrom       :: a -> [a]            -- [n..]
    enumFromThen   :: a -> a -> [a]       -- [n,n'..]
    enumFromTo     :: a -> a -> [a]       -- [n..m]
    enumFromThenTo :: a -> a -> a -> [a]  -- [n,n'..m]
    -- Default declarations given in Prelude
```

#### Numeric Types Conversion

```
fromInteger             :: (Num a) => Integer -> a
fromRational            :: (Fractional a) => Rational -> a
toInteger               :: (Integral a) => a -> Integer
toRational              :: (RealFrac a) => a -> Rational
fromIntegral            :: (Integral a, Num b) => a -> b
fromRealFrac            :: (RealFrac a, Fractional b) => a -> b

fromIntegral            =  fromInteger . toInteger
fromRealFrac            =  fromRational . toRational
```

https://www.haskell.org/tutorial/numbers.html

#### Haskell-Style Syntax for types:

Function g from type a to type b: 

```haskell
g :: a -> b
```

Function with two arguments and result of type a:

```haskell
s :: a -> a -> a
```

Function f from a type a to type m b, a type m parametrized on type b

```haskell
f :: a -> m b
```

A function h which takes as argument two functions of type 
a -> b and b -> c and returns a function of type a -> m b

```haskell
h :: ( a -> b) -> (b -> c) -> ( a -> m b)
```

### Lists

Haskell lists are built from nils ([]) empty list, and cons (:).

```haskell
[x0, x1, x2, x3, ..., xn-1, xn] = x0:x1:x2:x3:...:xn-1:xn:[]
```

#### Creating Lists

```haskell

> [-4, 10, 20, 30.40]

> let x = [-23, 40, 60, 89, 100]
> x
[-23,40,60,89,100]


> [0..10]
[0,1,2,3,4,5,6,7,8,9,10]
> 
> [-4..10]
[-4,-3,-2,-1,0,1,2,3,4,5,6,7,8,9,10]
> 

```

#### List Operations

Picking the nth element of a list.

```haskell

> [1, 2, 3, 4, 5, 6] !! 2
3
> [1, 2, 3, 4, 5, 6] !! 3
4
> [1, 2, 3, 4, 5, 6] !! 0
1
```

```haskell
> let lst  = [-4..10]
> lst
[-4,-3,-2,-1,0,1,2,3,4,5,6,7,8,9,10]
```
First Element
```haskell
> head [1, 2, 3, 4, 5]
1
```

Last Element
```haskell
> last [1, 2, 3, 4, 5]
5
```

Maximum element
```haskell
> maximum lst
10
```

Minimum element
```haskell
> minimum lst
-4
```

Reversing a list
```haskell

> reverse [1, 2, 3, 4, 5]
[5,4,3,2,1]
```

Sum of all elements
```haskell
> sum lst
45
```

Product of all elements
```haskell
> product lst
0
```

Adding an element to the begining of the list

```haskell
> 20 : lst
[20,-4,-3,-2,-1,0,1,2,3,4,5,6,7,8,9,10]
```

Adding an element to end of the list

```haskell

> lst ++ [20]
[-4,-3,-2,-1,0,1,2,3,4,5,6,7,8,9,10,20]
> 
```

Extract the elements after the head of a list, which must be non-empty. 
* tail :: [a] -> [a]    Source

```haskell
> tail [1, 2, 3, 4, 5]
[2,3,4,5]

```

Return all the elements of a list except the last one. The list must be non-empty.
* init :: [a] -> [a]    Source
```haskell
> init [1, 2, 3, 4, 5]
[1,2,3,4]
> 
```

Make a new list containing just the first N elements from an existing list. 
* take n xs
```haskell
> take 5 lst
[-4,-3,-2,-1,0]
```



Delete the first N elements from a list. 
* drop n xs

```haskell

> lst
[-4,-3,-2,-1,0,1,2,3,4,5,6,7,8,9,10]
> 
> drop 5 lst
[1,2,3,4,5,6,7,8,9,10]

```

Split a list into two smaller lists (at the Nth position). 

* splitAt n xs

```haskell

-- (Returns a tuple of two lists.) 

> splitAt 5 lst
([-4,-3,-2,-1,0],[1,2,3,4,5,6,7,8,9,10])
> 

```

TakeWhile, applied to a predicate p and a list xs, returns the longest 
prefix (possibly empty) of xs of elements that satisfy p:
* takeWhile :: (a -> Bool) -> [a] -> [a]

```haskell

> takeWhile (< 3) [1,2,3,4,1,2,3,4]
[1,2]
> takeWhile (< 9) [1,2,3]
[1,2,3]
>  takeWhile (< 0) [1,2,3]
[]

```

DropWhile p xs returns the suffix remaining after takeWhile p xs: 

* dropWhile :: (a -> Bool) -> [a] -> [a]    Source

```haskell

> takeWhile (< 3) [1,2,3,4,1,2,3,4]
[1,2]
> takeWhile (< 9) [1,2,3]
[1,2,3]
>  takeWhile (< 0) [1,2,3]
[]
> dropWhile (< 3) [1,2,3,4,5,1,2,3] 
[3,4,5,1,2,3]
>  dropWhile (< 9) [1,2,3]
[]
> dropWhile (< 0) [1,2,3] 
[1,2,3]
> 

```

Concating Nested Lists

```haskell
> :t concat
concat :: [[a]] -> [a]

> concat [[1, 2], [], [233, 33], [1, 2, 3]]
[1,2,233,33,1,2,3]

> concat ["hello", " world", " Haskell", "FP"]
"hello world HaskellFP"
> 
 

```


#### Chekings Lists

Check if a list is empty. 
* null xs

```haskell

> null []
True
> null [1, 2, 3, 4, 5]
False

```

Find out whether any list element passes a given test. 
* any my_test xs

```haskell

> any (>3) [1, 2, 3, 4, 5]
True
> any (>10) [1, 2, 3, 4, 5]
False
> 
> any (==3) [1, 2, 3, 4, 5]
True
> 
> any (==10) [1, 2, 3, 4, 5]
False
> 
```

Check whether all list elements pass a given test. 
* all my_test xs

```haskell

> all (>3) [1, 2, 3, 4, 5]
False
> all (<10) [1, 2, 3, 4, 5]
True
> all (<10) [1, 2, 3, 4, 5, 20]
False
> 
```

Check if elements belongs to the list.

* elem :: Eq a => a -> [a] -> Bool

```haskell

> elem 1  [1,2,3] 
True
> elem 4 [1,2,3] 
False
>
```


## Functions

### Creating functions

In the GHCI Shell

```haskell

> let f x y = sqrt ( x^2 + y^2 )
> 
> f 80 60
100.0
> f 50 30
58.309518948453004
> 

> :t f
f :: Floating a => a -> a -> a

```

In a Haskell source file, *.hs

```haskell
f x y = sqrt ( x^2 + y^2 )
```

### Anonymous Functions or Lambda Functions

<!--
@TODO: Add more anonymous functions examples.
-->

```haskell

> (\x -> x^2 - 2.5*x) 10
75.0

> let f = \x -> x^2 - 2.5*x

> map f [1, 2, 3, 4, 5]
[-1.5,-1.0,1.5,6.0,12.5]

> map (\x -> x^2 - 2.5*x) [1, 2, 3, 4, 5]
[-1.5,-1.0,1.5,6.0,12.5]

>  let f = (\x y -> x + y)
>  
>  f 20 30
50
>  let f20 = f 20
>  f20 10
30
>  x/y + x*y) 10 20
200.5
>  x/y + x*y) (10, 20)
200.5
>  


```

### Infix Functions

Any function of two arguments can be used as an infix function or custom operator.

Example:

```haskell
> let addVectors (a1, a2, a3) (b1, b2, b3) = (a1+b1, a2+b2, a3+b3)
> let subVectors (a1, a2, a3) (b1, b2, b3) = (a1-b1, a2-b2, a3-b3)

> :t addVectors 
addVectors :: (Num t, Num t1, Num t2) =>  (t, t1, t2) -> (t, t1, t2) -> (t, t1, t2)

> :t subVectors 
subVectors   :: (Num t, Num t1, Num t2) => (t, t1, t2) -> (t, t1, t2) -> (t, t1, t2)


> addVectors (23, 10, 4) (3, 8, 9)
(26,18,13)


> (23, 10, 4) `addVectors` (3, 8, 9) -- Used as an infix function
(26,18,13)
> 

> subVectors (23, 10, 4) (3, 8, 9)
(20,2,-5)
> 

> (23, 10, 4) `subVectors` (3, 8, 9)
(20,2,-5)
> 

> let f x y = 10*x - y**2
> 
> f 10 3
91.0
> 10 `f` 3
91.0
> 

> let addJust (Just a) (Just b) = Just (a+b)
> addJust (Just 10) (Just 30)
Just 40
> 

> (Just 10) `addJust` (Just 30) -- Used as custom operator
Just 40
> 
```


### Infix Operators as Functions

<!--
@TODO: Add more examples with logical infix operators
-->

In Haskell the infix operators can be seen as a two-argument function.

```
x + y is equivalent to add x y or (+ x y)
```


**Arithmetic Operators**

| Shorthand  |  Equivalence         | Type Signature |
|------------|----------------------|----------------|
| (+4)       |  \x -> x 4           |                |
| (*3)       |  \x -> x * 3           | |
| (/2)       |  \x -> x / 2           | |
| ((-)5)     |  \x -> 5 - x         | |
| (^2)       |  \x -> x ^ 2           | |
| (2^)       |  \x -> 2 ^ x           | |
| (+)        |  \x y -> x + y        | (+) :: Num a => a -> a -> a        |
| (-)        |  \x y -> x - y         | (-) :: Num a => a -> a -> a        |
| (/)        |  \x y -> x / y         | (/) :: Fractional a => a -> a -> a |
| (^)        |  \x y -> x ^ y         | (^) :: (Integral b, Num a) => a -> b -> a |
| (**)       |  \x y -> x ** y        | (**) :: Floating a => a -> a -> a |

**Comparison Operator**

| Shorthand  |  Equivalence         | Type Signature |
|------------|----------------------|----------------|
| (>)        |  \x y -> x > y       | (>) :: Ord a => a -> a -> Bool |
| (<)        |  \x y -> x < y       | (<) :: Ord a => a -> a -> Bool |
| (>=)       |  \x y -> x >= y      | (>=) :: Ord a => a -> a -> Bool |
| (<=)       |  \x y -> x <= y      | (<=) :: Ord a => a -> a -> Bool |
| (==)       |  \x y -> x == y      | (==) :: Eq a => a -> a -> Bool |
| (/=)       |  \x y -> x /= y      | (/=) :: Eq a => a -> a -> Bool |

**Boolean operators**

| Shorthand  |  Equivalence         | Type Signature | Name |
|------------|----------------------|----------------|------|
| (&&)        |  \x y -> x && y         | (&&) :: Bool -> Bool -> Bool | And |
| (||)       |  \x y z -> x || y        | (||) :: Bool -> Bool -> Bool | Or |
| (not)       | not x                   |  not :: Bool -> Bool         | Not |

**List and Tuples Operators**

| Shorthand  |  Equivalence         | Type Signature                   | Name            |
|------------|----------------------|----------------------------------|-----------------|
| (,)        |  \x y -> (x, y)      | (,) :: a -> b -> (a, b)          | Tuple of two elements |
| (,,)       |  \x y z -> (x, y, z) | (,,) :: a -> b -> c -> (a, b, c) | Tuple of three elements |
| (!!)       | alist !! i = alist[i] |  (!!) :: [a] -> Int -> a        | Nth element of a list |
| (:)        | \x xs -> x:xs       | (:) :: a -> [a] -> [a]           | Cons            |

**Examples**

```haskell
> (+) 10 30.33
40.33

> map ((+) 10) [1, 20, 43, 44]
[11,30,53,54]
> 

> (-) 100 30
70

> map ((-) 100) [10, 20, 80, -50]
[90,80,20,150]
> 
> map (flip (-)100) [10, 20, 80, -50]
[-90,-80,-20,-150]


> (/) 100 10
10.0

> (*) 40 30
1200

> map (*10) [1, 2, 3, 4]
[10,20,30,40]
> 

> (^) 2 6
64

> 4 ** 0.5
2.0

> 2 ** 0.5
1.4142135623730951

> (**) 2  3.5
11.313708498984761
>

> map ((**) 0.5) [1, 2, 3, 4]
[0.5,0.25,0.125,6.25e-2]

> map ((flip (**)) 0.5) [1, 2, 3, 4]
[1.0,1.4142135623730951,1.7320508075688772,2.0]
> 

> (,) 4 5
(4,5)

> map ((,)4) [1, 2, 3, 4]
[(4,1),(4,2),(4,3),(4,4)]

> map ((flip (,)) 4) [1, 2, 3, 4]
[(1,4),(2,4),(3,4),(4,4)]

> (,,) 4 5 7
(4,5,7)

> ((,,) 4) 5 6
(4,5,6)

> map (uncurry ((,,) 4)) [(5, 6), (1, 1), (3, 4)]
[(4,5,6),(4,1,1),(4,3,4)]

> map ((,,) 12 4) [1, 2, 3, 4]
[(12,4,1),(12,4,2),(12,4,3),(12,4,4)]
> 

> alist =  ['a', 'b', 'c', 'd', 'e'] 
> alist !! 0 
'a'
> alist !! 3
'd'
> 
> (!!3) alist
'd'
> (!!0) alist
'a'
> 
> (!!) alist 0
'a'
> (!!) alist 3
'd'

> map ((!!) alist) [0, 2, 3, 4]
"acde"
> 
> map (!!2) [['a', 'b', 'c'], ['y', 'w', 'x', 'z'], ['1', '2', '3', '4']]
"cx3"
> 


> (>) 30 10
True
> (<) 30 10
False
>
> map (>30) [60, 380, 23, 1, 100]
[True,True,False,False,True]
> 
> filter (>30) [60, 380, 23, 1, 100]
[60,380,100]
> 

> (==) 100 10
False
> (==) 10 10
True
> 
> 
> filter (==10) [100, 10, 20, 10, 30]
[10,10]
> 
> map (uncurry (==)) [(100, 100), (10, 23), (34, 44), (0, 0)]
[True,False,False,True]
> 
> filter (uncurry (==)) [(100, 100), (10, 23), (34, 44), (0, 0)]
[(100,100),(0,0)]
> 

> 10 /= 100
True
> 10 /= 10
False
> 
> 
> filter (/=10) [100, 10, 20, 10, 30]
[100,20,30]
> 
> filter (uncurry (/=)) [(100, 100), (10, 23), (34, 44), (0, 0)]
[(10,23),(34,44)]

> :t (+)
(+) :: Num a => a -> a -> a
> 
> :t (-)
(-) :: Num a => a -> a -> a
> 
> :t (/)
(/) :: Fractional a => a -> a -> a
> 
> :t (*)
(*) :: Num a => a -> a -> a
> 
> :t (^)
(^) :: (Integral b, Num a) => a -> b -> a

{- Cons Operator -}
> :t (:)
(:) :: a -> [a] -> [a]
> 

> (1:) [9, 2, 3, 4]
[1,9,2,3,4]
> 

> (:) 1 []
[1]

> (:) 1 [0, 3, 5, 6]
[1,0,3,5,6]
> 


> map (-1:) [[1, 2, 3], [5, 6], [0]]
[[-1,1,2,3],[-1,5,6],[-1,0]]
> 

> map ((:) 89) [[1, 2, 3], [5, 6], [0]]
[[89,1,2,3],[89,5,6],[89,0]]
> 


> 1:[]
[1]
> 1:2:[]
[1,2]
> 1:2:3:[]
[1,2,3]
> 

> 1:[0]
[1,0]
> 2:1:[0]
[2,1,0]
> 

> (2:[1, 9, 8, 10])
[2,1,9,8,10]
> 

> (:[1, 2, 3, 4])  0
[0,1,2,3,4]
> 

> map (:[1, 2, 3, 4])  [89, 77, 55, 66]
[[89,1,2,3,4],[77,1,2,3,4],[55,1,2,3,4],[66,1,2,3,4]]
> 

> map (:["haskell "])  ["amazing", "awsome", "cool" ]
[["amazing","haskell "],["awsome","haskell "],["cool","haskell "]]
> 


```

### Currying

<!--
@TODO: Show the same example in other languages like: F#, Ocaml and Python
-->

Example 1:

```haskell

> let add a b = a + b
> let add10 = add 10
> 
> add 20 30
50
> add (-10) 30
20
> add10 20
30
> add10 30
40
> map add10 [-10, 20, 30, 40]
[0,30,40,50]
> 
```

### Function Composition / Composition Operator

In Haskell the operator (.) dot is used for composing functions. Pure functions can be composed like math functions.

See also: [Function composition (computer science)](http://en.wikipedia.org/wiki/Function_composition_%28computer_science%29)

```
(.) :: (b -> c) -> (a -> b) -> a -> c

Given:
    
    f :: b -> c
    g :: a -> b

(f . g ) x = f (g x)

    h = f . g
    h :: a -> c
```

Function Composition Block Diagram

```haskell
                f . g
        ................................
        . /------\        /------\     . 
a -->   . |  g   |  -->   |  f   | --> .---> c
        . \------/   b    \------/  c  . 
        ................................
           g :: a -> b   f :: b -> c
    
    (.) :: (b -> c) -> (a -> b) -> a -> c
```


Composition Law

```
id . f = f                  Left  identity law
f . id = f                  Right identity law
(f . g) . h = f . (g . h)   Associativity


Constant Function Composition
f       . const a = const (f a)
const a . f       = const a

dentity function            -->  id x = x 
const - Constant Function   --> const a b =  a   
```

Simplifying Code with function composition:

```
    h( f ( g( x)))  ==>  (h . f . g ) x   OR  h . f . g  $ x 
OR   
    h $ f $ g x     ==>   h . f . g $ x    

                                 Point Free Style
composed x = h . f . g $ x ==>   composed = h . f . g 
```

Function Composition with Map and Filter

```
h :: c -> [a]
f :: a -> b

map :: (a -> b) -> [a] -> [b]
filter :: (a -> Bool) -> [a] -> [a]


map     f (h c) = map    f . h $ c
filter  f (h c) = filter f . h $ c
```

Inverting Predicate Functions

```
inverted_predicate == not . predicate
```

```haskell
> not True
False
> not False
True
> 

> (>5) 10
True
> (>5) 3
False

> not . (>5) $ 10
False
> not . (>5) $ 3
True
> 

> let f = not . (>5)
> f 10
False
> f 5
True

> import Data.List
> 
> filter ( isPrefixOf "a" ) ["a","ab","cd","abcd","xyz"]
["a","ab","abcd"]
> 
> filter ( not . isPrefixOf "a" ) ["a","ab","cd","abcd","xyz"]
["cd","xyz"]
> 


```


Example:

```haskell
> let f = (+4)
> let g = (*3)
> 
> 
> f (g 6) -- (+4) ((*3) 6) = (+4) 18 = 22
22
> 
> (f . g) 6
22
> 
> (.) f g 6
22
> 
> let h = f . g
> 
> h 6
22
>  

> id 10
10
> id 3
3
> 
> id Nothing
Nothing
> id 'a'
'a'
> id (Just 10)
Just 10
> 


> (f . id) 10
14
> (id . f) 10
14
> 

> const 10 20
10
> const 10 3
10
> 

> (f . (const 10)) 4
14
> (f . (const 10)) 3
14
> const 10 . f $ 7
10
> const 10 . f $ 3
10
> 

{- Avoiding Parenthesis with composition -}
> let g x = x * 2
> let f x = x + 10
> let h x = x - 5
> 
> h (f (g 3))
11
> h $ f $ g 3
11
> 
> (h . f . g ) 3
11
> h . f . g $ 3
11
> 

{- Function Composition with curried functions -}

> let f1 x y = 10*x + 4*y
> let f2 a b c = 4*a -3*b + 2*c
> let f3 x = 3*x

> (f1 3 ( f3 5))
90
> 
> f1 3 $ f3 5
90
> 
> f1 3 . f3 $ 5
90
> 
> let f = f1 3 . f3 
> 
> f 5
90
> f 8
126
> 


> (f1 4 (f2 5 6 (f3 5)))
168
> 
> f1 4 $ f2 5 6 $ f3 5
168
> 
> f1 4 . f2 5 6 . f3 $ 5
168
> 
> let g = f1 4 . f2 5 6 . f3 {- You can also create new functions -}
> :t g
g :: Integer -> Integer
> g 5
168
> g 10
288
> 

{- Function Composition with Map and Filter -}

> import Data.Char

> :t ord
ord :: Char -> Int

> :t ordStr
ordStr :: [Char] -> [Int]
> 

> ordStr "curry"
[99,117,114,114,121]
> 
> let r x= x + 30
> 
> map r (ordStr "curry")
[129,147,144,144,151]
> 
> map r $ ordStr "curry"
[129,147,144,144,151]
> 
> map r . ordStr $ "curry"
[129,147,144,144,151]
> 
> sum . map r . ordStr $ "curry"
715
> 

> let s =  map r . ordStr
> s "curry"
[129,147,144,144,151]
> s "haskell"
[134,127,145,137,131,138,138]
> 

let sum_ord = sum . map r . ordStr 

> sum_s "curry"
715
> sum_s "haskell"
950
> 
> sum_ord "curry"
715
> sum_ord "haskell"
950
> 


> map ord (map toUpper "haskell")
[72,65,83,75,69,76,76]
> 
> map ord . map toUpper $ "haskell"
[72,65,83,75,69,76,76]
> 

> map (flip (-) 10) . map ord . map toUpper $ "haskell"
[62,55,73,65,59,66,66]
> 

> map chr . map (flip (-) 10) . map ord . map toUpper $ "haskell"
">7IA;BB"
> 

{- The function f is in point free style -}

> let f = map chr . map (flip (-) 10) . map ord . map toUpper
> 
> f "haskell"
">7IA;BB"
> 

```

<!--
-->


### The $ apply operator.

```haskell
f $ x = f x

> :t ($)
($) :: (a -> b) -> a -> b
```

Example: This operator is useful to apply an argument to a list of functions.

```haskell
> ($ 10) (*3)
30
> 
> let f x = x*8 - 4
> 
> ($ 10) f
76
> 

> map ($ 3) [(*3), (+4), (^3)]
[9,7,27]
> 

```

OR

```haskell
> let apply x f = f x
> 
> map (apply 3)  [(*3), (+4), (^3)]
[9,7,27]
> 

```

See also the Clojure function [juxt](https://clojuredocs.org/clojure.core/juxt)

Apply a set of functions to a single argument.

```haskell
> let juxt fs x = map ($ x) fs

> juxt [(*3), (+4), (/10)] 30
[90.0,34.0,3.0]
> 
> let fs = juxt [(*3), (+4), (/10)]
> 
> :t fs
fs :: Double -> [Double]
>
> fs 30
[90.0,34.0,3.0]
> fs 40
[120.0,44.0,4.0]
> 
> map fs [10, 20, 30]
[[30.0,14.0,1.0],[60.0,24.0,2.0],[90.0,34.0,3.0]]
> 
> 
```


### Recursion

Reverse A list

```haskell

reverse2 :: [a] -> [a]
reverse2 []     = []
reverse2 (x:xs) = reverse2 xs ++ [x]

*Main> reverse2 [1, 2, 3, 4, 5]
[5,4,3,2,1]
```

Product of a List

```haskell

prod :: [Int] -> Int
prod [] = 1
prod (x:xs) = x * prod xs


*Main> prod [1, 2, 3, 4, 5]
120
*Main> 
*Main> :t prod
prod :: [Int] -> Int
```
Factorial

```haskell

fact 0 = 1
fact n = n*fact(n-1)

> map fact [1..10]
[1,2,6,24,120,720,5040,40320,362880,3628800]
```

Fibonacci Function

```haskell
fib 0 = 1
fib 1 = 1
fib n | n>= 2
    = fib(n-1) + fib(n-2)
```


### Integer Arithmetic Functions

| Function | Description |
|----------|-------------|
| even     | Test if number is even, multiple of 2 |
| odd      | Test if number is odd, non multiple of 2 |
| quot     | Quotient of two numbers | 
| rem      | Remainder from the quotient | 
| div      | Similar to "quot", but is rounded down towards minus infinity |
| mod | Returns the modulus of the two numbers | 
| divMod | Returns the quotient and the modulus tuple |
| gcd   | Greatest common divisor of two numbers |
| lcd   | Lowest Common Multiple of two numbers |
| compare | Compare two numbers |

Exaples:

```haskell

{- -------------------Interger Division----------------- -}

{- Division Quotient -}

> quot 70 8
8
> 
> quot (-80)  8
-10
> 
> 80 `quot` 8
10
> 

> div 100 8
12
> 
> div (-100) 8
-13
> quot (-100) 8
-12
> 
> 100 `div` 8
12
> 

{- Remainder-}

> rem 100 12
4
> rem 100 10
0
> 100 `rem` 12
4
> 100 `rem` 10
0
> 
> rem (-100) 12
-4
> rem (-100) 10
0
> (-100) `rem` 12
-4
> (-100) `rem` 10
0
> 


> mod 100 12
4
> mod 100 10
0
> 100 `mod` 12
4
> 100 `mod` 10
0
> 
> mod (-100) 12
8
> 
> (-100) `mod` 12
8
> 


{- DivMod Quotient and Modulus of Division -}

> divMod 100 12
(8,4)
> divMod 100 10
(10,0)
> 100 `divMod` 12
(8,4)
> 100 `divMod` 10
(10,0)
> 
> divMod (-100) 12
(-9,8)
> divMod (-100) 10
(-10,0)
> 


{- Odd / Even Test -}

> even 20
True
> even 31
False

> odd 20
False
> odd 31
True

> [1..10]
[1,2,3,4,5,6,7,8,9,10]
> filter odd [1..10]
[1,3,5,7,9]
> filter even [1..10]
[2,4,6,8,10]
> 

{- Greatest Common Divisor -}

> gcd 840 15
15
> 
> gcd 21 14
7
> 
> 

> foldl1 gcd [21, 14, 35, 700]
7
> 


{- Lowest Common Multiple -}

> lcm 9 36
36
> 
> lcm 15 35
105
> 
{- 
    Lowest Common multiple of a list of numbers
    15 = 3 x 5
    35 = 5 x 7
    20 = 4 x 5
    40 = 8 x 5
    
    lcm = 3 x 5 x 8 = 840
-}
> foldl1 lcm [15, 35, 20, 40]
840
> 
```

Reference:

* http://en.wikibooks.org/wiki/Haskell/A_Miscellany_of_Types


### Mathematical Functions

Negate, Sqrt, Log, Exp and Power 

```haskell

{- Negate -}

> negate 100
-100
> negate 100.324
-100.324
> 


{- Natural logarithm -}
> log 10
2.302585092994046
> 

{- Logarithm to any base -}

> let log10 = logBase 10
> let log2  = logBase 2
> 
> log10 100
2.0
> map log10 [1, 10, 20, 100, 1000]
[0.0,1.0,1.3010299956639813,2.0,3.0]
> 
> map log2 [1, 2, 4, 8, 16]
[0.0,1.0,2.0,3.0,4.0]
> 

{- Square Root -}
> sqrt 100
10.0
> sqrt 10
3.1622776601683795
> 

{- Exponential function -}
> exp 1
2.718281828459045
> exp 2
7.38905609893065
> 

{- Pow/ Power Function x^y-}

> sqrt 2
1.4142135623730951
> 2 ** 0.5
1.4142135623730951
> 

> 2** 3
8.0
> 
> (**) 2 3
8.0
> 

> map round [13.03123, 13.20, 13.50, 13.60, 13.992]
[13,13,14,14,14]
> 
```

Trigonometric Functions

```haskell

> pi
3.141592653589793
>

> sin pi
1.2246063538223773e-16
> 
> sin (pi/3)
0.8660254037844386
> 
> asin (0.8660254037844386) == pi/3
True
> 


> cos pi
-1.0
>
> acos (-1)
3.141592653589793
> acos (-1) == pi
True
> 



> atan 1
0.7853981633974483
> 

> atan2 1 (-1)
2.356194490192345
> 
```


Floor, Round, Ceil 

```haskell

> map round [13.03123, 13.20, 13.50, 13.60, 13.992]
[13,13,14,14,14]
> 

> map truncate  [13.03123, 13.20, 13.50, 13.60, 13.992]
[13,13,13,13,13]
> 

> map floor [13.03123, 13.20, 13.50, 13.60, 13.992]
[13,13,13,13,13]
> 

> map ceiling [13.03123, 13.20, 13.50, 13.60, 13.992]
[14,14,14,14,14]
> 
```


Convert Interger to Float Point

```haskell
> let inv x = 1/x

> :t inv
inv :: Fractional a => a -> a
> 


> let v = [1..10]
> v
[1,2,3,4,5,6,7,8,9,10]
> :t v
v :: [Integer]
> 

> inv 10
0.1
> inv 0.1
10.0
> 

> map inv v

<interactive>:20:5:
    No instance for (Fractional Integer) arising from a use of `inv'
    Possible fix: add an instance declaration for (Fractional Integer)
    In the first argument of `map', namely `inv'
    In the expression: map inv v
    In an equation for `it': it = map inv v

> map (inv . fromInteger) v
[1.0,0.5,0.3333333333333333,0.25,0.2,0.16666666666666666,0.14285714285714285,0.125,0.1111111111111111,0.1]
> 


```

### Standard Functions

**id Identity Function**

```haskell
> :t id
id :: a -> a

> 
> id 100
100
> id "Hello World"
"Hello World"
> 
```

**Constant Function**

```haskell
> :t const
const :: a -> b -> a
> 

> let f1 = const 10
> f1 20
10
> f1 0
10
> map f1 [1, 2, 3]
[10,10,10]

``` 


### Higher Order Functions

<!--
@TODO: Add more higher order functions: zip, zip3, zip4, unzip, unzip3 .., zipWith, zipWith3 ..
-->

Higher Order functions are functions that takes functions as arguments.

Why Higher Order Function?

* Common programming idioms, such as applying a function twice, can naturally be encapsulated as general purpose higher-order functions (Hutton);

* Special purpose languages can be defined within Haskell using higher-order functions, such as for list processing, interaction, or parsing (Hutton);

* Algebraic properties of higher-order functions can be used to reason about programs. (Hutton)

Reference:
* [Graham Hutton Lecture](http://www.cs.nott.ac.uk/~gmh/functional.ppt)
* [Graham Hutton - University of Nottingham](http://www.cs.nott.ac.uk/~gmh/)


#### Map

map :: (a -> b) -> [a] -> [b]

The map functional takes a function as its first argument, then applies it to every element of a list. 
[Programming in Haskell 3rd CCSC Northwest Conference • Fall 2001](http://www.willamette.edu/~fruehr/haskell/lectures/tutorial4.html#@sli@31)

```haskell

> map (^2) [1..10]
[1,4,9,16,25,36,49,64,81,100]

> map (`div` 3) [1..20]
[0,0,1,1,1,2,2,2,3,3,3,4,4,4,5,5,5,6,6,6]

{- Map With Anonymous Functions -}
>  map (\x -> x*x - 10*x) [1..10]
[-9,-16,-21,-24,-25,-24,-21,-16,-9,0]


> map reverse ["hey", "there", "world"]
["yeh","ereht","dlrow"]

> reverse ["hey", "there", "world"]
["world","there","hey"]

```

**Example Estimating PI**

Pi number can be approximated by Gregory series. 

http://shuklan.com/haskell/lec06.html#/0/6


```
                n
              _____         k+1
              \         (-1)
            4  \      ___________
               /        2k - 1
              /____
                 1
```

```haskell

>  let f x = 4*(-1)^(x+1)/(2*k - 1) where k = fromIntegral x
>  let piGuess n = sum $ map f [1..n]
>  
>  map piGuess [1, 10, 20, 30, 50, 100]
[4.0,3.0418396189294032,3.09162380666784,3.108268566698947,3.121594652591011,3.1315929035585537]
>
>  {- Approximation Error -}
>  
>  map (pi -) $ map piGuess [1, 10, 20, 30, 50, 100]
[-0.8584073464102069,9.975303466038987e-2,4.996884692195325e-2,3.332408689084598e-2,1.999800099878213e-2,9.99975003123943e-3]


```

#### Filter

filter :: (a -> Bool) -> [a] -> [a]

Returns elements of a list that satisfy a predicate.
Predicate is boolean function which returns True or False.

```haskell

> filter even [1..10]
[2,4,6,8,10]
> 
> filter (>6) [1..20]
[7,8,9,10,11,12,13,14,15,16,17,18,19,20]
> 

```

**Example With custom types**

Credits: http://shuklan.com/haskell/lec06.html#/0/10

```haskell

> data Gender = Male | Female deriving(Show, Eq, Read)
> 
> let people = [(Male, "Tesla"), (Male, "Alber"), (Female, "Zoe"), (Male, "Tom"), (Female, "Olga"), (Female, "Mia"), (Male, "Abdulah")]

> filter (\(a, b) -> a==Female) people
[(Female,"Zoe"),(Female,"Olga"),(Female,"Mia")]
> 
> filter (\(a, b) -> a==Male) people
[(Male,"Tesla"),(Male,"Alber"),(Male,"Tom"),(Male,"Abdulah")]
> 
```


#### Higher-order predicates

Predicates (boolean-valued functions) can be extended to lists via the higher-order predicates any and all. 
[Programming in Haskell 3rd CCSC Northwest Conference • Fall 2001](http://www.willamette.edu/~fruehr/haskell/lectures/tutorial4.html#@sli@31)]

```haskell

> map even [1..5]
[False,True,False,True,False]

> all even (map (2*) [1..5])
True

> any odd [ x^2 | x<-[1..5] ]
True
```

#### Fold

The fold functions foldl and foldr combine elements of a list based on a binary function and an initial value. In some programming languages fold is known as reduce. The fold in some programming languages Python is called reduce.

"The higher-order library function foldr (“fold right”) encapsulates this simple pattern of recursion, with the function  and the value v as arguments" (Graham Hutton)

**Why Is Foldr Useful?** (Graham Hutton)

* Some recursive functions on lists, such as sum, are simpler to define using foldr;

* Properties of functions defined using foldr can be proved using algebraic properties of foldr, such as fusion and the banana split rule;

* Advanced program optimisations can be simpler if foldr is used in place of explicit recursion.

**Right Fold**

```
foldr f z [x]

    f is a function of two arguments:
    z is is the initial value of the accumulator
    [x] Is a list of values

foldr (+)  10  [1, 2, 3, 4]  =>  (+ 1 (+ 2 (+ 3 (+ 4 10)))) => 20

 
         \ f            (f 1 (f 2 (f 3 (f 4 10)))) => (+ 1 (+ 2 (+ 3 (+ 4 10))))
        / \
       1   \
           /\ f         (f 2 (f 3 (f 4 10)))
          /  \
         2    \
              /\ f      (f 3 (f 4 10))
             /  \
            3    \
                 /\ f   (f 4 10)
                /  \
               /    \
               4     \
                      z = 10
        
```

Foldr Definition:

```
foldr :: (a -> b -> b) -> b -> [a] -> b
foldr []     = v
foldr (x:xs) = x (+) foldr xs
```    

**Left Fold**

```
foldl :: (a -> b -> a) -> a -> [b] -> a

foldl (+)  10  [1, 2, 3, 4]  =>  (+ 4 (+3 (+ 2 (+ 1 10)))) => 20

          \
          /\ f             (f 4 (f 3 (f 2 (f 1 10))))
         /  \
        /    \
       4      \ f          (f 3 (f 2 (f 1 10)))
             / \ 
            /   \
           3     \ f       (f 2 (f 1 10))
                 /\   
                /  \
               2    \ f    (f 1 10)
                   / \
                  /   \
                 1     \
                        z = 10
```


Common Haskell Functions can be defined using fold

```
sum     = foldr (+) 0
product = foldr (*) 1
and     = foldr (&&) True
```


Examples:

```haskell

-- Summation from 1 to 10
> foldr (+) 0 [1..10]
55

{- Product from 1 to 10 -}
> foldr (*) 1 [1..10]
3628800
> 

{- Maximum Number in a list -}

> foldr (\x y -> if x >= y then x else y ) 0 [ -10, 100, 1000, 20, 34.23, 10]
1000.0
> 

```


Reference:
* [Graham Hutton Lecture](http://www.cs.nott.ac.uk/~gmh/functional.ppt)
* [Graham Hutton - University of Nottingham](http://www.cs.nott.ac.uk/~gmh/)


#### Scanl

Shows the intermediate values of a fold.

```haskell

{- Cumulative Sum -}
> scanl (+) 0 [1..5]
[0,1,3,6,10,15]

{- Cumulative Product -}

> scanl (*) 1 [1..5]
[1,1,2,6,24,120]

```

#### Curry and Uncurrying


**Curry**

Converts a function ((a, b) -> c) that has a single argument: a tuple of two values (a, b) to a new function that has a two arguments a and b and returns c. For short: curry converts an uncurried function to a curried function.

```
curry :: ((a, b) -> c) -> a -> b -> c 
```


**Uncurry**

Converts a function (a -> b -> c) that accepts a sequence of arguments a, b and returns c to a function that accepts a tuple of two arguments (a, b) and returns c. For short: it converts a curried function to a function on pairs.

This function and its variants are useful to map a function of multiple arguments over a list of arguments.

```
uncurry :: (a -> b -> c) -> (a, b) -> c
```   

**Example: Uncurrying a function**

```haskell
> let f x y = 10*x - y
>
> :t f
f :: Num a => a -> a -> a
> 
> 
> f 2 4
```

The problem is: how to map f over a list of pairs of a tuple of values??

```haskell
> map f [(1, 2), (4, 5), (9, 10)]

<interactive>:122:5:
    No instance for (Num (t0, t1)) arising from a use of `f'
    Possible fix: add an instance declaration for (Num (t0, t1))
    In the first argument of `map', namely `f'
```

Solution: Uncurry the function f: 

```haskell

> let f' = uncurry f
>
> :t f'
f' :: (Integer, Integer) -> Integer
>
> 
> map f' [(1, 2), (4, 5), (9, 10)]
[8,35,80]
> 
> map (uncurry f) [(1, 2), (4, 5), (9, 10)]
[8,35,80]
> 
```

**Example: Currying a function**

```haskell
> let g (x, y) = 10*x - y
> 
> :t g
g :: Num a => (a, a) -> a
> 
> g (2, 4)
16
> 
> g 2 4
<interactive>:138:1:
    No instance for (Num (a0 -> t0)) arising from a use of `g'
    Possible fix: add an instance declaration for (Num (a0 -> t0))
    In the expression: g 2 4
    In an equation for `it': it = g 2 4
    ...
> 
> let g' = curry g
> :t g'
g' :: Integer -> Integer -> Integer
> 
> g' 2 4
16
> 
> (curry g) 2 4
16
> 
```

**Other Examples**

Map a function of 3 arguments and a function of 4 arguments of over a list of tuples:

```haskell

> let uncurry3 f (a, b, c) = f a b c
> let uncurry4 f (a, b, c, d) = f a b c d
> 
> :t uncurry3
uncurry3 :: (t1 -> t2 -> t3 -> t) -> (t1, t2, t3) -> t
> 
> :t uncurry4
uncurry4 :: (t1 -> t2 -> t3 -> t4 -> t) -> (t1, t2, t3, t4) -> t
> 
> 
> let f a b c = 10*a -2*(a+c) + 5*c
> 
> 
> map (uncurry3 f) [(2, 3, 5), (4, 9, 2), (3, 7, 9)]
[31,38,51]
> 
> 

> 
> let f x y z w = 2*x + 4*y + 10*z + w
> 
> map (uncurry4 f) [(2, 3, 5, 3), (4, 9, 2, 8), (3, 7, 9, 1)]
[69,72,125]
> 
```

#### Flip 

Converts a function of two arguments a, b to a new one with argument in inverse order of the old one.

```
flip :: (a -> b -> c) -> b -> a -> c
```

Example: 

```
> let f a b = 10*a + b
> 
> :t f
f :: Num a => a -> a -> a

> 
> f 5 6
56
>
> f 6 5
65
> 
> 
> (flip f) 5 6
65
> 
```

#### Iterate

This function is useful for recursive algorithms like, root finding, numerical serie approximation, differential equation solving and finite differences.


```
iterate f x = x : iterate f (f x)
```

It creates an infinite list of iterates.

```haskell
[x, f x, f (f x), f (f (f x)), ...]
```

Example: [source](http://www2.mae.ufl.edu/haftka/numerical/Lectures/Chapter6.1-2.pdf)

Find the square root of a number by Fixed-point iteration

```
Xi+1 = g(Xi)
```

The magnitude of the derivative of g must be smaller than 1 to the method work.

```
sqrt(a) --> f(x) = x^2 - a = 0 
x  = 1/2*(a/x+x)
x  = g(x) --> g(x) = 1/2*(a/x+x)
```


```haskell
> let f a x = 0.5*(a/x + x)

> let g = f 2 -- a = 2

> g 2
1.5
> g 1.5
1.4166666666666665
> g 1.41666
1.4142156747561165
> g 1.14142156
1.4468112805021982

{- OR -}

> let gen = iterate g 2
>
> take 5 gen
[2.0,1.5,1.4166666666666665,1.4142156862745097,1.4142135623746899]

{-- 
Finally the root algorithm  using the power of lazy evaluation
with the iterate function

--}

> let f a x = 0.5*(a/x + x)
> let root a =  last $ take 10 $ iterate (f a) a 
> 
> root 2
1.414213562373095
> root 2 - sqrt 2
-2.220446049250313e-16
> 
> root 10
3.162277660168379
> sqrt 10
3.1622776601683795
>
> root 10 - sqrt 10
-4.440892098500626e-16
> 
> 

```

#### takeWhile

Apply a predicate p to a list xs and returns the longest prefix, that can be empty of xs of elements that satisfy the predicate.

```haskell
> :t takeWhile
takeWhile :: (a -> Bool) -> [a] -> [a]
> 

{- Constant Function that always returns True-}
> :t const True
const True :: b -> Bool
> 
> takeWhile (const True)  [10, 20, 8, 4, 5, 7, 9] 
[10,20,8,4,5,7,9]
> 

> takeWhile (const False)  [10, 20, 8, 4, 5, 7, 9] 
[]
> 

> takeWhile (>5) [10, 20, 8, 4, 5, 7, 9] 
[10,20,8]
> 

> takeWhile (<10) [1, 2, 3, 9, 10, 20, 30]
[1,2,3,9]
> 

> takeWhile (/='a') "testing a function"
"testing "
> 


```

#### dropWhile

The function dropWhile apply a predicate p to a list xs and returns the suffix remaining after takeWhile.

Example:

```haskell
> :t dropWhile
dropWhile :: (a -> Bool) -> [a] -> [a]
> 

> dropWhile (const True) [10, 20, 8, 4, 5, 7, 9] 
[]

> dropWhile (const False) [10, 20, 8, 4, 5, 7, 9] 
[10,20,8,4,5,7,9]

> dropWhile (>5) [10, 20, 8, 4, 5, 7, 9]
[4,5,7,9]

> dropWhile (/='a') "testing a function"
"a function"
> 

```

#### Zip and Unzip

Zip takes two lists and returns a list of corresponding pairs. If one input list is short, excess elements of the longer list are discarded. 

```haskell
zip :: [a] -> [b] -> [(a, b)]
zip3 :: [a] -> [b] -> [c] -> [(a, b, c)]
```

Data.List

```haskell
zip4 :: [a] -> [b] -> [c] -> [d] -> [(a, b, c, d)]
zip5 :: [a] -> [b] -> [c] -> [d] -> [e] -> [(a, b, c, d, e)]
zip6  :: [a] -> [b] -> [c] -> [d] -> [e] -> [f] -> [(a, b, c, d, e, f)]
```

Unzip transforms a list of pairs into a list of first components and a list of second components. It is the inverse of zip.

```haskell
unzip :: [(a, b)] -> ([a], [b])
unzip3 :: [(a, b, c)] -> ([a], [b], [c])
```

Data.List
```
unzip4 :: [(a, b, c, d)] -> ([a], [b], [c], [d])
unzip5 :: [(a, b, c, d, e)] -> ([a], [b], [c], [d], [e])
unzip6 :: [(a, b, c, d, e, f)] -> ([a], [b], [c], [d], [e], [f])
```

Examples: Zip

```haskell
> zip [1, 3, 4, 5, 6] [10, 30, 40, 50, 60]
[(1,10),(3,30),(4,40),(5,50),(6,60)]
> 

> zip [1, 3, 4, 5, 6] [10, 30, 40]
[(1,10),(3,30),(4,40)]
> 

> zip [5, 6] [10, 30, 40, 50, 60]
[(5,10),(6,30)]
> 

> zip [1, 2, 3, 4, 5] ['a', 'b', 'c', 'd', 'e']
[(1,'a'),(2,'b'),(3,'c'),(4,'d'),(5,'e')]
> 

> zip ["haskell", "ocaml", "sml", "scala", "erlang"] ['a', 'b', 'c', 'd', 'e']
[("haskell",'a'),("ocaml",'b'),("sml",'c'),("scala",'d'),("erlang",'e')]
> 

> zip3 [1, 2, 3, 4, 5] ['a', 'b', 'c', 'd', 'e'] ["haskell", "ocaml", "sml", "scala", "erlang"]
[(1,'a',"haskell"),(2,'b',"ocaml"),(3,'c',"sml"),(4,'d',"scala"),(5,'e',"erlang")]
> 

> zip3 [1, 2, 3, 4, 5] ['a', 'b', 'c', 'd', 'e'] ["haskell", "ocaml", "sml", "scala"]
[(1,'a',"haskell"),(2,'b',"ocaml"),(3,'c',"sml"),(4,'d',"scala")]
> 

> zip3 [4, 5] ['a', 'b', 'c', 'd', 'e'] ["haskell", "ocaml", "sml", "scala"]
[(4,'a',"haskell"),(5,'b',"ocaml")]
> 
> 

> import Data.List
> 
> zip4 [1..5] [5..15] ['a'..'z'] (replicate 4 Nothing)
[(1,5,'a',Nothing),(2,6,'b',Nothing),(3,7,'c',Nothing),(4,8,'d',Nothing)]
> 
```

Example: Unzip

```haskell
> unzip [(1,10),(3,30),(4,40),(5,50),(6,60)]
([1,3,4,5,6],[10,30,40,50,60])
> 

> unzip [(1,'a'),(2,'b'),(3,'c'),(4,'d'),(5,'e')]
([1,2,3,4,5],"abcde")
> 

> import Data.List

> unzip3 [(1,'a',"haskell"),(2,'b',"ocaml"),(3,'c',"sml"),(4,'d',"scala")]
([1,2,3,4],"abcd",["haskell","ocaml","sml","scala"])
> 

> unzip4 [(1,5,'a',Nothing),(2,6,'b',Nothing),(3,7,'c',Nothing),(4,8,'d',Nothing)]
([1,2,3,4],[5,6,7,8],"abcd",[Nothing,Nothing,Nothing,Nothing])
> 

> let (x, y) = unzip [(1,'a'),(2,'b'),(3,'c'),(4,'d'),(5,'e')]
> x
[1,2,3,4,5]
> y
"abcde"
> 

> let (a, b, c) = unzip3 [(1,'a',"haskell"),(2,'b',"ocaml"),(3,'c',"sml"),(4,'d',"scala")]
> a
[1,2,3,4]
> b
"abcd"
> c
["haskell","ocaml","sml","scala"]
> 

```


#### ZipWith 

ZipWith function applies a function of two arguments to each elements of two given lists returning a new list.

Defined in Prelude

```haskell
zipWith :: (a -> b -> c) -> [a] -> [b] -> [c]
zipWith3 :: (a -> b -> c -> d) -> [a] -> [b] -> [c] -> [d]
```

Defined in Data.List

```haskell
import Data.List
zipWith4   :: (a -> b -> c -> d -> e) -> [a] -> [b] -> [c] -> [d] -> [e]
zipWith5   :: (a -> b -> c -> d -> e -> f) -> [a] -> [b] -> [c] -> [d] -> [e] -> [f]
zipWith7   :: (a -> b -> c -> d -> e -> f -> g -> h) -> [a] -> [b] -> [c] -> [d] -> [e] -> [f] -> [g] -> [h]
```

Examples:

```haskell

{- 

ZipWith takes a function of two arguments and two lists 
returning a new one

    ->  (a -> b -> c)   : Function of two arguments returning type c
    ->  [a]            :  List of type a
    ->  [b]            :  List of type b
    
    Returns 
    ->  [c]            :  List of type c
-}
> :t zipWith
zipWith :: (a -> b -> c) -> [a] -> [b] -> [c]
> 

> :t (+)
(+) :: Num a => a -> a -> a
> 


{- Add each element of two lists -}
> zipWith (+) [1, 2, 3, 4] [9, 10, 3, 5]
[10,12,6,9]
> 
> 

{- Multiply each element of two lists-}
> zipWith (*) [1, 2, 3, 4] [9, 10, 3, 5]
[9,20,9,20]
> 

{- Subtract each element of two lists -}
> zipWith (-) [1, 2, 3, 4] [9, 10, 3, 5]
[-8,-8,0,-1]
> 

{- zipWith with anonymous functions -}

> zipWith (\x y -> 10*x + 4*y) [10, 20, 30] [3, 4, 5]
[112,216,320]
> 
> let f = zipWith (\x y -> 10*x + 4*y)
> 
> f [10, 20, 30] [3, 4, 5]
[112,216,320]
> 


{- New functions can be created by curring arguments -}

> let addVectors = zipWith (+)
> let subVectors = zipWith (-)
> let mulVectors = zipWith (*)
> 
> :t addVectors 
addVectors :: [Integer] -> [Integer] -> [Integer]
> :t subVectors 
subVectors :: [Integer] -> [Integer] -> [Integer]
> :t mulVectors 
mulVectors :: [Integer] -> [Integer] -> [Integer]
> 

> addVectors [1, 2, 3, 4] [9, 10, 3, 5]
[10,12,6,9]
> 
> subVectors [1, 2, 3, 4] [9, 10, 3, 5]
[-8,-8,0,-1]
> mulVectors [1, 2, 3, 4] [9, 10, 3, 5]
[9,20,9,20]
> 

{- Using Functions as operators -}

> [1, 2, 3, 4]  `addVectors` [9, 10, 3, 5]
[10,12,6,9]
> 
> 
> [1, 2, 3, 4]  `subVectors` [9, 10, 3, 5]
[-8,-8,0,-1]
> 
> [1, 2, 3, 4]  `mulVectors` [9, 10, 3, 5]
[9,20,9,20]
> 

> let f x y z = x*y*z 

> zipWith3 f [1, 3, 4, 8] [4, 5, 9] [8, 7, 3]
[32,105,108]
> 
> let zf = zipWith3 f
> 
> zf [1, 3, 4, 8] [4, 5, 9] [8, 7, 3]
[32,105,108]
> 

> import Data.List
> 
> zipWith4 g [12, 34, 1, 4] [8, 19, 33, 23] [5, 7, 8, 9] [33, 78, 17, 14]
[337,2371,-1277,-929]
> 

> let g1 = zipWith4 g [12, 34, 1, 4] 
> g1 [8, 19, 33, 23] [5, 7, 8, 9] [33, 78, 17, 14]
[337,2371,-1277,-929]

> let g2 = g1 [8, 19, 33, 23]
> g2 [5, 7, 8, 9] [33, 78, 17, 14]
[337,2371,-1277,-929]

> let g3 = g2 [5, 7, 8, 9]
> g3  [33, 78, 17, 14]
[337,2371,-1277,-929]

> let g4 = g3 [33, 78, 17, 14]
> g4
[337,2371,-1277,-929]
> 

``` 


#### Replicate

Replicate an element of type a n times.
```
replicate :: Int -> a -> [a]
```

Example:
```haskell
> :t replicate 
replicate :: Int -> a -> [a]
> 

> replicate 4 'a'
"aaaa"
> replicate 6 2.345
[2.345,2.345,2.345,2.345,2.345,2.345]
> 

{- You can also replicate functions -}
> let f = replicate 3 (+1)
> :t f
f :: [Integer -> Integer]
> 
> map ($ 5) f
[6,6,6]
> 

> replicate 3 (Just 5)
[Just 5,Just 5,Just 5]
> 
> replicate 3 Nothing
[Nothing,Nothing,Nothing]
> 

```

#### Other Useful higher-order functions

The standard Prelude defines scores of useful functions, many of which enjoy great generality due to the abstractional capabilities of polymorphic 
types and higher-order functions [[Programming in Haskell 3rd CCSC Northwest Conference • Fall 2001](http://www.willamette.edu/~fruehr/haskell/lectures/tutorial4.html#@sli@31)]


```haskell
> zipWith (*) [1..10] [1..10]
[1,4,9,16,25,36,49,64,81,100]

> :t replicate
replicate :: Int -> a -> [a]

> zipWith replicate [1..6] ['a'..'z']
["a","bb","ccc","dddd","eeeee","ffffff"]

> takeWhile (<100) [ 2^n | n<-[1..] ]
[2,4,8,16,32,64]

> :t takeWhile
takeWhile :: (a -> Bool) -> [a] -> [a]
```


### Functions to Manipulate Characters and Strings

#### Strings Features

**Strings as List of Characters**

```
> 
> ['(', ')', '!', 'a', 'b', 'c', '0', '1']
"()!abc01"
> 
```


**Character Sequences**

```haskell
> ['a'..'z']
"abcdefghijklmnopqrstuvwxyz"

> ['A'..'Z']
"ABCDEFGHIJKLMNOPQRSTUVWXYZ"

> ['0'..'9']
"0123456789"
> 

> ['0'..'z']
"0123456789:;<=>?@ABCDEFGHIJKLMNOPQRSTUVWXYZ[\\]^_`abcdefghijklmnopqrstuvwxyz"

```

**Add a character to a string**

```haskell

> "adding " ++ "three" ++ " strings"
"adding three strings"
> 

> "Hello world " ++ ['1']
"Hello world 1"
> 

> 'x' : "Hello World"
"xHello World"
> 
> 'y' : 'x' : "Hello World"
"yxHello World"
> 

```

#### Prelude String Functions

**lines**

Lines breaks a string up into a list of strings at newline characters. The resulting strings do not contain newlines.


```
lines :: String -> [String] 
```

```haskell
> let text = "Hello World\nHaskell\n Is very Cool"
> text
"Hello World\nHaskell\n Is very Cool"


> putStrLn text
Hello World
Haskell
 Is very Cool
> 
> 

> lines text
["Hello World","Haskell"," Is very Cool"]
> 
```

**unlines**

Unlines is an inverse operation to lines. It joins lines, after appending a terminating newline to each.

```
unlines :: [String] -> String 
```

```haskell
> unlines ["Hello World","Haskell"," Is very Cool"]
"Hello World\nHaskell\n Is very Cool\n"
> 
> putStrLn $ unlines ["Hello World","Haskell"," Is very Cool"]
Hello World
Haskell
 Is very Cool

>
```

**words**

Words breaks a string up into a list of words, which were delimited by white space.

```
words :: String -> [String] 
```

```haskell
> words "Hello world haskell 123 2312 --- "
["Hello","world","haskell","123","2312","---"]
> 
```

**unwords**

unwords is an inverse operation to words. It joins words with separating spaces.

```
unwords :: [String] -> String 
```

```haskell
> unwords ["Hello","world","haskell","123","2312","---"]
"Hello world haskell 123 2312 ---"
> 
```

**reverse**

Reverse a string. 

```haskell
> reverse "lleksaH dlroW olleH"
"Hello World Haskell"
> 
```

#### Data.Char String Functions

Documentation: https://hackage.haskell.org/package/base-4.2.0.1/docs/Data-Char.html

```haskell
import Data.Char

> ['0'..'z']
"0123456789:;<=>?@ABCDEFGHIJKLMNOPQRSTUVWXYZ[\\]^_`abcdefghijklmnopqrstuvwxyz"
> 

> filter isDigit  ['0'..'z']
"0123456789"
> 

> filter isAlpha ['0'..'z']
"ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz"
> 

> filter isLower ['0'..'z']
"abcdefghijklmnopqrstuvwxyz"
> 
> filter isUpper ['0'..'z']
"ABCDEFGHIJKLMNOPQRSTUVWXYZ"
> 
> 

> filter isHexDigit ['0'..'z']
"0123456789ABCDEFabcdef"
> 

> filter isAlphaNum ['0'..'z']
"0123456789ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz"
> 

> map toUpper ['a'..'z']
"ABCDEFGHIJKLMNOPQRSTUVWXYZ"
>

> map toLower ['A'..'Z']
"abcdefghijklmnopqrstuvwxyz"
> 

{- Convert to ascii decimal number -}
> map ord ['a'..'f']
[97,98,99,100,101,102]
> 


{- Convert ascii to char -}
> map chr [97,98,99,100,101,102]
"abcdef"
> 
```


#### Data.List.Split String Functions

The Data.List.Split module contains a wide range of strategies for splitting lists with respect to some sort of delimiter, mostly implemented through a unified combinator interface. The goal is to be flexible yet simple.

Documentation: http://hackage.haskell.org/package/split-0.1.4.1/docs/Data-List-Split.html

```haskell
> import Data.List.Split
> 

> splitOn "," "1232,2323.232,323.434"
["1232","2323.232","323.434"]
> 
> 

> map (\s -> read s :: Double) $ splitOn "," "1232,2323.232,323.434"
[1232.0,2323.232,323.434]
> 
> 

> endBy "," "1232,2323.232,323.434,"
["1232","2323.232","323.434"]
> 
> 

>  splitOneOf ";.," "foo,bar;baz.glurk"
["foo","bar","baz","glurk"]
> 

> chunksOf  3 ['a'..'z']
["abc","def","ghi","jkl","mno","pqr","stu","vwx","yz"]
> 
> 

```

### Useful notations for functions 

Credits: http://yannesposito.com/Scratch/en/blog/Haskell-the-Hard-Way/

```
x :: Int            ⇔ x is of type Int
x :: a              ⇔ x can be of any type
x :: Num a => a     ⇔ x can be any type a
                      such that a belongs to Num type class 
f :: a -> b         ⇔ f is a function from a to b
f :: a -> b -> c    ⇔ f is a function from a to (b→c)
f :: (a -> b) -> c  ⇔ f is a function from (a→b) to c
```



## Pattern Matching

Tuple Constructor

```haskell

> let norm3D (x, y, z) = sqrt(x^2 + y^2 + z^2)
> 
> norm3D (33, 11, 3)
34.91418050019218
> 
> norm3D (33, 1, 3)
33.15116890850155
> 
```

```haskell

addVectors :: (Num a) => (a, a) -> (a, a) -> (a, a)
addVectors a b = (fst a + fst b, snd a + snd b)

> addVectors (8, 9)(-10, 12)
(-2,21)
> 
> addv1 = addVectors (1, 3)
> 
> let addv1 = addVectors (1, 3)
> 
> map addv1 [(12, 23), (45, 23), (6, 14)]
[(13,26),(46,26),(7,17)]
```

```haskell

add3Dvectors (x1, y1, z1) (x2, y2, z2) = (x1+x2, y1+y2, z1+z
first  (x, _, _) = x
second (_, y, _) = y
third  (_, _, z) = z

> first (1, 2, 3)
1
> second  (1, 2, 3)
2
> third (1, 2, 3)
3   
> add3Dvectors (23, 12, 233) (10, 100, 30)
(33,112,263)
```

**Guarded Equations**

Absolute Value

```haskell
abs n | n >=0 = n
      | otherwise = -n
```

Signum/Sign Function

```haskell

-- Without Pattern Matching
sign n = if n < 0 then - 1 else if n == 0 then 0 else 1


sign x | x >  0 =  1
       | x == 0 =  0 
       | x <  0 = -1

----------- OR -----


sign n | n <  0    = -1
       | n == 0    = 0
       | otherwise = 1


--------------------

> let sign x | x > 0 = 1 | x == 0 = 0 | x < 0 = -1


> map sign [-4..4]
[-1,-1,-1,-1,0,1,1,1,1]

```

```haskell
f x y | y > z  = x^^2 - 10.5
      | y == z = x+10*y
      | y < z  = x/z + y
      where z = x^2 - 5*y

```

```haskell

units angle sym | sym == "deg" = angle*pi/180.0
                | sym == "rad" = angle

> :{
| let units angle sym | sym == "deg" = angle*pi/180.0
|                 | sym == "rad" = angle
| 
| :}
> 
> units 180 "deg"
3.141592653589793
> 
> units pi "rad"
3.141592653589793
> 
> units 90 "deg" == pi/2
True
> 
> sin(units 90 "deg")
1.0
> sin(units 1.57 "rad")
0.9999996829318346
> 
```

```haskell

password :: (Eq a, Num a) => a -> [Char]
password 3423 = "OK - Safe opened"
password x    = "Error: Wrong Password pal"

> password 10
"Error: Wrong Password pal"
> password 11
"Error: Wrong Password pal"
> password 3423
"OK - Safe opened"
> s
```

```haskell
sayMe :: (Integral a) => a -> [Char]
sayMe 1 = "One!"  
sayMe 2 = "Two!"  
sayMe 3 = "Three!"  
sayMe 4 = "Four!"  
sayMe 5 = "Five!"  
sayMe x = "Not between 1 and 5" 

> map sayMe [1..8]
["One!","Two!","Three!","Four!","Five!","Not between 1 and 5", "Not between 1 and 5","Not between 1 and 5"]


```

## List Comprehension

### Simple List Comprehension

```haskell 
> [x^2 | x <- [1..10]]
[1,4,9,16,25,36,49,64,81,100]

>  [ odd x | x <- [1..9]] 
[True,False,True,False,True,False,True,False,True]

```

### Comprehensions with multiple generators

Comprehensions with multiple generators, separated by commas.
The generators are x <- [1, 2, 4] and y <- [4,5].

```haskell
> [(x, y) | x <- [1, 2, 4], y <- [4,5]]
[(1,4),(1,5),(2,4),(2,5),(4,4),(4,5)]

> [(x-y, x+y) | x <- [1, 2, 4], y <- [4,5]]
[(-3,5),(-4,6),(-2,6),(-3,7),(0,8),(-1,9)]

> [(x/y, x*y) | x <- [1, 2, 4], y <- [4,5]]
[(0.25,4.0),(0.2,5.0),(0.5,8.0),(0.4,10.0),(1.0,16.0),(0.8,20.0)]
```

### Function Inside List Comprehension

```haskell

> let f x y = sqrt(x^2 + y^2)

> [ f x y | x <- [1, 2, 4], y <- [4,5]]
[4.123105625617661,5.0990195135927845,4.47213595499958,5.385164807134504,5.656854249492381,6.4031242374328485]

```

### Comprehension with Guards

Guards or filter is a boolean expression that removes elements that would 
otherwise have been included in the list comprehension. They restricts the values 
produced by earlier generators.

Even number sequence

```haskell

> [x | x <- [1..10], even x]
[2,4,6,8,10]

>  [x | x <- [1,5,12,3,23,11,7,2], x>10] 
[12,23,11]

> [(x,y) | x <- [1,3,5], y <- [2,4,6], x<y]
[(1,2),(1,4),(1,6),(3,4),(3,6),(5,6)]


```

Odd Number sequence

```haskell

> [x | x <- [1..10], odd x]
[1,3,5,7,9]
```


Number factors and Prime Numbers

```haskell

> let factors n = [ x | x <- [1..n], mod n x == 0]
> 
> factors 15
[1,3,5,15]
> 
> factors 10
[1,2,5,10]
> 
> factors 100
[1,2,4,5,10,20,25,50,100]
> 
> factors 17
[1,17]
> factors 19
[1,19]

> let prime n = factors n == [1, n]
> 
> prime 17
True
> prime 19
True
> prime 20
False
> 

{- Get all prime numbers until number n -}

> let primes_n n = [ x | x <- [1..n], prime x]
> 
> primes_n 10
[2,3,5,7]
> primes_n 100
[2,3,5,7,11,13,17,19,23,29,31,37,41,43,47,53,59,61,67,71,73,79,83,89,97]
> 

```




## Abstract Data Type

**Example: Days of Week**

Enumerated sets is type which can only have a limited number of values. 


```haskell

data Weekday = Monday
             | Tuesday
             | Wednesday
             | Thursday
             | Friday
             | Saturday
             | Sunday
  deriving (Eq, Ord, Enum)

fromDay :: Weekday -> Int
fromDay = fromEnum

toDay :: Int -> Weekday
toDay = toEnum   

> map (Monday<) [ Tuesday, Friday, Sunday]
[True,True,True]

> map (Thursday<) [Monday, Tuesday, Friday, Sunday]
[False,False,True,True]

> 
> Monday == Tuesday
False
> Tuesday == Tuesday
True
>  

> 
> fromDay Saturday 
5

> 1 + fromDay Monday 
1
> 1 + fromDay Saturday 
6
> Saturday 
Saturday
> 
> toDay 0
Monday
> toDay 6
Sunday
> 
> 


```

**Example: Colors**

```haskell

data Color
    = Red
    | Orange
    | Yellow
    | Green
    | Blue
    | Purple
    | White
    | Black
    | CustomColor Int Int Int -- R G B components
    deriving (Eq)

colorToRGB Red    = (255,0,0)
colorToRGB Orange = (255,128,0)
colorToRGB Yellow = (255,255,0)
colorToRGB Green  = (0,255,0)
colorToRGB Blue   = (0,0,255)
colorToRGB Purple = (255,0,255)
colorToRGB White = (255,255,255)
colorToRGB Black = (0,0,0)
colorToRGB (CustomColor r g b) = (r,g,b)   -- this one is new
 
    
> 
> Red == White
False
> 
> Red == Red
True
> 

> let b = CustomColor 120 240 100
> colorToRGB b
(120,240,100)

> map colorToRGB [ Blue, White, Yellow ]
[(0,0,255),(255,255,255),(255,255,0)]
> 


```

**Example: Shapes**

```haskell

data Shape = Circle  Float 
            | Rect   Float Float 

square   :: Float -> Shape
square n =  Rect n n 

area            :: Shape -> Float
area (Circle r)  = pi * r^2
area (Rect x y)  = x  * y

*Main> area $  Rect 20 30
600.0
*Main> area $ Circle 20
1256.6371
*Main> area $ square 20
400.0
*Main> 


```

**Example: Students GPA**

```haskell

data Student = USU String Float 
             deriving (Show)

get_gpa :: Student -> Float
get_gpa (USU _ grade) = grade

get_name :: Student -> String
get_name (USU name _ ) = name

class_gpa :: [Student] -> Float
class_gpa myclass = (sum c) / fromIntegral  (length c)
                  where 
                  c = map get_gpa myclass


*Main> let myke = USU "Mike" 4.0
*Main> 
*Main> get_name myke
"Mike"
*Main> get_gpa myke
4.0
*Main> 

*Main> let myclass = [USU "Mike" 3.7, USU "Steve" 3.9, USU "Fred" 2.9, USU "Joe" 1.5]
*Main> 

*Main> class_gpa myclass 
3.0
*Main

```

**Example: Typeclass with record Syntax**

```haskell

data Person = Person { firstName :: String, 
                       lastName :: String, 
                       age :: Int 
                     }
                     deriving (Eq, Show, Read)


people = [ Person { firstName = "Ayn",  lastName = "Rand",  age =50},
           Person { firstName = "John", lastName = "Galt",  age =28},
           Person { firstName = "Adam", lastName = "Smith", age =70}]


{- Get someone from the people database -}
getPerson n = people !! n

{- Show Person -}
showPerson :: Person -> String
showPerson person  = "Name: " ++ show(firstName person) ++ " - Last Name: " ++ show(lastName person) ++ " - Age " ++ show(age person) 

> people
[Person {firstName = "Ayn", lastName = "Rand", age = 50},Person {firstName = "John", lastName = "Galt", age = 28},Person {firstName = "Adam", lastName = "Smith", age = 70}]
> 

> map firstName people
["Ayn","John","Adam"]
> 

> map (\el ->  fst el ++ " " ++  snd el) $ zip (map firstName people) (map lastName people)
>  ["Ayn Rand","John Galt","Adam Smith"]


> people !! 1
Person {firstName = "John", lastName = "Galt", age = 28}
> people !! 2
Person {firstName = "Adam", lastName = "Smith", age = 70}
> 

> "person 0 is " ++ show (people !! 0)
"person 0 is Person {firstName = \"Ayn\", lastName = \"Rand\", age = 50}"
> 
> "person 1 is " ++ show (people !! 1)
"person 1 is Person {firstName = \"John\", lastName = \"Galt\", age = 28}"
>


> let person = read "Person {firstName =\"Elmo\", lastName =\"NA\", age = 0}" :: Person
> person
Person {firstName = "Elmo", lastName = "NA", age = 0}
> 
> firstName person 
"Elmo"
> last
last      lastName
> lastName person 
"NA"
> age person
0
> 

> let tesla = Person { firstName = "Nikola", lastName = "Tesla", age =30}
> tesla
Person {firstName = "Nikola", lastName = "Tesla", age = 30}
> 

> showPerson tesla
"Name: \"Nikola\" - Last Name: \"Tesla\" - Age 30"
> 

```

Reference: 
    * http://learnyouahaskell.com/making-our-own-types-and-typeclasses


## Functors, Monads, Applicatives and Monoids

The concepts of functors, monads and applicatives comes from [category theory](http://en.wikipedia.org/wiki/Category_theory).

### Functors

Functors is a prelude class for types which the function fmap is defined. The function fmap is a generalization of map function.

```haskell
class  Functor f  where
    fmap        :: (a -> b) -> f a -> f b
```

* f is a parameterized data type
* (a -> b ) Is a polymorphic function that takes a as parameter and returns b
* f a : a is a parameter, f wraps a
* f b : b is a parameter wrapped by f

A functor must satisfy the following operations (aka functor laws):

```haskell

-- id is the identity function:
id :: a -> a
id x = x

fmap (f . g) = fmap f . fmap g  -- Composition law
fmap id = id                    -- Identity law
```

The following functors defined in Haskell standard library prelude.hs. The function fmap is defined for each of the functor types.

**List**

```haskell
instance Functor [] where
    fmap = map
```

**Maybe**

```haskell

data Maybe x = Nothing | Just x

instance  Functor Maybe  where
    fmap f Nothing    =  Nothing
    fmap f (Just x)   =  Just (f x)
```

**Either**

```haskell

data Either c d = Left c | Right d

instance Functor (Either a) where
    fmap f (Left a) = Left a
    fmap f (Right b) = Right (f b)
```

**IO**

```haskell
instance  Functor IO where
   fmap f x           =  x >>= (return . f)
```

Examples:

The most well known functor is the list functor:

```haskell
> let f x  = 10*x -2
> fmap f [1, 2, 3, 10]
[8,18,28,98]
> 
> fmap f (fmap f [1, 2, 3, 10])
[78,178,278,978]
> 
```

The Maybe type is a functor which the return value is non deterministic that returns a value if the computation is successful or return a null value Nothing if the computation fails. It is useful to avoid boilerplate successive null checkings and avoid null checking error.

```haskell
> 
> let add10 x = x + 10
> 
> 
> fmap add10 Nothing
Nothing
> 
> 
> 
> fmap add10 $ fmap add10 Nothing
Nothing
> 
> 
> fmap add10 (Just 10)
Just 20
> 
> 
> fmap add10 $ fmap add10 (Just 10)
Just 30
> 
> 
```

**Functor Laws Testing**


```haskell

-- fmap id == id

> fmap id [1, 2, 3] == id [1, 2, 3]
True
> 
> 
> let testLaw_id functor = fmap id functor == id functor
> testLaw_id [1, 2, 3]
True
> testLaw_id []
True
> 

-- Testing for Maybe functor
> testLaw_id Nothing
True
> testLaw_id (Just 10)
True
> 
> 

-- Composition Testing
-- fmap (f . g) = fmap f . fmap g  -- Composition law
> let f x = x + 1
> let g x = 2*x
> 

> 
> fmap (f . g)  [1, 2, 3]
[3,5,7]
> 
> 
> :t (fmap f)
(fmap f) :: (Functor f, Num b) => f b -> f b
> 
> 
> fmap (f . g)  [1, 2, 3] ==  ((fmap f) . (fmap g)) [1, 2, 3]
True
> 

> 
> let test_fcomp f g functor = fmap (f . g) functor ==  ((fmap f) . (fmap g)) functor
> 
> test_fcomp f g (Just 10)
True
> 
> test_fcomp f g Nothing
True
> 
>
```


To list all instances of the Functor class:

```haskell
> 
> :i Functor
class Functor f where
  fmap :: (a -> b) -> f a -> f b
  (<$) :: a -> f b -> f a
    -- Defined in `GHC.Base'
instance Functor (Either a) -- Defined in `Data.Either'
instance Functor Maybe -- Defined in `Data.Maybe'
instance Functor ZipList -- Defined in `Control.Applicative'
instance Monad m => Functor (WrappedMonad m)
  -- Defined in `Control.Applicative'
instance Functor (Const m) -- Defined in `Control.Applicative'
instance Functor [] -- Defined in `GHC.Base'
instance Functor IO -- Defined in `GHC.Base'
instance Functor ((->) r) -- Defined in `GHC.Base'
instance Functor ((,) a) -- Defined in `GHC.Base'

```

References:

* [The Functor Design Pattern](http://www.haskellforall.com/2012/09/the-functor-design-pattern.html)
* http://en.wikibooks.org/wiki/Haskell/Applicative_Functors
* http://comonad.com/reader/2008/deriving-strength-from-laziness/

### Monads

<!--
@TODO: Add State Monad section. 
@TODO: Add Writer Monad
@TODO: Add Reader Monad
-->

#### Overview

Monads in Haskell are used to perform IO, State, Parallelism, Exception Handling, parallelism, continuations and coroutines.

Most common applications of monads include:

* Representing failure and avoiding null checking using Maybe or Either monad 
* Nondeterminism using List monad to represent carrying multiple values
* State using State monad
* Read-only environment using Reader monad
* I/O using IO monad

A monad is defined by three things:

* a type constructor m that wraps a, parameter a;
* a return  operation: takes a value from a plain type and puts it into a monadic container using the constructor, creating a monadic value. The return operator must not be confused with the "return" from a function in a imperative language. This operator is also known as unit, lift, pure and point. It is a polymorphic constructor.
* a bind operator (>>=). It takes as its arguments a monadic value and a function from a plain type to a monadic value, and returns a new monadic value.

* A monadic function is a function which returns a Monad (a -> m b)

* Return/unit:     return :: Monad m => a -> m a
* Bind:            (>>=)  :: (Monad m) => m a -> (a -> m b) -> m b

A type class is an interface which is a set of functions and type signatures. Each type derived from a type class must implement the functions described with the same type signatures and same name as described in the interface/type class. It is similar to a Java interface.

In Haskell, the Monad type class is used to implement monads. It is provided by the Control.Monad module which is included in the Prelude. The class has the following methods:


```haskell

class Monad m where
    return :: a -> m a      -- Constructor (aka unit, lift) 
                            --Not a keyword, but a unfortunate and misleading name.
    (>>=)  :: m a -> (a -> m b) -> m b   -- Bind operator
    (>>)   :: m a -> m b -> m b
    fail   :: String -> m a
        
```

**Some Haskell Monads**

* IO Monads         - Used for output IO
* Maybe and Either  - Error handling and avoinding null checking
* List Monad        - One of the most widely known monads
* Writer Monad
* Reader Monad
* State Monad
 



#### Bind Operator

In a imperative language the bind operator could be described as below:
```
-- Operator (>>=)

func: Is a monadic function ->
    func :: a -> m b
        
    In Haskell:
        m a >>= func     == m b
    
    In a Imperative Language        
        bind (m a, func) == m b        

    In a Object Orientated language:
        (m a).bind( func) == m b
```

#### Monad Laws

All monads must satisfy the monadic laws:

In Haskell, all instances of the Monad type class (and thus all implementations of (>>=) and return) must obey the following three laws below:

Left identity:
```
Haskell
    m >>= return =  m       

Imperative Language Equivalent
    bind (m a, unit) == m a -- unit instead of return

Object Orientated Equivalent
    (m a).bind(unit) == m a
```

Left unit
```
Haskell
    return x >>= f  ==  f x 

Imperative Language Equivalent
    bind(unit x, f) ==  f x -- f x  == m a

Object Orientated Equivalent
    (unit x).bind(f) == f x
```

Associativity
```
Haskell
    (m >>= f) >>= g  =  m >>= (\x -> f x >>= g)  

Imperative Language Equivalent
    bind(bind(m a, f), g) == bind(m a, (\x -> bind(f x, g)))

Object Orientated Equivalent
    (m a).bind(f).bind(g) == (m a).bind(\x -> (f x).bind(g))
```

Nice Version.

```haskell
1. return >=> f       ==    f
2. f >=> return       ==    f
3. (f >=> g) >=> h    ==    f >=> (g >=> h)
```

Credits: http://mvanier.livejournal.com/4586.html

#### Selected Monad Implementations

**List Monad**

```haskell
instance  Monad []  where
    m >>= k          = concat (map k m)
    return x         = [x]
    fail s           = []
```

**Maybe Monad**

```haskell
data Maybe a = Nothing | Just a

instance Monad Maybe where
  Just a  >>= f = f a
  Nothing >>= _ = Nothing
  return a      = Just a
```

```haskell
(>>=) :: Maybe a -> (a -> Maybe b) -> Maybe b
return :: a -> Maybe a
```

**IO Monad**

```haskell
(>>=) :: IO a -> (a -> IO b) -> IO b
return :: a -> IO b
```


#### Return - Type constructor

Return is polymorphic type constructor. This name return is misleading, it has nothing to do with the return from a function in a imperative language.

Examples:

```haskell

> :t return
return :: Monad m => a -> m a
> 

> return 223.23 :: (Maybe Double)
Just 223.23
> 
> 
> return Nothing
Nothing
> 

> return "el toro" :: (Either String  String)
Right "el toro"
> 
> 

> 
> return "Nichola Tesla" :: (IO String)
"Nichola Tesla"
> 
> 
```

#### Haskell Monads

![](images/monadTable.png)

From: https://wiki.haskell.org/All_About_Monads#What_is_a_monad.3F



Under this interpretation, the functions behave as follows:

* fmap applies a given function to every element in a container
* return packages an element into a container,
* join takes a container of containers and flattens it into a single container.

```haskell

    fmap   :: (a -> b) -> M a -> M b  -- functor
    return :: a -> M a
    join   :: M (M a) -> M a
    
```

#### Monad function composition

```
(>=>) :: Monad m => (a -> m b) -> (b -> m c) -> a -> m c
```

[Under Construction]

```

return :: Monad m => a -> m a

{- Bind Operator -}
(>>=) :: (Monad m) => m a -> (a -> m b) -> m b

sequence  :: Monad m => [m a] -> m [a] 
sequence_ :: Monad m => [m a] -> m () 
mapM      :: Monad m => (a -> m b) -> [a] -> m [b]
mapM_     :: Monad m => (a -> m b) -> [a] -> m ()


{- monad composition operator -}
(>=>) :: Monad m => (a -> m b) -> (b -> m c) -> a -> m c
f >=> g = \x -> f x >>= g


data  Maybe a     =  Nothing | Just a  deriving (Eq, Ord, Read, Show)
data  Either a b  =  Left a | Right b  deriving (Eq, Ord, Read, Show)
data  Ordering    =  LT | EQ | GT deriving
                                  (Eq, Ord, Bounded, Enum, Read, Show)

```

#### Sources

* <http://mvanier.livejournal.com/4586.html>
* <https://jonaswesterlund.se/monads.html>    
* <http://learnyouahaskell.com/for-a-few-monads-more>
* <http://learnyouahaskell.com/a-fistful-of-monads>    
* <http://en.wikipedia.org/wiki/Monad_(functional_programming)>    
* <https://wiki.haskell.org/All_About_Monads#What_is_a_monad.3F>
* <http://dev.stephendiehl.com/hask/#monad-transformers>
* <http://blog.jakubarnold.cz/2014/07/20/mutable-state-in-haskell.html>
* <https://ro-che.info/articles/2012-01-02-composing-monads>
* <http://www.stephanboyer.com/post/9/monads-part-1-a-design-pattern>
* <http://the-27th-comrade.appspot.com/blog/ahJzfnRoZS0yN3RoLWNvbXJhZGVyDAsSBUVudHJ5GOFdDA>
* <http://comonad.com/reader/2008/deriving-strength-from-laziness/>
* <https://www.haskell.org/tutorial/monads.html>



### Maybe Monad

Using the Maybe type is possible to indicate that a function might or not return value. It is also useful to avoid many boilerplate null checkings.

```
data Maybe x = Nothing | Just x

f :: a -> Maybe b
return x  = Just x
Nothing >>= f = Nothing
Just x >>= f = f x


g :: a -> b
fmap g (Just x) = Just( g x)
fmap g  Nothing = Nothing

{- fmap is the same as liftM -}
liftM g (Just x) = Just( g x)
liftM g  Nothing = Nothing
```

Lift Functions

```haskell
liftM  :: Monad m => (a1 -> r) -> m a1 -> m r
liftM2 :: Monad m => (a1 -> a2 -> r) -> m a1 -> m a2 -> m r
liftM3 :: Monad m => (a1 -> a2 -> a3 -> r) -> m a1 -> m a2 -> m a3 -> m r
liftM4 :: Monad m => (a1 -> a2 -> a3 -> a4 -> r) -> m a1 -> m a2 -> m a3 -> m a4 -> m r
```

Example:

```haskell
> liftM (+4) (Just 10)
Just 14 
>
> liftM (+4) Nothing
Nothing
> 
> 

> liftM2 (+) (Just 10) (Just 5)
Just 15
> 
> 
> liftM2 (+) (Just 10) Nothing
Nothing
> 

> liftM2 (+) Nothing Nothing
Nothing
> 
```

**Error Handling and avoinding Null Checking**

Examples without Maybe:

```haskell

λ :set prompt "> " 
> 
> 
>  head [1, 2, 3, 4]
1
> head []
*** Exception: Prelude.head: empty list
 

> tail [1, 2, 3, 4]
[2,3,4]
> 
> tail []
*** Exception: Prelude.tail: empty list

> div 10 2
5
> div 10 0
*** Exception: divide by zero
> 
```

Examples with Maybe monad:

```haskell

fromJust (Just x) = x

safeHead :: [a] -> Maybe a
safeHead [] = Nothing
safeHead (x:_) = Just x

safeTail :: [a] -> Maybe [a]
safeTail [] = Nothing
safeTail (_:xs) = Just xs

safeLast :: [a] -> Maybe a
safeLast [] = Nothing
safeLast (y:[]) = Just y
safeLast (_:xs) = safeLast xs

safeInit :: [a] -> Maybe [a]
safeInit [] = Nothing
safeInit (x:[]) = Just []
safeInit (x:xs) = Just (x : fromJust(safeInit xs))

safediv y x | x == 0    = Nothing
            | otherwise = Just(y/x)

> fromJust (Just 10)
10

> safeHead [1..5]
Just 1
> safeHead []
Nothing
> 

> safeTail  [1..5]
Just [2,3,4,5]
> safeTail  []
Nothing
> 

> let div10by = safediv 10
> let div100by = safediv 100


> safediv 10 2
Just 5.0
> safediv 10 0
Nothing
> 
> 

> div10by 2
Just 5.0

> div100by 20
Just 5.0
> div100by 0
Nothing
> 

> map div10by [-2..2]
[Just (-5.0),Just (-10.0),Nothing,Just 10.0,Just 5.0]
> 
```

Composition With May be with the >>= (Monad bind operator)

```haskell


> div100by (div10by 2)

<interactive>:102:11:
    Couldn't match expected type `Double'
                with actual type `Maybe Double'
    In the return type of a call of `div10by'
    In the first argument of `div100by', namely `(div10by 2)'
    In the expression: div100by (div10by 2)
> 

> div10by 2 >>= div100by
Just 20.0

> div10by 2 >>= div10by >>= div100by 
Just 50.0
> 

> div10by 2 >>= safediv 0 >>= div100by 
Nothing
> 

> div10by 0 >>= safediv 1000 >>= div100by 
Nothing
> 
```

Reference:  

* http://www.fatvat.co.uk/2009/10/dealing-with-partial-functions.html 
* http://en.wikibooks.org/wiki/Haskell/Understanding_monads
* https://www21.in.tum.de/teaching/perlen/WS1415/unterlagen/Monads_in_Haskell.pdf


### List Monad

```haskell
instance Monad [] where
    --return :: a -> [a]
    return x = [x] -- make a list containing the one element given
 
    --(>>=) :: [a] -> (a -> [b]) -> [b]
    xs >>= f = concat (map f xs) 
        -- collect up all the results of f (which are lists)
        -- and combine them into a new list
```

Examples Using the bind operator for lists:

```haskell
> [10,20,30] >>= \x -> [2*x, x+5] 
[20,15,40,25,60,35]
> 

> [10,20,30] >>= \x -> [(2*x, x+5)] 
[(20,15),(40,25),(60,35)]
> 
```

Do Notation for lists

The list comprehension is a syntax sugar for do-notation to list monad.

File: listMonad.hs 
```haskell
listOfTuples :: [(Int,Char)]  
listOfTuples = do  
    n <- [1,2]  
    ch <- ['a','b']  
    return (n,ch) 
```    

Ghci shell
```
> :l listMonad.hs 
[1 of 1] Compiling Main             ( listMonad.hs, interpreted )
Ok, modules loaded: Main.
> 

> listOfTuples 
[(1,'a'),(1,'b'),(2,'a'),(2,'b')]

> [ (n,ch) | n <- [1,2], ch <- ['a','b'] ]  
[(1,'a'),(1,'b'),(2,'a'),(2,'b')]
> 

> do { x <- [10, 20, 30] ; [x, x+1] }
[10,11,20,21,30,31]

> do { x <- [10, 20, 30] ; [(x, x+1)] }
[(10,11),(20,21),(30,31)]
> 

> do { x <- [10, 20, 30] ; y <- [1, 2, 3] ; return (x*y) }
[10,20,30,20,40,60,30,60,90]
> 

> sequence [[1,2],[3,4]]
[[1,3],[1,4],[2,3],[2,4]]
> 
> 
```

Operator: (,)
```
> (,) 3 4
(3,4)
> 

> map ((,)2) [1, 2, 3, 4]
[(2,1),(2,2),(2,3),(2,4)]
```

**fmap, map and liftM**

For a list, fmap is equivalent to map

```haskell
> fmap ((,)3) [1, 2, 3, 4]
[(3,1),(3,2),(3,3),(3,4)]
> 
> fmap (+3) [1, 2, 3, 4]
[4,5,6,7]
> 

> liftM ((,)3) [1, 2, 3, 4]
[(3,1),(3,2),(3,3),(3,4)]
> 

> liftM (+3) [1, 2, 3, 4]
[4,5,6,7]
> 
```

**liftM and Cartesian Product**

```haskell

> liftM2 (,) [1, 2, 3] [4, 5, 6, 7]
[(1,4),(1,5),(1,6),(1,7),(2,4),(2,5),(2,6),(2,7),(3,4),(3,5),(3,6),(3,7)]
> 
> 
> liftM2 (,) ['a', 'b', 'c'] [1, 2]
[('a',1),('a',2),('b',1),('b',2),('c',1),('c',2)]
> 
> 

> liftM2 (*) [1, 2, 3] [4, 5, 6, 7]
[4,5,6,7,8,10,12,14,12,15,18,21]
> 

> liftM2 (+) [1, 2, 3] [4, 5, 6, 7]
[5,6,7,8,6,7,8,9,7,8,9,10]
> 

> liftM3 (,,) [1, 2, 3] ['a', 'b', 'c', 'd'] ['x', 'y', 'z']
[(1,'a','x'),(1,'a','y'),(1,'a','z'),(1,'b','x'),(1,'b','y'),(1,'b','z'),(1,'c','x'),(1,'c','y'),(1,'c','z'),(1,'d','x'),(1,'d','y'),(1,'d','z'),(2,'a','x'),(2,'a','y'),(2,'a','z'),(2,'b','x'),(2,'b','y'),(2,'b','z'),(2,'c','x'),(2,'c','y'),(2,'c','z'),(2,'d','x'),(2,'d','y'),(2,'d','z'),(3,'a','x'),(3,'a','y'),(3,'a','z'),(3,'b','x'),(3,'b','y'),(3,'b','z'),(3,'c','x'),(3,'c','y'),(3,'c','z'),(3,'d','x'),(3,'d','y'),(3,'d','z')]

```


http://learnyouahaskell.com/a-fistful-of-monads

### IO and IO Monad

Haskell separates pure functions from computations where side effects must be considered by encoding those side effects as values of a particular type. Specifically, a value of type (IO a) is an action, which if executed would produce a value of type a.  [[1](https://wiki.haskell.org/Introduction_to_IO)]

Actions are either atomic, as defined in system primitives, or are a sequential composition of other actions. The I/O monad contains primitives which build composite actions, a process similar to joining statements in sequential order using `;' in other languages. Thus the monad serves as the glue which binds together the actions in a program. [[2](https://www.haskell.org/tutorial/io.html)]

Haskell uses the data type IO (IO monad) for actions.

* > let n = v   Binds n to value v
* > n <- a      Executes action a and binds the name n to the result
* > a           Executes action a
* do  notation  is syntactic sugar for (>>=) operations. 


**Intput Functions**

Stdin - Standard Input
```haskell
getChar             :: IO Char
getLine             :: IO String
getContents         :: IO String
interact            :: (String -> String) -> IO ()
readIO              :: Read a => String -> IO a
readLine            :: Read a => IO a
```


**Output Functions**

Stdout - Standard Output
```haskell
print               :: Show a => a -> IO ()
putStrLn            :: String -> IO ()
putStr              :: String -> IO ()
```

**Files**
```
type FilePath = String

writeFile     ::  FilePath -> String            -> IO ()
appendFile    ::  FilePath -> String            -> IO ()
readFile      ::  FilePath                      -> IO String
```

#### Main action

The only IO action which can really be said to run in a compiled Haskell program is main. 

HelloWorld.hs
```
main :: IO ()
main = putStrLn "Hello, World!"
```

Compile HelloWorld.hs
```
$ ghc HelloWorld.hs 
[1 of 1] Compiling Main             ( HelloWorld.hs, HelloWorld.o )
Linking HelloWorld ...

$ file HelloWorld
HelloWorld: ELF 32-bit LSB  executable, Intel 80386, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.24, BuildID[sha1]=9cd178d3dd88290e7fcfaf93c9aba9b2308a0e87, not stripped

```

Running HelloWorld.hs executable.
```
$ ./HelloWorld 
Hello, World!

$ runhaskell HelloWorld.hs
Hello, World!
```

#### Read and Show

```
show   :: (Show a) => a -> String
read   :: (Read a) => String -> a

{- lines 
    split string into substring at new line character \n \r
-}
lines :: String -> [String]
```

Example:

```haskell

> show(12.12 + 23.445)
"35.565"
> 

> read "1.245" :: Double
1.245
> 
> let x = read "1.245" :: Double
> :t x
x :: Double
> 
> read "[1, 2, 3, 4, 5]" :: [Int]
[1,2,3,4,5]
> 

```

#### Operator >> (then)

The “then” combinator (>>) does sequencing when there is no value to pass:

```haskell
(>>)    ::  IO a -> IO b -> IO b
m >> n  =   m >>= (\_ -> n)
```

Example:

```haskell
> let echoDup = getChar >>= \c -> putChar c >> putChar c
> echoDup 
eee> 
> 
> echoDup 
ooo> 
> 

```

It is equivalent in a do-notation to:

```
echoDup = do
    c <- getChar
    putChar c
    putChar c
```


#### Basic I/O Operations

Every IO action returns a value. The returned value is tagged with IO type.

Examples:

```haskell
getChar :: IO Char -- Performs an action that returns a character

{- 
    To capture a value returned by an action, the operator <- must be used
-}
> c <- getChar 
h> 
> c
'h'
> :t c
c :: Char
> 
```

IO Actions that returns nothing uses the unit type (). The return type is IO (), it is equivalent to C language void.

Example:

```haskell
> :t putChar
putChar :: Char -> IO ()

> putChar 'X'
X> 
> 
```

The operator >> concatenates IO actions, it is equivalent to (;) semicolon operator in imperative languages.

```haskell
> :t (>>)
(>>) :: Monad m => m a -> m b -> m b
```

```haskell
> putChar 'X' >>  putChar '\n'
X
> 
```

Equivalent code in a imperative language, Python.

```python
>>> print ('\n') ; print ('x')


x

```



#### Do Notation

The statements in the do-notation are executed in a sequential order. It is syntactic sugar for the bind (>>=) operator. The values of local statements are defined using let and result of an action uses the (<-) operator. The “do” notation adds syntactic sugar to make monadic code easier to read.

The do notation 

```
anActon = do {v1 <- e1; e2} 
```

is a syntax sugar notation for the expression:

```
anActon = e1 >>= \v1 -> e2
```

Plain Syntax

```haskell
getTwoChars :: IO (Char,Char)
getTwoChars = getChar   >>= \c1 ->
              getChar   >>= \c2 ->
              return (c1,c2)
```

Do Notation

```haskell
getTwoCharsDo :: IO(Char,Char)
getTwoCharsDo = do { c1 <- getChar ;
                     c2 <- getChar ;
                     return (c1,c2) }
```

Or:

```haskell
getTwoCharsDo :: IO(Char,Char)
getTwoCharsDo = do 
    c1 <- getChar 
    c2 <- getChar 
    return (c1,c2)
```


##### Basic Do Notation

File: do_notation1.hs
```haskell
do1test = do
    c <- getChar 
    putChar 'x'
    putChar c
    putChar '\n'
```

In the shell ghci
```haskell
> :l do_notation1.hs 
[1 of 1] Compiling Main             ( do_notation1.hs, interpreted )
Ok, modules loaded: Main.
> 

> :t do1test 
do1test :: IO ()
> 

> do1test -- User types character 'a'
axa
> do1test -- User types character 'x'
txt
> do1test -- User types character 'p'
pxp
> 
```

##### Do Notation and Let keyword

File: do_notation2.hs

```haskell
make_string :: Char -> String
make_string achar = "\nThe character is : " ++ [achar]

do2test = do
    let mychar = 'U'
    c <- getChar     
    putStrLn (make_string c)
    putChar mychar
    putChar '\n'
    
do3test = do   
    c <- getChar     
    let phrase = make_string c
    putStrLn phrase   
    putChar '\n'
```

In the shell ghci
```haskell
> :l do_notation2.hs 
[1 of 1] Compiling Main             ( do_notation1.hs, interpreted )
Ok, modules loaded: Main.
> 

> :t make_string 
make_string :: Char -> String
>

> :t do2test 
do2test :: IO ()

> make_string 'q'
"\nThe character is : q"
> make_string 'a'
"\nThe character is : a"
> 

> do2test 
a
The character is : a
U

> do2test 
p
The character is : p
U

> do3test 
a
The character is : a

> do3test 
b
The character is : b
```

##### Do Notation returning a value


File: do_return.hs
```haskell
doReturn = do
    c <- getChar
    let test = c == 'y'
    return test
```

In ghci shell
```haskell
> :t doReturn 
doReturn :: IO Bool
> 

> doReturn 
aFalse
> doReturn 
bFalse
> doReturn 
cFalse
> doReturn 
yTrue
> 

> x <- doReturn 
r> 
> x
False
> 
> x <- doReturn 
m> 
> x
False
> x <- doReturn 
y> 
> x
True
> 
```


##### Combining functions and I/O actions

```haskell
> import Data.Char (toUpper)
> 
> let shout = map toUpper 
> :t shout
shout :: [Char] -> [Char]
> 

{- Fmap is Equivalent to liftM , those functions
apply a function to the value wraped in the monad and returns a new monad of 
same type with the return value wraped

-}

> :t liftM
liftM :: Monad m => (a1 -> r) -> m a1 -> m r
> :t fmap
fmap :: Functor f => (a -> b) -> f a -> f b
> 


> shout "hola estados unidos"
"HOLA ESTADOS UNIDOS"

> liftM shout getLine
Hello world
"HELLO WORLD"


> fmap shout getLine
heloo
"HELOO"
> 

> let upperLine = putStrLn "Enter a line" >> liftM shout getLine

> upperLine 
Enter a line
hola estados Unidos
"HOLA ESTADOS UNIDOS"
> 

> upperLine 
Enter a line
air lift
"AIR LIFT"
> 
```

##### Executing a list of actions

The list myTodoList doesn't execute any action, it holds them. To join those actions the function sequence_ must be used.


```haskell
> 
> let myTodoList = [putChar '1', putChar '2', putChar '3', putChar '4']

> :t myTodoList 
myTodoList :: [IO ()]
> 

> :t sequence_
sequence_ :: Monad m => [m a] -> m ()
>
> sequence_ myTodoList 
1234> 
> 

> 
> let newAction = sequence_ myTodoList 
> :t newAction 
newAction :: IO ()
> 
> newAction 
1234> 
> 
> 
```

The function sequence_ is defined as:

```haskell
sequence_        :: [IO ()] -> IO ()
sequence_ []     =  return ()
sequence_ (a:as) =  do a
                       sequence as                                            
```

Or defined as:

```haskell
sequence_        :: [IO ()] -> IO ()
sequence_        =  foldr (>>) (return ())
```

The sequence_ function can be used to construct putStr from putChar:

```
putStr                  :: String -> IO ()
putStr s                =  sequence_ (map putChar s)
```

##### Control Structures 

###### For Loops

```haskell
> :t forM_
forM_ :: Monad m => [a] -> (a -> m b) -> m ()

> :t forM
forM :: Monad m => [a] -> (a -> m b) -> m [b]
> 
```

Example:

```haskell
> :t (putStrLn . show)
(putStrLn . show) :: Show a => a -> IO (

> (putStrLn . show) 10
10
> (putStrLn . show) 200
200
>

> forM_ [1..10] (putStrLn . show)
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
```

##### mapM and mapM_

Map a monadic function, a function that returns a monad, to a list. It is similar to forM and formM_.

```haskell
> :t mapM
mapM :: Monad m => (a -> m b) -> [a] -> m [b]
> 
> :t mapM_
mapM_ :: Monad m => (a -> m b) -> [a] -> m ()
> 
> 
```

Example:

```haskell

> :t (putStrLn . show)
(putStrLn . show) :: Show a => a -> IO (

> mapM_ (putStrLn . show) [1..10]
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
```

#### IO Examples

**Example 1**

```haskell
> let echo = getChar >>= putChar 
> echo 
aa> 
> echo 
cc> 
> 


> :t getChar
getChar :: IO Char
> :t putChar
putChar :: Char -> IO ()
> :t (>>=)
(>>=) :: Monad m => m a -> (a -> m b) -> m b
> 
```

**Example 2**

```haskell
reverseInput = do 
    putStrLn "Enter a line of text:"
    x <- getLine
    putStrLn (reverse x)

> reverseInput 
Enter a line of text:
Hello World
dlroW olleH
>          
```        


**Example 3**

File: questions.hs
```haskell
questions = do
    putStrLn "\nWhat is your name ??"
    name <- getLine
    
    putStrLn "\nWhere you come from ??"
    country <- getLine
    
    putStrLn "\nHow old are you ??"
    age <- getLine
    
    
    let result = "Your name is : " ++ name ++ "\nYou come from " ++ country  ++ "\nYour age is : " ++ age
    putStrLn result       
```

GHCI Shell

```haskell
[1 of 1] Compiling Main             ( questions.hs, interpreted )
Ok, modules loaded: Main.
> 
> questions

Whats your name ??
George Washington

Where you come from ??
US

Whats your age ??
60
Your name is : George Washington
You come from US
Your age is : 60

```

**Example 4 - Reading and Writing a File**

```haskell
> (show [(x,x*x) | x <- [0,1..10]])
"[(0,0),(1,1),(2,4),(3,9),(4,16),(5,25),(6,36),(7,49),(8,64),(9,81),(10,100)]"
> 
> :t writeFile "squares.txt" (show [(x,x*x) | x <- [0,1..10]])
writeFile "squares.txt" (show [(x,x*x) | x <- [0,1..10]]) :: IO ()
> 
> writeFile "squares.txt" (show [(x,x*x) | x <- [0,1..10]])
> 
> readFile "squares.txt"
"[(0,0),(1,1),(2,4),(3,9),(4,16),(5,25),(6,36),(7,49),(8,64),(9,81),(10,100)]"
> 
> :t readFile "squares.txt"
readFile "squares.txt" :: IO String
> 
> 
> content <- readFile "squares.txt"
> :t content
content :: String
> content
"[(0,0),(1,1),(2,4),(3,9),(4,16),(5,25),(6,36),(7,49),(8,64),(9,81),(10,100)]"
> 
> let array = read content :: [(Int,Int)]
> array
[(0,0),(1,1),(2,4),(3,9),(4,16),(5,25),(6,36),(7,49),(8,64),(9,81),(10,100)]
> 

> let readSquareFile = liftM (\cont -> read cont :: [(Int, Int)]) (readFile "squares.txt")
> 
> readSquareFile 
[(0,0),(1,1),(2,4),(3,9),(4,16),(5,25),(6,36),(7,49),(8,64),(9,81),(10,100)]
> 
> :t readSquareFile 
readSquareFile :: IO [(Int, Int)]
> 

> sq <- readSquareFile 
> sq
[(0,0),(1,1),(2,4),(3,9),(4,16),(5,25),(6,36),(7,49),(8,64),(9,81),(10,100)]
> 
> :t sq
sq :: [(Int, Int)]
> 

> :t liftM (map $ uncurry (+)) readSquareFile 
liftM (map $ uncurry (+)) readSquareFile :: IO [Int]
> 
> liftM (map $ uncurry (+)) readSquareFile 
[0,2,6,12,20,30,42,56,72,90,110]
> 
> 
```

#### Sources

* [Introduction to IO](https://wiki.haskell.org/Introduction_to_IO)
* [A Gentle Introduction to Haskell, Version 98 -  Input/Output](https://www.haskell.org/tutorial/io.html)

* http://en.wikibooks.org/wiki/Haskell/Understanding_monads
* http://shuklan.com/haskell/lec09.html#/
* http://learnyouahaskell.com/functors-applicative-functors-and-monoids
* http://squing.blogspot.com.br/2008/01/unmonad-tutorial-io-in-haskell-for-non.html



## Useful Custom Functions/ Iterators and Operators

This a collection of useful short code snippets. 


### Pipelining Operators

Haskell doesn't have a native Pipe operator like F# (F-Sharp) does, however
it can be defined by the user.

```haskell

> let (|>) x f = f x
> 
> let (|>>) x f = map f x

> let (?>>) x f = filter f x


> take 3 (reverse (filter even [1..10]))
[10,8,6]

> [1..10] |> filter even |> reverse |> take 3
[10,8,6]
> 


> [1..10] |>> (^2) |>> (/10) |>> (+100)
[100.1,100.4,100.9,101.6,102.5,103.6,104.9,106.4,108.1,110.0]

> 
> [1..10] ?>> even
[2,4,6,8,10]
> 
> [1..10] ?>> even |>> (+1)
[3,5,7,9,11]
> 
> 

```

### Iterators

#### Pair Iterator

Definition:

```haskell
pairs alist = zip alist (tail alist)
```

The pairs iterator converts a list of elements to a new list of consecutive elements tuple. 

Pseudo code:
```
pairs [e0, e1, e2, e3, e4 ...] ==> [(e0, e1), (e1, e2), (e3, e4) ...]
```

Let f be a function of two arguments:
```
f :: a -> a -> b
```

The function f can be applied to to the pairs sequence using the higher order function uncurry.

Pseudo code:
```   
> g = uncurry(f) :: (a, a) -> b
> g (x, y) = f x y

> map uncurry(f) $ pairs [e0, e1, e2, e3, e4 ...]
>   [g (e0, e1), g (e1, e2), g (e2, e3), g (e3, e4) ...]
```


It can be useful to calculate the distance between two points, lagged difference, growth of a time series, draw a line between each two consecutive points or apply any function to two consecutive elements.

Example: Grouping Consecutive numbers

```haskell
> let pairs alist = zip alist (tail alist)

> pairs [1..5]
[(1,2),(2,3),(3,4),(4,5)]
```

Example: Lagged Difference

Pseudo code:
```
lagdiff [e0, e1, e2, e3, e4 ...] ==> [(e1 - e0), (e2 - e1), (e3 - e2) ... ]
``` 

Development:

```haskell

> let pairs alist = zip alist (tail alist)

> :t pairs
pairs :: [b] -> [(b, b)]

> :t (-)
(-) :: Num a => a -> a -> a

> :t uncurry(-)
uncurry(-) :: Num c => (c, c) -> c
> 

> (-) 20 10
10
> 

> uncurry(-) (20, 10)
10
> 

> uncurry(-) (10, 20)
-10
> 

> uncurry(flip (-)) (10, 20)
10
> 

> pairs [10.3, 20.5, 5.6, 8.23, 40.3]
[(10.3,20.5),(20.5,5.6),(5.6,8.23),(8.23,40.3)]
> 

> map (uncurry ( flip (-))) $ pairs [10.3, 20.5, 5.6, 8.23, 40.3]
[10.2,-14.9,2.630000000000001,32.06999999999999]
> 

> let lagdiff series = map (uncurry ( flip (-))) $ pairs series
> :t lagdiff 
lagdiff :: Num b => [b] -> [b]
> 

> lagdiff [10.3, 20.5, 5.6, 8.23, 40.3]
[10.2,-14.9,2.630000000000001,32.06999999999999]
> 

> lagdiff [10, 30, 5, 8, 100]
[20,-25,3,92]
> 

```

Example: Distance between points on the plane.

```haskell

> let pairs alist = zip alist (tail alist)

{- [(X, Y)]  coordinates of points in a plane -}
> let points = [(1.0, 2.0), (3.0, 4.0), (-1.0, 5.0), (6.0, 6.0)]
> let distance (x1, y1) (x2, y2) = sqrt( (x2-x1)^2 + (y2-y1)^2 )

> let lines = pairs points 
> lines
[((1.0,2.0),(3.0,4.0)),((3.0,4.0),(-1.0,5.0)),((-1.0,5.0),(6.0,6.0))]
> 

> distance (1.0, 2.0) (3.0, 4.0)
2.8284271247461903
> 

{- Calculate the length of each line segment -}

> map (uncurry(distance)) lines
[2.8284271247461903,4.123105625617661,7.0710678118654755]
> 

> sum $ map (uncurry(distance)) lines
14.022600562229327
> 

> let totalLength points  =  sum $  map (uncurry(distance)) $ pairs (points)
> 
> totalLength points 
14.022600562229327
> 

```

#### Triples Iterator

Definition:
```haskell
triples alist = zip3 alist (tail alist) (tail $ tail alist)
```

Example:
```haskell
> triples [1..10]
[(1,2,3),(2,3,4),(3,4,5),(4,5,6),(5,6,7),(6,7,8),(7,8,9),(8,9,10)]
> 

> :t triples 
triples :: [c] -> [(c, c, c)]
> 
> 
```

#### Sliding Window Iterator

This iterator is used in Scala and it is a generalized pairs iterator.

Definition:

```haskell
sliding n alist = map (take n) (take (length(alist) -n + 1 ) $ iterate tail alist)
```

Example:

```haskell
>  sliding 3 [1..10]
[[1,2,3],[2,3,4],[3,4,5],[4,5,6],[5,6,7],[6,7,8],[7,8,9],[8,9,10]]

>  sliding 4 [1..10]
[[1,2,3,4],[2,3,4,5],[3,4,5,6],[4,5,6,7],[5,6,7,8],[6,7,8,9],[7,8,9,10]]

> sliding 5 [1..10]
[[1,2,3,4,5],[2,3,4,5,6],[3,4,5,6,7],[4,5,6,7,8],[5,6,7,8,9],[6,7,8,9,10]]

> sliding 6 [1..10]
[[1,2,3,4,5,6],[2,3,4,5,6,7],[3,4,5,6,7,8],[4,5,6,7,8,9],[5,6,7,8,9,10]]

> sliding 9 [1..10]
[[1,2,3,4,5,6,7,8,9],[2,3,4,5,6,7,8,9,10]]
> 
```

Scala Equivalent
```
scala> (1 to 5).iterator.sliding(3).toList
res2: List[Seq[Int]] = List(List(1, 2, 3), List(2, 3, 4), List(3, 4, 5))
```

#### Enumerate Iterator

Equivalent to python enumerate.

Definition:
```haskell
enumerate :: [b] -> [(Int, b)]
enumerate alist = zip [0..(length(alist)-1)] alist
```

Example:

```haskell
> enumerate ['a', 'b', 'c', 'd', 'e', 'f']
[(0,'a'),(1,'b'),(2,'c'),(3,'d'),(4,'e'),(5,'f')]

> take 8  (enumerate ['a'..'z'])
[(0,'a'),(1,'b'),(2,'c'),(3,'d'),(4,'e'),(5,'f'),(6,'g'),(7,'h')]
> 
```

**Group by length**

Definition:

```haskell
groupByLen n alist = filter (\a -> length(a) == n  ) ( map f indexes )
    where
    len = length(alist)
    indexes = map (\i -> n*i) [0..(div len n)]
    f idx = take n (drop idx alist)
```

Example:

```haskell
> groupByLen 3 [1..15]
[[1,2,3],[4,5,6],[7,8,9],[10,11,12],[13,14,15]]
> 
> groupByLen 5 [1..15]
[[1,2,3,4,5],[6,7,8,9,10],[11,12,13,14,15]]
> 
> groupByLen 6 [0..20]
[[0,1,2,3,4,5],[6,7,8,9,10,11],[12,13,14,15,16,17]]
> 
> groupByLen 3 ['a'..'z']
["abc","def","ghi","jkl","mno","pqr","stu","vwx"]
> 

```

### Applying Multiples Functions


#### Applying a list of functions to the same argument.

**juxt** is a function that allows apply a list of functions of same type signature to a single argument. This is useful for numerical analysis, statistics and engineering. This function was taken from the Clojure library.

```haskell
juxt fs x = map ($ x) fs
```

Example:
```
> let juxt fs x = map ($ x) fs

> juxt [(*3), (+4), (/10)] 30
[90.0,34.0,3.0]
> 
> let fs = juxt [(*3), (+4), (/10)]
> 
> :t fs
fs :: Double -> [Double]
>
> fs 30
[90.0,34.0,3.0]
> fs 40
[120.0,44.0,4.0]
> 
> map fs [10, 20, 30]
[[30.0,14.0,1.0],[60.0,24.0,2.0],[90.0,34.0,3.0]]
> 
```

#### Applying a tuple of functions to a same argument.

The family of functions juxt2, juxt3, juxt4 allow apply tuples of functions to a single argument. This is necessary when the functions don't have the same type signature. 

```haskell
juxt2 (f1, f2) x = (f1 x, f2 x)
juxt3 (f1, f2, f3) x = (f1 x, f2 x, f3 x)
juxt4 (f1, f2, f3, f4) x = (f1 x, f2 x, f3 x, f4 x)
juxt5 (f1, f2, f3, f4, f5) x = (f1 x, f2 x, f3 x, f4 x, f5 x)
```

Example:
```haskell

{- 

This function fails in static typed language when 
the functions don't have the same type signature 

-}
> juxt [(>100), (+100)]  30

<interactive>:36:9:
    No instance for (Num Bool) arising from the literal `100'
    Possible fix: add an instance declaration for (Num Bool)
    In the second argument of `(>)', namely `100'
    In the expression: (> 100)
    In the first argument of `juxt', namely `[(> 100), (+ 100)]'


> juxt2 ((>100), (+100))  30
(False,130)
> 
> 
> let f = juxt2 ((>100), (+100))
> :t f
f :: Integer -> (Bool, Integer)
> 
> f 30
(False,130)
>
> map f [10, 20, 25, 30, 100, 150]
[(False,110),(False,120),(False,125),(False,130),(False,200),(True,250)]
> 


> 
> juxt3 (length, maximum, minimum)  [100.23, 23.23, 12.33, -123.23, -1000.23, 4000.5]
(6,4000.5,-1000.23)
> 


{- 

    The type system fails to resolve the types in someone
    cases. So when it happens the developer must make the
    function types explicit.

-}
> let analytics = juxt3 (length, maximum, minimum)
> 
> :t analytics 
analytics :: [()] -> (Int, (), ())
> 
> analytics [100.23, 23.23, 12.33, -123.23, -1000.23, 4000.5]

<interactive>:79:12:
    No instance for (Fractional ()) arising from the literal `100.23'
    Possible fix: add an instance declaration for (Fractional ())
    In the expression: 100.23
    In the first argument of `analytics', namely
      `[100.23, 23.23, 12.33, - 123.23, ....]'
    In the expression: analytics [100.23, 23.23, 12.33, - 123.23, ....]

> let analytics :: [Double] -> (Int, Double, Double)  ; analytics = juxt3 (length, maximum, minimum)
> 
> :t analytics 
analytics :: [Double] -> (Int, Double, Double)
> 

> analytics [100.23, 23.23, 12.33, -123.23, -1000.23, 4000.5]
(6,4000.5,-1000.23)
> 

> import Data.Char
> 
> let f = juxt3 (succ, pred, ord)
> :t f
f :: Char -> (Char, Char, Int)
> 
> let a = map f "haskell is fun"
> a
[('i','g',104),('b','`',97),('t','r',115),('l','j',107),('f','d',101),('m','k',108),('m','k',108),('!','\US',32),('j','h',105),('t','r',115),('!','\US',32),('g','e',102),('v','t',117),('o','m',110)]
> 
> unzip3 a
("ibtlfmm!jt!gvo","g`rjdkk\UShr\USetm",[104,97,115,107,101,108,108,32,105,115,32,102,117,110])
> 
>

```

#### Control Flow Functions

**between**

```haskell
between a b x = a <= x && x <= b
```

```haskell
> filter (between 10 20) [23, 5, 8, 17, 24, 13, 12]
[17,13,12]
> 

> filter (not . between 10 20) [23, 5, 8, 17, 24, 13, 12]
[23,5,8,24]
```

**ifelseDo**

Pseudo Code:

```
f(x) = if pred(x) == True then: fa(x) else fb(x)
```

```haskell
ifelseDo pred fa fb  x  =  if pred x then fa x else fb x
```

Example: Apply the list the function (if x >10 then 10*x else x+5)

```haskell
> let  ifelseDo pred fa fb  x  =  if pred x then fa x else fb x

> map (ifelseDo (>10) (*4) (+5)) [-1, 2, 7, 8, 9, 10, 20, 30, 50]
[4,7,12,13,14,15,80,120,200]

> let f = ifelseDo (>10) (*4) (+5)

> f 1
6
> f 3
8
> f 5
10
> 

> f 20
80
> f 30
120

λ> map f [-1, 2, 7, 8, 9, 10, 20, 30, 50]
[4,7,12,13,14,15,80,120,200]

```

**ifelse***


Pseudo Code:

```
f(x) = if pred(x) == True then: a else b
```

```haskell
ifelse   pred a  b   x  =  if pred x then a   else b
```

Example: 

If x<0 set x to -1 else set to 1

```haskell
> let f  = ifelse (<0) (-1) 1
> 
> f 2
1
> f 40
1
> f (-1)
-1
> f (-10)
-1

> map f [-1, -2, 3, 4, -5, -6, 0, 2]
[-1,-1,1,1,-1,-1,1,1]
> 
```

**ifelseEq**

Pseudo Code:

```
f(x) = if pred(x) == True then: a else x
```

```haskell
ifelseEq pred a      x  =  if pred x then a   else x
```

Example: if(x) > 10 then 30 else x
```haskell

> let ifelseEq pred a x  =  if pred x then a   else x

> let f = ifelseEq (>10) 30

> map f [1, 2, 20, 10, 9, 8, 100]
[1,2,30,10,9,8,30]
> 

```

## Applications


### Mathematics


**Trigonometric Degree Functions**

```haskell

deg2rad deg = deg*pi/180.0  -- convert degrees to radians
rad2deg rad = rad*180.0/pi  -- convert radians to degrees

sind = sin . deg2rad        
cosd = cos . deg2rad        
tand = tan . deg2rad
atand = rad2deg . atan
atan2d y x = rad2deg (atan2 y x )
```

Example:


```haskell

> map rad2deg [pi/6, pi/4, pi/3, pi/2, pi]
[29.999999999999996,45.0,59.99999999999999,90.0,180.0]
> 
> 

> map sind [30.0, 45.0, 60.0, 90.0, 180.0 ]
[0.49999999999999994,0.7071067811865475,0.8660254037844386,1.0,1.2246063538223773e-16]
> 
```


### Picewise Functions


Implement the following functions in Haskell

```

       /  0.10    if 0.0      <= x <= 7150.0
       |  0.15    if 7150.0   <  x <= 29050.0
       |  0.25    if 29050.0  <  x <= 70350.0
f1(x)= |  0.28    if 70350.0  <  x <= 146750.0
       |  0.33    if 146750.0 <  x <= 319100.0
       \  0.35    if 139100.0 <  x < +infinitum


       /  x^2 - 1  if x < 0
f2(x) = |  x   - 1  if 0 <= x < 4
       \  3        if x > 4
```

```haskell

import Graphics.Gnuplot.Simple

(|>) x f = f x
(|>>) x f = map f x

pairs xs = zip xs (tail xs)

infp =    1.0e30  -- Plus Infinite
infm = (-1.0e30)  -- Minus Infinite

inInterval x (p1, p2) = (fst p1) < x && x <= (fst p2) 

piceWiseFactory intervalTable x = f x
    where
    f =  filter (inInterval x) (pairs intervalTable) 
        |> head 
        |> fst 
        |> snd 

arange start stop step = [start,(start+step)..(stop-step)]

plotFxs f xs  = do
    let ys = map f xs
    plotList [] (zip xs ys)


f1_table = 
    [
    (0.0,        const 0.10),
    (7150.0,     const 0.15),
    (29050.0,    const 0.25),
    (70350.0,    const 0.28),
    (146750.0,   const 0.33),  
    (319100.0,   const 0.35),  
    (1.0e30,     const 0.35)
    ]

f2_table = [
    (infm,  \x -> x**2 - 1), --  if -∞ < x <= 0  -> x^2 - 1 
    (0.0,   \x -> x - 1.0 ), --  if 0  < x <= 4  -> x   - 1
    (4.0,   \x -> 3.0),      --  if 4  < x <= +∞ -> 3.0
    (infp,  \x -> 3.0 )
    ]

f1 = piceWiseFactory f1_table
f2 = piceWiseFactory f2_table

```

```haskell
> plotFxs f1 $ arange (1.0) 400000 1000.0
```

![f1 chart](images/chartF1table.png)

```haskell
> plotFxs f2 $ arange (-4) 4 0.01
```


![f2 chart](images/chartF2table.png)

### Numerical Methods 

#### Polynomial

Polynomial evaluation by the horner method.

```haskell
polyval :: Fractional a => [a] -> a -> a
polyval coeffs x = foldr (\b c -> b + x*c) 0 coeffs

polyderv :: Fractional a => [a] -> [a] 
polyderv coeffs = zipWith (*) (map fromIntegral [1..n]) (tail coeffs )
    where
    n = (length coeffs) - 1    

```

Example:

```
Reference: http://www.math10.com/en/algebra/horner.html

f(x) = a0 + a1x + a2x2 + a3x3 + a4x4 + a5x5
f(x0) = a0 + x0(a1 + x0(a2 + x0(a3 + x0(a4 + a5x0)))) 

Example: Evaluate the polynomial 
    f(x)  =  1x4 + 3x3 + 5x2 + 7x + 9 at x = 2 
    df(x) =  3x3 + 6x2 + 10x +  7
```

```haskell
    
> let coeffs  = [9.0, 7.0, 5.0, 3.0, 1.0] 
> let f  = polyval  coeffs

let df = polyval $  polyderv coeffs

> polyderv coeffs 
[7.0,10.0,9.0,4.0]

> f 2
83.0

> df 2
95.0

> (\x -> 7 + 10*x + 9*x^2 + 4*x^3) 2
95
```





#### Numerical Derivate

```haskell

derv dx f x = (f(x+dx) - f(x))/dx

f x = 2*x**2 - 2*x
df = derv 1e-5 f

*Main> map f [2, 3, 4, 5] 
[4.0,12.0,24.0,40.0]
*Main> 

*Main> let df = derv 1e-5 f
*Main> 
*Main> map df  [2, 3, 4, 5]
[6.000020000040961,10.000019999978349,14.000019999116374,18.000019998964945]
*Main> 

*Main> let dfx x = 4*x - 2
*Main> map dfx [2, 3, 4, 5]
[6,10,14,18]
```

#### Nonlinear Equation - Root-finding

See also: 

* [Root finding](http://en.wikipedia.org/wiki/Root-finding_algorithm)
* [Newton's method](http://en.wikipedia.org/wiki/Newton's_method)
* [Bisection method](http://en.wikipedia.org/wiki/Bisection_method)

**Bisection Method**

```haskell

bisection_iterator :: (Floating a, Floating a1, Ord a1) => (a -> a1) -> [a] -> [a]
bisection_iterator f guesslist = newguess
    where
    a =  guesslist !! 0
    b =  guesslist !! 1
    c = (a+b)/2.0
    p = f(a)*f(c)
    newguess = (\p -> if p < 0.0 then [a, c] else [c, b] ) p


bisectionSolver eps itmax f x1 x2 = (root, error, iterations) 
    where  
    
    bisection_error xlist = abs(f $ xlist !! 1)
    check_error xlist = bisection_error xlist > eps

    iterator = bisection_iterator  f

    rootlist = [x1, x2] |> iterate iterator |> takeWhile check_error |> take itmax

    pair = last rootlist |> iterator
    root = last pair
    error = bisection_error pair

    iterations = length rootlist    

*Main> let f x  =  exp(-x) -3*log(x)
*Main> bisectionSolver 1e-5 100 f 0.05 3
(1.1154509544372555,8.86237816760671e-6,19)
*Main> 

```

**Newton Raphson Method**

```haskell
{-
Newton-Raphson Method Iterator, builds an iterator function
from the function to be solved and its derivate.

-}
newton_iterator f df x = x - f(x)/df(x)

{---------------------------------------------------------------------
    newtonSolver(eps, itmax, f, df, guess)

    Solve equation using the Newton-Raphson Method.
    
    params:
    
        eps   :  Tolerance of the solver
        itmax :  Maximum number of iterations
        f     :  Function which the root will be computed
        df    :  Derivate of the function
        guess :  Initial guess 

newtonSolver
  :: (Fractional t, Ord t) =>
     t -> Int -> (t -> t) -> (t -> t) -> t -> (t, t, Int)
-----------------------------------------------------------------------
-}
newtonSolver :: (Floating t, Ord t) => t -> Int -> (t -> t) -> (t -> t) -> t -> (t, t, Int)
newtonSolver eps itmax f df guess = (root, error, iterations)
    where
    check_root x = abs(f(x)) > eps                                  
    iterator = newton_iterator f df   -- Builds the Newton Iterator                              
    generator = iterate $ iterator    -- Infinite List that will that holds the roots (Lazy Evaluation)

    rootlist = take itmax $ takeWhile check_root $ generator guess                                  
    root = iterator $ last $ rootlist                                  
    error = abs(f(root))
    iterations = length rootlist


square_root a | a > 0       = newtonSolver 1e-6 50 (\x -> x^2 -a) (\x -> 2*x) a 
              | otherwise   = error ("The argument must be positive")

{- 
    Solve f(x) = x^2 - 2 = 0 
    
    The solution is sqrt(2)
-}
> let f x = x^2 - 2.0
> 
> let df x = 2*x
> 
> let df x = 2.0*x
> 
> newtonSolver 1e-3 100 f df 5
(1.414470981367771,7.281571315052027e-4,4)
> 
> newtonSolver 1e-3 100 f df 50
(1.4142150098491113,4.094082521888254e-6,8)
> 
```

**Secant Method**

```haskell

(|>) x f = f x
(|>>) x f = map f x

secant_iterator :: Floating t => (t -> t) -> [t] -> [t]
secant_iterator f guesslist = [x, xnext]
    where
    x =  guesslist !! 0
    x_ = guesslist !! 1
    xnext = x - f(x)*(x-x_)/(f(x) - f(x_))

secantSolver eps itmax f x1 x2 = (root, error, iterations) 
    where  
    
    secant_error xlist = abs(f $ xlist !! 1)
    check_error xlist = secant_error xlist > eps

    iterator = secant_iterator  f

    rootlist = [x1, x2] |> iterate iterator |> takeWhile check_error |> take itmax

    pair = last rootlist |> iterator
    root = last pair
    error = secant_error pair

    iterations = length rootlist

*Main> let f x = x^2 - 2.0
*Main> secantSolver  1e-4 20 f 2 3
(1.4142394822006472,7.331301515467459e-5,6)
*Main> 
*Main> let f x = exp(x) - 3.0*x^2
*Main> secantSolver 1e-5 100 f (-2.0)  3.0
(-0.458964305393305,6.899607281729558e-6,24)
*Main> 

```

#### Differential Equations

**Euler Method**

The task is to implement a routine of Euler's method and then to use it to solve the given example of Newton's cooling law with it for three different step sizes of 2 s, 5 s and 10 s and to compare with the analytical solution. The initial temperature T0 shall be 100 °C, the room temperature TR 20 °C, and the cooling constant k 0.07. The time interval to calculate shall be from 0 s to 100 s

From: http://rosettacode.org/wiki/Euler_method

```
Solve differential equation by the Euler's Method.

    T(t)
    ---- =  -k(T(t) - Tr)
     dt
    
    T(t) = Tr + k(T0(t) - Tr).exp(-k*t)
```

```haskell


import Graphics.Gnuplot.Simple


eulerStep f step (x, y)= (xnew, ynew)
                    where
                    xnew = x + step
                    ynew = y + step * (f (x, y))

euler :: ((Double, Double) -> Double) -> Double -> Double -> Double -> Double -> [(Double, Double)]
euler f x0 xf y0 step = xypairs
                     where
                     iterator = iterate $ eulerStep f step
                     xypairs = takeWhile (\(x, y) -> x <= xf ) $ iterator (x0, y0)

> let dTemp k temp_r (t, temp) = -k*(temp - temp_r)

> euler (dTemp 0.07 20.0) 0.0 100.0 100.0 5.0
[(0.0,100.0),(5.0,72.0),(10.0,53.8),(15.0,41.97) \.\.\.
(100.0,20.01449963666907)]
> 

let t_temp = euler (dTemp 0.07 20.0) 0.0 100.0 100.0 5.0

plotList [] t_temp

```

![](images/euler_newton_cooling.png)

**Runge Kutta RK4**

See also: [Runge Kutta Methods](http://en.wikipedia.org/wiki/Runge%E2%80%93Kutta_methods)

```haskell

import Graphics.Gnuplot.Simple

rk4Step f h (x, y) = (xnext, ynext)
                      where
                      
                      k1 = f (x, y)
                      k2 = f (x+h/2, y+h/2*k1)
                      k3 = f (x+h/2, y+h/2*k2)
                      k4 = f (x+h,y+h*k3)
                      
                      xnext = x + h
                      ynext = y + h/6*(k1+2*k2+2*k3+k4)
                      
rk4 :: ((Double, Double) -> Double) -> Double -> Double -> Double -> Double -> [(Double, Double)]
rk4 f x0 xf y0 h = xypairs
                     where
                     iterator = iterate $ rk4Step f h
                     xypairs = takeWhile (\(x, y) -> x <= xf ) $ iterator (x0, y0)

> let dTemp k temp_r (t, temp) = -k*(temp - temp_r)
> 
> let t_temp = rk4 (dTemp 0.07 20.0) 0.0 100.0 100.0 5.0
> plotList [] t_temp
> 
```

### Statistics and Time Series

#### Some Statistical Functions

Arithmetic Mean of a Sequence

```haskell
mean lst = sum lst / fromIntegral (length lst)
```

Geometric Mean of Sequence 
```haskell
geomean lst = (product lst) ** 1/(fromIntegral (length lst))
```

Convert from decimal to percent
```haskell
to_pct   lst = map (100.0 *) lst {- Decimal to percent -}
from_pct lst = map (/100.0)  lsd {- from Percent to Decimal -}
```

Lagged Difference of a time serie
* lagddif [xi] = [x_i+1 - x_i]
```haskell
lagdiff lst = zipWith (-) (tail lst) lst
```

Growth of a Time Serie
* growth [xi] = [(x_i+1 - x_i)/xi]
```haskell
growth lst = zipWith (/) (lagdiff lst) lst
```

Percentual Growth
```haskell
growthp = to_pct . growth
```

Standard Deviation and Variance of a Sequence

```haskell
{- Standard Deviation-}
stdev values =  values   |>> (\x -> x -  mean values ) |>> (^2) |> mean |> sqrt

{- Standard Variance -}
stvar values = stdev values |> (^2)
```

**Example: Investment Return**

The annual prices of an Blue Chip company are given below,
find the percent growth rate at the end of each year and 
the [CAGR](http://www.investopedia.com/articles/analyst/041502.asp) Compound annual growth rate.

```
year    0    1     2     3     4     5
price  16.06 23.83 33.13 50.26 46.97 39.89
```

Solution:

```haskell

> let (|>) x f = f x
> let (|>>) x f = map f x
>
> let cagr prices = (growthp prices |>> (+100) |> geomean ) - 100
>
> let prices = [16.06, 23.83, 33.13, 50.26, 46.97, 39.89 ]
> 
> {- Percent Returns -}
> let returns = growthp prices
> 
> returns
[48.38107098381071,39.02643726395302,51.705402958044054,-6.545961002785513,-15.073451139024908]
> 

> let annual_cagr = cagr prices 
> annual_cagr 
19.956476057259906
> 

```

#### Monte Carlo Simulation Coin Toss

The simplest such situation must be the tossing of a coin. Any individual event will result in the coin falling with one side or the other uppermost (heads or tails). However, common sense tells us that, if we tossed it a very large number of times, the total number of heads and tails should become increasingly similar. For a greater number of tosses the percentage of heads or tails will be next to 50% in a non-biased coin. Credits: [Monte Carlo Simulation - Tossing a Coin](http://staff.argyll.epsb.ca/jreed/math7/strand4/4203.htm)

See [Law of Large Numbers](http://en.wikipedia.org/wiki/Law_of_large_numbers)

![](images/coinflip.gif)

File: coinSimulator.hs
```haskell
import System.Random
import Control.Monad (replicateM)

{-
    0 - tails
    1 - means head

-}

flipCoin :: IO Integer
flipCoin = randomRIO (0, 1)

flipCoinNtimes n = replicateM n flipCoin

frequency elem alist = length $ filter (==elem) alist

relativeFreq :: Integer -> [Integer] -> Double
relativeFreq elem alist = 
    fromIntegral (frequency elem alist) / fromIntegral (length alist)

simulateCoinToss ntimes =  do
    serie <- (flipCoinNtimes  ntimes)
    let counts = map (flip frequency serie)   [0, 1]
    let freqs = map (flip relativeFreq serie) [0, 1]
    return (freqs, counts)

showSimulation ntimes = do
    result <- simulateCoinToss ntimes
    let p_tails = (fst result) !! 0
    let p_heads = (fst result) !! 1
    
    let n_tails = (snd result) !! 0
    let n_heads = (snd result) !! 1
    
    let tosses = n_tails + n_heads
    let p_error = abs(p_tails - p_heads)
    
    putStrLn $ "Number of tosses : " ++ show(tosses)
    putStrLn $ "The number of tails is : " ++ show(n_tails)        
    putStrLn $ "The number of heads is : " ++ show(n_heads)
    putStrLn $ "The % of tails is : " ++ show(100.0*p_tails)
    putStrLn $ "The % of heads is :" ++ show(100.0*p_heads)
    putStrLn $ "The %erro is : "  ++ show(100*p_error)
    putStrLn "\n-------------------------------------"
```


```
> :r
[1 of 1] Compiling Main             ( coinSimulator.hs, interpreted )
Ok, modules loaded: Main.
> 

> :t simulateCoinToss 
simulateCoinToss :: Int -> IO ([Double], [Int])
> 

> :t showSimulation 
showSimulation :: Int -> IO ()
> 


> simulateCoinToss 30
([0.5666666666666667,0.43333333333333335],[17,13])
> 
> simulateCoinToss 50
([0.56,0.44],[28,22])
> 
> simulateCoinToss 100
([0.46,0.54],[46,54])
> 
> simulateCoinToss 1000
([0.491,0.509],[491,509])
> 

> mapM_ showSimulation [1000, 10000, 100000, 1000000]
Number of tosses : 1000
The number of tails is : 492
The number of heads is : 508
The % of tails is : 49.2
The % of heads is :50.8
The %erro is : 1.6000000000000014

-------------------------------------
Number of tosses : 10000
The number of tails is : 4999
The number of heads is : 5001
The % of tails is : 49.99
The % of heads is :50.01
The %erro is : 1.9999999999997797e-2

-------------------------------------
Number of tosses : 100000
The number of tails is : 49810
The number of heads is : 50190
The % of tails is : 49.81
The % of heads is :50.19
The %erro is : 0.38000000000000256

-------------------------------------
Number of tosses : 1000000
The number of tails is : 499878
The number of heads is : 500122
The % of tails is : 49.9878
The % of heads is :50.01219999999999
The %erro is : 2.4399999999996647e-2

-------------------------------------
```

### Vectors

**Dot Product of Two Vectors / Escalar Product**

* v1.v2 = (x1, y1, z1) . (x2, y2, z2) = x1.y1 + y1.y2 + z2.z1
* v1.v2 = Σai.bi

```haskell

> let dotp v1 v2 = sum ( zipWith (*) v1 v2 )   - With Parenthesis
> let dotp v1 v2 = sum $ zipWith (*) v1 v2     - Without Parenthesis with $ operator

> dotp [1.23, 33.44, 22.23, 40] [23, 10, 44, 12]
1820.81


```

**Norm of a Vector**

* norm = sqrt( Σxi^2)

```haskell
> let norm vector = (sqrt . sum) (map (\x -> x^2) vector)

> norm [1, 2, 3, 4, 5]
7.416198487095663

-- Vector norm in multiple line statements in GHCI interactive shell

> :{
| let {
|      norm2 vec =  sqrt(sum_squares)
|      where 
|      sum_squares = sum(map square vec)
|      square x = x*x
|      }
| :}
> 
> norm2 [1, 2, 3, 4, 5]
7.416198487095663
> 

```

**Linspace and Range Matlab Function**

```haskell

linspace d1 d2 n = [d1 + i*step | i <- [0..n-1] ]
    where 
    step = (d2 - d1)/(n-1)
        

range start stop step =  [start + i*step | i <- [0..n] ]
    where
    n = floor((stop - start)/step)

```

### Tax Brackets

Progressive Income Tax Calculation

Credits: [Ayend - Tax Challange](http://ayende.com/blog/108545/the-tax-calculation-challenge)

The following table is the current tax rates in Israel:


```
                        Tax Rate
Up      to 5,070        10%
5,071   up to 8,660     14%
8,661   up to 14,070    23%
14,071  up to 21,240    30%
21,241  up to 40,230    33%
Higher  than 40,230     45%
```


Here are some example answers:
```
    5,000 –> 500
    5,800 –> 609.2
    9,000 –> 1087.8
    15,000 –> 2532.9
    50,000 –> 15,068.1
``` 

This problem is a bit tricky because the tax rate doesn’t apply to the 
whole sum, only to the part that is within the current rate.

A progressive tax system is a way to calculate a tax for a given price 
using brackets each taxed separately using its rate. The french tax on 
revenues is a good example of a progressive tax system.

```
To calculate his taxation, John will have to do this calculation 
(see figure on left):

= (10,000 x 0.105) + (35,000 x 0.256) + (5,000 x 0.4)
= 1,050 + 8,960 + 2,000
= 12,010
 
John will have to pay $ 12,010

If John revenues was below some bracket definition (take $ 25,000 for 
example), only the last bracket containing the remaining amount to be 
taxed is applied :

= (10,000 x 0.105) + (15,000 x 0.256)

Here nothing is taxed in the last bracket range at rate 40.
```

Solution:

```haskell

(|>) x f = f x
(|>>) x f = map f x
joinf functions element = map ($ element) functions

-- Infinite number
above = 1e30 

pairs xs = zip xs (tail xs)

{- 
    Tax rate function - Calculates the net tax rate in %
    
    taxrate = 100 *  tax / (gross revenue)

-}
taxrate taxfunction income = 100.0*(taxfunction income)/income

progressivetax :: [[Double]] -> Double -> Double
progressivetax taxtable income = amount
            where 
            rates = taxtable |>> (!!1) |>> (/100.0)  |> tail
            levels = taxtable |>> (!!0)
            table = zip3 levels (tail levels) rates            
            amount = table |>> frow income |> takeWhile (>0) |> sum
            
            frow x (xlow, xhigh, rate) | x > xhigh = (xhigh-xlow)*rate 
                                       | otherwise = (x-xlow)*rate   
taxsearch taxtable value = result        
        where
        rows = takeWhile (\row -> fst row !! 0 <= value) (pairs taxtable)       
        result = case rows of 
                    [] -> taxtable !! 0
                    xs -> snd $ last rows

{- 
   This is useful for Brazil income tax calculation

  [(Gross Salary  – Deduction - Social Security ) • Aliquot – Deduction] = IRRF 
  [(Salário Bruto – Dependentes – INSS) • Alíquota – Dedução] =

-}
incometax taxtable income  = amount--(tax, aliquot, discount)
                where
                
                row = taxsearch taxtable income                
                aliquot = row !! 1
                discount = row !! 2                
                amount = income*(aliquot/100.0) - discount

{- Progressive Tax System -}
israeltaxbrackets = [
    [0,          0],
    [ 5070.0, 10.0],
    [ 8660.0, 14.0],
    [14070.0, 23.0],
    [21240.0, 30.0],
    [40230.0, 33.0],
    [above  , 45.0]
    ]                    

taxOfIsrael     = progressivetax israeltaxbrackets
taxRateOfIsrael = taxrate taxOfIsrael

braziltaxbrackets = [
    [1787.77,    0,   0.00],
    [2679.29,  7.5, 134.48],
    [3572.43, 15.0, 335.03],
    [4463.81, 22.5, 602.96],
    [above,    27.5, 826.15]
   ]


taxOfBrazil = incometax braziltaxbrackets
taxRateOfBrazil = taxrate  taxOfBrazil



{- 
    Unit test of a function of numerical input and output.
    
    input       - Unit test case values             [t1, t2, t2, e5]
    expected    - Expected value of each test case  [e1, e2, e3, e4]
    tol         - Tolerance 1e-3 typical value 
    f           - Function:                         error_i = abs(e_i-t_i)
    
    Returns true if in all test cases  error_i < tol
-}
testCaseNumeric :: (Num a, Ord a) => [a1] -> [a] -> a -> (a1 -> a) -> Bool
testCaseNumeric input expected tol f = all (\t -> t && True) ( zipWith (\x y -> abs(x-y) < tol) (map f input) expected )

testIsraelTaxes = testCaseNumeric  
    [5000, 5800, 9000, 15000, 50000]
    [500.0,609.2,1087.8,2532.9,15068.1]
    1e-3 taxOfIsrael

> testIsraelTaxes 
True
> 
> 
> taxOfIsrael 5000
500.0
> taxOfIsrael 5800
609.2
> taxOfIsrael 1087.8
108.78
> taxOfIsrael 15000.0
2532.9
> taxOfIsrael 50000.0
15068.1
> 
> taxRateOfIsrael 5000
10.0
> taxRateOfIsrael 5800
10.50344827586207
> taxRateOfIsrael 15000
16.886
> taxRateOfIsrael 50000
30.1362

```

Sources: 
    * http://ayende.com/blog/108545/the-tax-calculation-challenge
    * http://gghez.com/c-net-implementation-of-a-progressive-tax-system/




### Small DSL Domain Specific Language

  
Simple DSL for describing cups of Starbucks coffee and computing prices (in dollars). 
Example taken from: http://www.fssnip.net/9w 


starbuck_dsl.hs

```haskell
data Size  = Tall | Grande | Venti
            deriving (Eq, Enum, Read, Show, Ord)
 
data Drink = Latte | Cappuccino | Mocha | Americano            
            deriving (Eq, Enum, Read, Show, Ord)

data Extra = Shot | Syrup
            deriving (Eq, Enum, Read, Show, Ord)

data Cup = Cup {
                cupDrink :: Drink,
                cupSize  :: Size,
                cupExtra :: [Extra]         
               }
               deriving(Eq, Show, Read)

{-
 -                  Table in the format:
 -                 -------------------
 -                  tall, grande, venti 
 -    Latte         p00   p01     p02
 -    Cappuccino    p10   p11     p12
 -    Mocha         p20   p21     p22
 -    Amaericano    p30   p31     p32
 -}

table = [
    [2.69, 3.19, 3.49],
    [2.69, 3.19, 3.49],
    [2.99, 3.49, 3.79],
    [1.89, 2.19, 2.59]
    ]    


extraPrice :: Extra -> Double
extraPrice Syrup = 0.59
extraPrice Shot  = 0.39

priceOfcup cup =  baseprice + extraprice
            where
            drinkrow = table !!  fromEnum  (cupDrink cup)
            baseprice   = drinkrow !!  fromEnum  (cupSize cup)
            extraprice = sum $ map extraPrice (cupExtra cup)
            


{- Constructor of Cup -}
cupOf drink size extra = Cup { 
                             cupSize = size, 
                             cupDrink = drink, 
                             cupExtra = extra}

drink_options = [ Latte, Cappuccino, Mocha, Americano]
size_options  = [ Tall, Grande, Venti]  
extra_options = [[], [Shot], [Syrup], [Shot, Syrup]]

cup_combinations =  
            [ cupOf drink size extra | drink <- drink_options, size <- size_options, extra <- extra_options]

```

Example:


```haskell
> :load starbucks_dsl.hs 
[1 of 1] Compiling Main             ( starbucks_dsl.hs, interpreted )
Ok, modules loaded: Main.
> 
> 

> let myCup = cupOf Latte Venti [Syrup]
> let price = priceOfcup myCup 
> myCup 
Cup {cupDrink = Latte, cupSize = Venti, cupExtra = [Syrup]}
> price
4.08
> 

> priceOfcup (cupOf Cappuccino Tall [Syrup, Shot])
3.67
> 

> let cups = [ cupOf Americano Venti extra |  extra <- extra_options]
> cups
[Cup {cupDrink = Americano, cupSize = Venti, cupExtra = []},
Cup {cupDrink = Americano, cupSize = Venti, cupExtra = [Shot]},
Cup {cupDrink = Americano, cupSize = Venti, cupExtra = [Syrup]},
Cup {cupDrink = Americano, cupSize = Venti, cupExtra = [Shot,Syrup]}]
> 

> let prices = map priceOfcup cups
> prices
[2.59,2.98,3.1799999999999997,3.57]
> 

> let cupPrices = zip cups prices
> cupPrices
[(Cup {cupDrink = Americano, cupSize = Venti, cupExtra = []},2.59),
(Cup {cupDrink = Americano, cupSize = Venti, cupExtra = [Shot]},2.98),
(Cup {cupDrink = Americano, cupSize = Venti, cupExtra = [Syrup]},3.1799999999999997),
(Cup {cupDrink = Americano, cupSize = Venti, cupExtra = [Shot,Syrup]},3.57)]
> 

```

#### String Processing

<!--
@TODO: Add String Processing Examples
-->

## Libraries

### System Programming in Haskell

**Directory**

Get current Directory
```
> import System.Directory
> 
> getCurrentDirectory 
"/home/tux/PycharmProjects/Haskell"
> 
```

Change Current Directory
```haskell
> import System.Directory
> 
> setCurrentDirectory "/"
> 
> getCurrentDirectory 
"/"
> 
getCurrentDirectory :: IO FilePath
> 
> 
> fmap (=="/") getCurrentDirectory 
True
> 
> liftM (=="/") getCurrentDirectory 
True
> 
```

List Directory Contents
```haskell
> import System.Directory
>
>  getDirectoryContents "/usr"
[".","include","src","local","bin","games","share","sbin","lib",".."]
> 
> :t getDirectoryContents 
getDirectoryContents :: FilePath -> IO [FilePath]
> 
```

Special Directories Location
```haskell
> getHomeDirectory
"/home/tux"
> 
> getAppUserDataDirectory "myApp"
"/home/tux/.myApp"
> 
> getUserDocumentsDirectory
"/home/tux"
> 
```

**Running External Commands**

```haskell
> import System.Cmd
> 
> :t rawSystem
rawSystem :: String -> [String] -> IO GHC.IO.Exception.ExitCode
> 
> rawSystem "ls" ["-l", "/usr"]
total 260
drwxr-xr-x   2 root root 118784 Abr 26 03:38 bin
drwxr-xr-x   2 root root   4096 Abr 10  2014 games
drwxr-xr-x 131 root root  36864 Mar 11 01:38 include
drwxr-xr-x 261 root root  53248 Abr 14 16:46 lib
drwxr-xr-x  10 root root   4096 Dez  2 18:55 local
drwxr-xr-x   2 root root  12288 Abr  3 13:28 sbin
drwxr-xr-x 460 root root  20480 Abr 26 03:38 share
drwxr-xr-x  13 root root   4096 Jan 13 21:03 src
ExitSuccess
>
```

**Reading input from a system command in Haskell**

This command executes ls -la and gets the output.

```haskell
import System.Process
test = readProcess "ls" ["-a"] ""


> import System.Process
> let test = readProcess "ls" ["-a"] ""
> 
> :t test
test :: IO String
> 
> test >>= putStrLn 
.
..
adt2.py
adt.py
build.sh
build_zeromq.sh
clean.sh
codes
comparison.ods
dict.sh
ffi
figure1.png
.git


```

### Data.Time

#### System 

#### Get current year / month / day in Haskell

UTC time:

Note that the UTC time might differ from your local time depending on the timezone.

```haskell
import Data.Time.Clock
import Data.Time.Calendar

main = do
    now <- getCurrentTime
    let (year, month, day) = toGregorian $ utctDay now
    putStrLn $ "Year: " ++ show year
    putStrLn $ "Month: " ++ show month
    putStrLn $ "Day: " ++ show day
```

#### Get Current Time

Local time:

It is also possible to get your current local time using your system’s default timezone:

```haskell
import Data.Time.Clock
import Data.Time.Calendar
import Data.Time.LocalTime

main = do
    now <- getCurrentTime
    timezone <- getCurrentTimeZone
    let zoneNow = utcToLocalTime timezone now
    let (year, month, day) = toGregorian $ localDay zoneNow
    putStrLn $ "Year: " ++ show year
    putStrLn $ "Month: " ++ show month
    putStrLn $ "Day: " ++ show day
```


```haskell
import Data.Time.Clock
import Data.Time.LocalTime

main = do
    now <- getCurrentTime
    timezone <- getCurrentTimeZone
    let (TimeOfDay hour minute second) = localTimeOfDay $ utcToLocalTime timezone now
    putStrLn $ "Hour: " ++ show hour
    putStrLn $ "Minute: " ++ show minute
    -- Note: Second is of type @Pico@: It contains a fractional part.
    -- Use @fromIntegral@ to convert it to a plain integer.
    putStrLn $ "Second: " ++ show second
```

#### Documentation By Examples - GHCI shell

##### Date Time Manipulation

```haskell
import Data.Time

> :t getCurrentTime
getCurrentTime :: IO UTCTime
> 


> t <- getCurrentTime
> t
2015-03-04 23:22:39.046752 UTC
> 

> :t t
t :: UTCTime


> today <- fmap utctDay getCurrentTime 
> today
2015-03-04
> :t today
today :: Day
> 
> 

>  let (year, _, _) = toGregorian today
> year
2015
> 

> :t fromGregorian 2015 0 0
fromGregorian 2015 0 0 :: Day

> fromGregorian 2015 0 0
2015-01-01
> 

> diffDays today (fromGregorian year 0 0)
62
> 

> import Text.Printf
>
> tm <- getCurrentTime
>  let (year, month, day) = toGregorian (utctDay tm)
> year
2015
> month
3
> day
4
> 

> printf "The current date is %04d %02d %02d\n" year month day
The current date is 2015 03 04


> import System.Locale
> 
> fmap (formatTime defaultTimeLocale "%Y-%m-%d") getCurrentTime
"2015-03-04"
> 
> 

```

##### Difference between two dates

```haskell

> import Data.Time
> import Data.Time.Clock.POSIX
> 

> let bree = UTCTime (fromGregorian 1981 6 16) (timeOfDayToTime $ TimeOfDay 4 35 25) -- 1981-06-16 04:35:25 UTC
> bree
1981-06-16 04:35:25 UTC
> 


> let nat  = UTCTime (fromGregorian 1973 1 18) (timeOfDayToTime $ TimeOfDay 3 45 50) -- 1973-01-18 03:45:50 UTC
> nat
1973-01-18 03:45:50 UTC
> 


> 
> let bree' = read "1981-06-16 04:35:25" :: UTCTime
> bree'
1981-06-16 04:35:25 UTC
> :t bree'
bree' :: UTCTime
> 
> let nat'  = read "1973-01-18 03:45:50" :: UTCTime
> 
> nat'
1973-01-18 03:45:50 UTC
> 


> difference = diffUTCTime bree nat / posixDayLength
> difference 
3071.03443287037s
> 

>  "There were " ++ (show $ round difference) ++ " days between Nat and Bree"
"There were 3071 days between Nat and Bree"
> 
```

##### Day in a Week/Month/Year or Week Number

```haskell

> import Data.Time
> import Data.Time.Calendar.MonthDay
> import Data.Time.Calendar.OrdinalDate
> import System.Locale

> :t fromGregorian
fromGregorian :: Integer -> Int -> Int -> Day

> let (year, month, day) = (1981, 6, 16) :: (Integer , Int , Int )
> 
> let date = (fromGregorian year month day)
> date
1981-06-16
> 
> let (week, week_day) = sundayStartWeek date
> week
24
> week_day
2
> 

> let (year_, year_day) = toOrdinalDate date
> year_
1981
> year_day
167
> 


> let (week_day_name, _) = wDays defaultTimeLocale !! week_day
> week_day_name
"Tuesday"
> 

> :t defaultTimeLocale 
defaultTimeLocale :: TimeLocale
> 
> defaultTimeLocale 
TimeLocale {wDays = [("Sunday","Sun"),("Monday","Mon"),("Tuesday","Tue"),("Wednesday","Wed"),("Thursday","Thu"),("Friday","Fri"),("Saturday","Sat")], months = [("January","Jan"),("February","Feb"),("March","Mar"),("April","Apr"),("May","May"),("June","Jun"),("July","Jul"),("August","Aug"),("September","Sep"),("October","Oct"),("November","Nov"),("December","Dec")], intervals = [("year","years"),("month","months"),("day","days"),("hour","hours"),("min","mins"),("sec","secs"),("usec","usecs")], amPm = ("AM","PM"), dateTimeFmt = "%a %b %e %H:%M:%S %Z %Y", dateFmt = "%m/%d/%y", timeFmt = "%H:%M:%S", time12Fmt = "%I:%M:%S %p"}
> 
> 
```

##### Parsing Dates and Times from Strings

```haskell
> import Data.Time
> import Data.Time.Format
> import Data.Time.Clock.POSIX
> import System.Locale

> let day:: Day ; day = readTime defaultTimeLocale "%F" "1998-06-03"
> 
> day
1998-06-03
> 

```

##### Printing a Date

```haskell
> import Data.Time
> import Data.Time.Format
> import System.Locale
> 
> now <- getCurrentTime
> :t now
now :: UTCTime
> 
> formatTime defaultTimeLocale "The date is %A (%a) %d/%m/%Y" now
"The date is Wednesday (Wed) 04/03/2015"
> 
> 

> let t = do now <- getCurrentTime ; return $ formatTime defaultTimeLocale "The date is %A (%a) %d/%m/%Y" now
> t
"The date is Wednesday (Wed) 04/03/2015"
> 


```


Credits: 

* http://techoverflow.net/blog/2014/06/13/get-current-year-month-day-in-haskell/
* http://techoverflow.net/blog/2014/08/24/get-current-hour-minute-second-in-haskell/
* http://pleac.sourceforge.net/pleac_haskell/datesandtimes.html


## Miscelanious

### Haskell IDEs and Text Editors


<!--
@TODO: Show Haskell IDEs text editors and features
-->

### GHCI configuration file

The ghci configuration file allows the user to create custom commands and 
customize the ghci shell. The file is in the directory ~/.ghci in Unix systems 
like Linux and OSX.

Example: ~/.ghci
```
import System.Directory ( getCurrentDirectory)
import System.Process (readProcess)

:set -hide-package mtl

:set prompt "\x1b[32m>\x1b[0m " -- set the shell prompt to print λ (lambda)

:def hoogle \s -> return $ ":! hoogle --count=15 \"" ++ s ++ "\""

let xclip_ =  readProcess "xclip" ["-o", "-selection", "clipboard"] ""

let __savePasted = do {  code <-  readProcess "xclip" ["-o", "-selection", "clipboard"] ""  ;  putStrLn 

code ; writeFile "/tmp/haskTemp.hs" code}

let pwd = getCurrentDirectory >>= putStrLn

:def paste (\_ -> __savePasted >> return ":load /tmp/haskTemp.hs" )
:def pwd (\_ -> pwd >> return "")

```

It requires hoogle to be installed on Linux: (sudo apt-get install hoogle)
on Ubuntu.

Examples:

```
:paste - Paste code block in clipboard and compiles it in ghci
:pwd   - Show Current Directory
```

```haskell

> :pwd
/home/tux/PycharmProjects/Haskell
> 
> 

> :hoogle getCurrentDirectory
Directory getCurrentDirectory :: IO FilePath
System.Directory getCurrentDirectory :: IO FilePath
> 


> :paste
import Data.Time.Clock
import Data.Time.Calendar
import Data.Time.LocalTime

main = do
    now <- getCurrentTime
    timezone <- getCurrentTimeZone
    let zoneNow = utcToLocalTime timezone now
    let (year, month, day) = toGregorian $ localDay zoneNow
    putStrLn $ "Year: " ++ show year
    putStrLn $ "Month: " ++ show month
    putStrLn $ "Day: " ++ show day
[1 of 1] Compiling Main             ( /tmp/haskTemp.hs, interpreted )
Ok, modules loaded: Main.
> 
> main
Year: 2015
Month: 4
Day: 26
> 


```


### Troubleshooting

#### Importing Ambigous Modules in GHCi

```haskell
> import Control.Monad.State

<no location info>:
    Ambiguous module name `Control.Monad.State':
      it was found in multiple packages: monads-tf-0.1.0.2 mtl-2.2.1
> 

> :set -hide-package mtl
> import Control.Monad.State
> 
```

Solution: Add the line to ~/.ghci

```
:set -hide-package mtl
```


## Documentation and Learning Materials


### Code Search Engine

Haskell API search engine, which allows you to search many 
standard Haskell libraries by either function name, or by approximate type signature. 

![](https://www.haskell.org/hoogle/res/hoogle.png)

* [Hoogle](https://www.haskell.org/hoogle)

* https://www.haskell.org/documentation

Dohaskell is a tagged Haskell learning resources index. U

* http://www.dohaskell.com/

### Libraries Documentation

#### Prelude

**Standard Library Prelude.hs**

Prelude.hs is the standard library loaded when Haskell starts.

* [Prelude - Standard defined functions documentation](http://hackage.haskell.org/package/base-4.7.0.2/docs/Prelude.html#v:getContents)
* [Prelude Source Code](https://www.haskell.org/onlinereport/standard-prelude.html)


* [Prelude.hs - Examples of How to use prelude functions](http://www.cse.unsw.edu.au/~en1000/haskell/inbuilt.html)

Nice and precise description of Haskell Libraries:

* [The Haskell 2010 Libraries Part I](https://www.haskell.org/onlinereport/haskell2010/haskellpa1.html)
* [The Haskell 2010 Libraries Part II](https://www.haskell.org/onlinereport/haskell2010/haskellpa2.html#x20-192000II)

* http://hackage.haskell.org/packages/archive/pkg-list.html

#### Type Classe

* http://www.haskell.org/haskellwiki/Typeclassopedia

**Monads**

* http://www.haskell.org/haskellwiki/All_About_Monads
* http://www.haskell.org/haskellwiki/IO_inside
* http://en.wikibooks.org/wiki/Haskell/Understanding_monads


#### Online Books

* [Real-World Haskell by Bryan O'Sullivan et al.](http://book.realworldhaskell.org)
* [Learn You a Haskell for Great Good!](http://learnyouahaskell.com/chapters)
* [Haskell Wikibook](http://en.wikibooks.org/wiki/Haskell)
* [Gentle Introduction To Haskell, version 98](https://www.haskell.org/tutorial/)

#### Books

* [Haskell Data Analysis Cookbook](http://haskelldata.com/)
* [Parallel and Concurrent Programming in Haskell, By Simon Marlow](http://chimera.labs.oreilly.com/books/1230000000929)


#### Papers and Articles

Papers

* [Why functional programming still matters by John Hughes](http://www.cse.chalmers.se/~rjmh/Papers/whyfp.pdf)
* [Composing contracts: an adventure in financial engineering ](http://research.microsoft.com/en-us/um/people/simonpj/Papers/financial-contracts/contracts-icfp.htm) - Simon Peyton Jones et al.
* [Monads for functional programming- Philip Wadler, University of Glasgow?](http://homepages.inf.ed.ac.uk/wadler/papers/marktoberdorf/baastad.pdf)
* [Learn Physics by Programming in Haskell - Scott N. Walck (Lebanon Valley College, Annville, Pennsylvania, USA) ](http://arxiv.org/abs/1412.4880)

Repositories of Papers:

* [Phd. Philip Wadler Papers](http://homepages.inf.ed.ac.uk/wadler/)
* [Simon Peyton Jones: papers](http://research.microsoft.com/en-us/um/people/simonpj/papers/papers.html)
* [Generic Haskell publications/papers](http://www.cs.uu.nl/research/projects/generic-haskell/publications.html)

* [Research papers/Functional pearls](https://wiki.haskell.org/Research_papers/Functional_pearls)

* [Great Works in Programming Languages](http://www.cis.upenn.edu/~bcpierce/courses/670Fall04/GreatWorksInPL.shtml)

Journal:
* [Journal of Functional Programming](http://journals.cambridge.org/action/displayJournal?jid=JFP)

Articles:

* [Why the world needs Haskell](http://www.devalot.com/articles/2013/07/why-haskell.html)
* http://paulkoerbitz.de/posts/Why-I-love-Haskell.html


#### Selected Wikipedia Articles

Selected Wikipedia Pages:

* [List of functional programming topics](http://en.wikipedia.org/wiki/List_of_functional_programming_topics)
* [Comparison of Functional Programming Languages](http://en.wikipedia.org/wiki/Comparison_of_functional_programming_languages)
* [Functional programming](http://en.wikipedia.org/wiki/Functional_programming)


* [Declarative programming](http://en.wikipedia.org/wiki/Declarative_programming)
* [Aspect-oriented programming](http://en.wikipedia.org/wiki/Aspect-oriented_programming)

**Pure Functions/ Lambda Calculus/ Closure/ Currying**

* [Lambda calculus](http://en.wikipedia.org/wiki/Lambda_calculus)
* [Higher-order function](http://en.wikipedia.org/wiki/Higher-order_function)
* [Referential transparency (computer science)](http://en.wikipedia.org/wiki/Referential_transparency_(computer_science))
* [Closure (computer programming)](http://en.wikipedia.org/wiki/Closure_(computer_programming))
* [Callback (computer programming)](http://en.wikipedia.org/wiki/Callback_(computer_programming))
* [Coroutine](http://en.wikipedia.org/wiki/Coroutine)

**Evaluation**

* [Eager Evaluation](http://en.wikipedia.org/wiki/Eager_evaluation)
* [Lazy Evaluation](http://en.wikipedia.org/wiki/Lazy_evaluation)
* [Short-circuit evaluation](http://en.wikipedia.org/wiki/Short-circuit_evaluation)

**Monads**

* [Monads Functional Programming](http://en.wikipedia.org/wiki/Monad_(functional_programming))
* [Haskell/Understanding monads](http://en.wikibooks.org/wiki/Haskell/Understanding_monads)
* [Monad transformer](http://en.wikipedia.org/wiki/Monad_transformer)

**Continuations**

* [Continuation](http://en.wikipedia.org/wiki/Continuation)
* [Continuation-passing style](http://en.wikipedia.org/wiki/Continuation-passing_style)

#### Community

* http://reddit.com/r/haskell
* http://www.reddit.com/r/haskellquestions
* http://stackoverflow.com/questions/tagged?tagnames=haskell
* irc.freenode.net #haskell on Freenode

Haskell Wiki             

* http://www.haskell.org/haskellwiki/Category:Tutorials
* http://www.haskell.org/haskellwiki/Category:Mathematics
* http://www.haskell.org/haskellwiki/Category:FAQ
* http://www.haskell.org/haskellwiki/Category:Communitys



#### References by Subject


* http://www.cis.upenn.edu/~matuszek/Concise%20Guides/Concise%20Haskell98.html
* http://www.cs.arizona.edu/~collberg/Teaching/372/2009/Handouts/Handout-11.pdf
* http://en.wikibooks.org/wiki/Yet_Another_Haskell_Tutorial/Language_basics
* https://courses.cs.washington.edu/courses/cse505/01au/functional/haskell-examples.txts


Toolset
* <http://en.wikibooks.org/wiki/Haskell/Using_GHCi_effectively>

List

* <https://wiki.haskell.org/How_to_work_on_lists>
* <https://hackage.haskell.org/package/base-4.2.0.1/docs/Data-List.html#v%3Atail>

List Comprehension

* <http://www.cs.nott.ac.uk/~gmh/chapter5.ppt>
* <http://www.cs.arizona.edu/~collberg/Teaching/372/2005/Html/Html-13/index.html>
* <http://zvon.org/other/haskell/Outputsyntax/listQcomprehension_reference.html>

Foreign Function Interface - FFI:
* <http://en.wikibooks.org/wiki/Haskell/FFI>

Misc:

* <https://www.fpcomplete.com/blog/2013/06/haskell-from-c>
* <https://wiki.haskell.org/Haskell_programming_tips>
* <http://bayleshanks.com/tutorials-haskell>

Lambda Calculus Concepts
* <https://wiki.haskell.org/Anonymous_function>
* <https://wiki.haskell.org/Closure>
* <https://wiki.haskell.org/Beta_reduction>

Data Types:
* <http://en.wikibooks.org/wiki/Haskell/More_on_datatypes>
* <https://www.fpcomplete.com/school/starting-with-haskell/introduction-to-haskell/2-algebraic-data-types>


Dollar Sign Operator: $
* <http://stackoverflow.com/questions/940382/haskell-difference-between-dot-and-dollar-sign>
* <http://snakelemma.blogspot.com.br/2009/12/dollar-operator-in-haskell.html>
* <http://lambda.jstolarek.com/2012/03/function-composition-and-dollar-operator-in-haskell/>

Pipelining:
* <http://stackoverflow.com/questions/1457140/haskell-composition-vs-fs-pipe-forward-operator>
* <http://stackoverflow.com/questions/4090168/is-there-an-inverse-of-the-haskell-operator>

Control:
* <http://hackage.haskell.org/package/base-4.7.0.2/docs/Control-Monad.html#v:forM>
* <http://en.wikibooks.org/wiki/Haskell/Control_structures>


#### Video Lectures

**Dr. Erik Meijer Series: Functional Programming Fundamentals**

All lectures: [C9 Lectures: Erik Meijer - Functional Programming Fundamentals Video Series](http://channel9.msdn.com/Series/C9-Lectures-Erik-Meijer-Functional-Programming-Fundamentals)

Haskell Videos

* [Function Definition    - Chapter 4 of 13](https://www.youtube.com/watch?v=fQU99SJdWGY)
* [List Comprehensions    - Chapter 5 of 13](https://www.youtube.com/watch?v=cdPyykm2-gg)
* [Recursive functions    - Chapter 6 of 13](https://www.youtube.com/watch?v=2ECvUT3nbqk)
* [Higher Order Functions - Chapter 7 of 13](https://www.youtube.com/watch?v=YRTQkBO2v-s)
* [Functional Parsers     - Chapter 8 of 13](https://www.youtube.com/watch?v=OrAVS4QbMqo)


**Channel 9 MSDN Videos about Functional Programming**

* http://channel9.msdn.com/Tags/functional+programming


**Haskell Course by Phd. Philip Wadler (Youtube)**

* [Haskell Course by Phd. Philip Wadler](https://www.youtube.com/playlist?list=PLtRG9GLtNcHBv4cuh2w1cz5VsgY6adoc3)

* [Phillip Wadler's home page](http://homepages.inf.ed.ac.uk/wadler/)


**Prof. Dr. Jürgen Giesl**

Credits:  * [Issue: seoulgithub](https://github.com/caiorss/Functional-Programming/issues/20)

* [Prof. Dr. Jürgen Giesl's home page](http://verify.rwth-aachen.de/giesl/) (In German.)
* [Lectures in English](https://videoag.fsmpi.rwth-aachen.de/?course=12ss-funkprog)


In this course, you will learn (Compiler+Assembly+Language) together in a single course. So, for a CS background person, this course will be highly beneficiary since Compiler and Assembler both are known to him/her. 

**Haskell From Scratch (Youtube)**

Creating complete programs in Haskell from the ground up.

* [Haskell From Scratch](https://www.youtube.com/playlist?list=PLxj9UAX4Em-Ij4TKwKvo-SLp-Zbv-hB4B)


**Learn you a haskell by Michał Drozd (Youtube)**

* [Learn you a haskell by Michal Drozd](https://www.youtube.com/playlist?list=PLPqPwGvHPSZB-urE6QFjKYt6AGXcZqJUh)


**Loop School**

Good video lectures about Category theory and Haskell programing language.

* http://school.looprecur.com/

