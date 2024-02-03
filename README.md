We have variants of Python that can use Python libs: welcome to
**Dogelang**, **Mochi**, **Hy**, **Coconut** and **Hask**.

We can also have languages that target the Python platform without
being necessarily compatible with Python, and domain-specific
languages.

For more ressources related to functional programming in Python, see
the [Awesome Functional Python](https://github.com/sfermigier/awesome-functional-python)
list.

<!-- generetae the toc with npm install markdown-toc and running markdown-toc -i README.md -->

<!-- toc -->

<!-- markdown-toc start - Don't edit this section. Run M-x markdown-toc-refresh-toc -->
**Table of Contents**

- [Variants of Python. They can use Python libs.](#variants-of-python-they-can-use-python-libs)
    - [Dg - it's a Python ! No, it's a Haskell !](#dg---its-a-python--no-its-a-haskell-)
    - [Hissp - It's Python with a Lissp!](#hissp---its-python-with-a-lissp)
    - [Hy - A dialect of Lisp that's embedded in Python](#hy---a-dialect-of-lisp-thats-embedded-in-python)
    - [Basilisp -  a Clojure-compatible(-ish) Lisp dialect targeting Python 3.8+](#basilisp----a-clojure-compatible-ish-lisp-dialect-targeting-python-38)
    - [Mochi - Dynamically typed programming language for functional programming and actor-style programming](#mochi---dynamically-typed-programming-language-for-functional-programming-and-actor-style-programming)
    - [Coconut - Simple, elegant, Pythonic functional programming](#coconut---simple-elegant-pythonic-functional-programming)
    - [Hask -  Haskell language features and standard libraries in pure Python.](#hask----haskell-language-features-and-standard-libraries-in-pure-python)
    - [Rabbit - a functional language on top of Python (discontinued in favor of Coconut)](#rabbit---a-functional-language-on-top-of-python-discontinued-in-favor-of-coconut)
    - [MakrellPy - a functional language with metaprogramming support and simplistic syntax](#makrellpy---a-functional-language-with-metaprogramming-support-and-simplistic-syntax)
- [Implemented in another language but target the Python platform. They can use Python libs.](#implemented-in-another-language-but-target-the-python-platform-they-can-use-python-libs)
    - [Erg - General statically typed multiparadigm rusty programming language](#erg---general-statically-typed-multiparadigm-rusty-programming-language)
- [Other languages that target the Python platform](#other-languages-that-target-the-python-platform)
    - [Haxe, the cross-platform toolkit](#haxe-the-cross-platform-toolkit)
- [Domain-specific languages](#domain-specific-languages)
    - [ProbLog. Probabilistic Logic Programming.](#problog-probabilistic-logic-programming)
    - [PyDatalog. Logic programming to use inside your Python program.](#pydatalog-logic-programming-to-use-inside-your-python-program)
    - [RBQL: SQL dialect with Python expressions](#rbql-sql-dialect-with-python-expressions)
- [Other languages built in RPython](#other-languages-built-in-rpython)
    - [Monte - secure distributed computation](#monte---secure-distributed-computation)
    - [Pixie, a lightweight and native lisp](#pixie-a-lightweight-and-native-lisp)
    - [RSqueak, a Squeak/Smalltalk VM written in RPython](#rsqueak-a-squeaksmalltalk-vm-written-in-rpython)

<!-- markdown-toc end -->

<!-- tocstop -->

# Variants of Python. They can use Python libs.

The following languages can make use of the Python libraries.

## Dg - it's a Python ! No, it's a Haskell !

![NOT'REALLY®](https://pyos.github.io/dg/images/seriousdawg.jpg)

Dogelang  |  
--- | ---
sources |[<https://github.com/pyos/dg>](https://github.com/pyos/dg)
doc | [<https://pyos.github.io/dg/>](https://pyos.github.io/dg/)
v1 ? | yes, april 2015
created | june, 2012

-   compiles to CPython 3.4. Dg is an alternative syntax to Python 3.
-   compatible with all the libraries
-   runs on PyPy

### Language features

-   function calls without parenthesis:

```livescript
print "wow" "two lines" sep: "\n"
```

-   reverse pipe operator:

```livescript
print $ "> {}: {}".format "Karkat" "Reference something other than Doge"
```

-   pipe and reverse pipe (on the same line, unlike Mochi)

```livescript
print <| 'What' + 'ever.' : 'This is the same thing ' + 'in a different direction.' |> print
```

-   function notation (arrow `->` notation)

```livescript
function = arg1 arg2 -> : print (arg1.replace "Do " "Did ") arg2 sep: ", " end: ".\n"
function "Do something" "dammit"
```

-   infix notation (with backticks)
-   function composition (with `<-`)
-   first class operators

```livescript
f = (+)
f 1 2 == 3
```

-   partial application (and `bind` is `functools.partial`)

```livescript
f = (2 *)
f 10 == 20
```

-   new functional builtins: `foldl` and `foldl1`, `scanl`, `flip`,
    `takewhile` and `dropwhile` (from `itertools`), `take` and `drop`,
    `iterate`, `head` and `fst`, `tail`, `snd`, `last` and `init`.
-   decorators don't need special syntax, they're just called with a
    function

        wtf = the~decorator~ $ ->

### Install

        pip3 install git+<https://github.com/pyos/dg>

### Editors

Editor |  
  --------- | --------------------------------------------------------------------------------
  Gedit |     [<https://github.com/pyos/dg-gedit/>](https://github.com/pyos/dg-gedit/)
  Sublime |   [<https://github.com/pyos/dg-textmate/>](https://github.com/pyos/dg-textmate/)

Pygments support.

### Example projects


Project |  
--- | ---
dogeweb , a functional web framework atop asyncio |   [<https://pyos.github.io/dogeweb/>](https://pyos.github.io/dogeweb/)


## Hissp - It's Python with a Lissp!

![](https://raw.githubusercontent.com/gilch/hissp/master/docs/hissp.svg)

> Hissp is a modular Lisp implementation that compiles to a functional subset of Python—Syntactic macro metaprogramming with full access to the Python ecosystem!

Hissp |  
-------------|------------------------------------------------------------------------
sources |      [<https://github.com/gilch/hissp>](https://github.com/gilch/hissp)
  doc   |       [https://hissp.readthedocs.io/](https://hissp.readthedocs.io/)
  v1 ?  |       no, v0.2 as of May 2021
  created|       2019
  discuss     | [gitter](https://gitter.im/hissp-lang/community)

The Hissp compiler is written in Python 3.8.

### Language features

> The Hissp compiler should include what it needs to achieve its goals, but no more. Bloat is not allowed.

> Hissp compiles to an unpythonic functional subset of Python.

> Hissp's basic macros are meant to be just enough to bootstrap native unit tests and demonstrate the macro system. They may suffice for small embedded Hissp projects, but you will probably want a more comprehensive macro suite for general use.

> You do not need Hissp installed to run the final compiled Python output


```lisp
(defmacro attach (target : :* args)
  "Attaches the named variables as attributes of the target.

  Positional arguments use the same name as the variable.
  Names after the ``:`` are key-value pairs.
  "
  (let (iargs (iter args)
        $target `$#target)
    (let (args (itertools..takewhile (lambda (a)
                                       (operator..ne a ':))
                                     iargs))
      `(let (,$target ,target)
         ,@(map (lambda (arg)
                  `(setattr ,$target ',arg ,arg))
                args)
         ,@(map (lambda (kw)
                  `(setattr ,$target ',kw ,(next iargs)))
                iargs)
         ,$target))))
```


## Hy - A dialect of Lisp that's embedded in Python

![](http://docs.hylang.org/en/stable/_images/hy-logo-small.png)

Hy |  
-------------|------------------------------------------------------------------------
sources |      [<https://github.com/hylang/hy/>](https://github.com/hylang/hy/)
  doc   |       [<http://hylang.org/>](http://hylang.org/)
  v1 ?  |       no
  created|       december, 2012
  online REPL |   [<https://try-hy.appspot.com/>](https://try-hy.appspot.com/)
  discuss     | [google group](https://groups.google.com/forum/#!forum/hylang-discuss)
  IRC         | `hy` on freenode

-   Hy compiles to Python bytecode (AST)
-   Hy can use python libraries, and we can import a Hy module into a
    Python program.

### Language features

-   it's python: context managers, named and keyword arguments, list
    comprehensions,...
-   macros, reader macros
-   threading macros (like Clojure), with `->` and `->>` (similar to
    pipes)

```lisp
(-> (read) (eval) (print) (loop))
```

```lisp
(import [sh [cat grep wc]])
(-> (cat "/usr/share/dict/words") (grep "-E" "^hy") (wc "-l"))  ; => 210
```

-   [anaphoric
    functions](http://docs.hylang.org/en/latest/contrib/anaphoric.html)

```lisp
(require hy.contrib.anaphoric)
(list (ap-map (* it 2) [1 2 3]))  ; => [2, 4, 6]
```

-   fraction literal (like Clojure)
-   unicode support (I mean for symbols)
-   pattern matching (in libraries, like
    [Hyskell](https://github.com/kirbyfan64/hyskell))
-   monads (in libraries, like [Hymn](https://github.com/pyx/hymn))

### Install

        pip install hy

### Editors

Editor |  
  ------- | --------------------------------------------------------------------------
  Emacs |   [<https://github.com/hylang/hy-mode>](https://github.com/hylang/hy-mode)
  All   |  lisp modes for any editor

### Example projects

Project |  
--- | ---
  Github trending |       [<https://github.com/trending/hy>](https://github.com/trending/hy)
  Live coding Blender |   [<https://github.com/chr15m/blender-hylang-live-code>](https://github.com/chr15m/blender-hylang-live-code)

### Good reads

Title |  
--- | ---
How Hy backported "yield from" to Python 2 |   [<http://dustycloud.org/blog/how-hy-backported-yield-from-to-python2/>](http://dustycloud.org/blog/how-hy-backported-yield-from-to-python2/)

## Basilisp -  a Clojure-compatible(-ish) Lisp dialect targeting Python 3.8+

Basilisp |  
  ---------|----------------------------------------------------------------
  sources  |[https://github.com/basilisp-lang/basilisp](https://github.com/basilisp-lang/basilisp)
  doc | [https://basilisp.readthedocs.io/en/latest/](https://basilisp.readthedocs.io/en/latest/)
  v1 ?  | no (as of 2024, Jan) but "generally stable at this point"
  created |  initial development release in 2018

### Language features

- Immutable data structures, backed by Immutables and Pyrsistent
- Strong emphasis on functional programming concepts
- Access to the vast array of existing Python libraries
- Seamless interoperability between Python code and Basilisp code
- Sophisticated REPL for REPL-based development

Planned features:

> Basilisp is still young and so lacks many features that more mature languages and runtimes might include. There are many such planned features that will hopefully improve the ergonomics of the project for new developers.

>  fundamental differences and omissions in Basilisp that make it differ from Clojure:

- Basilisp does not include Ref types or software transactional memory (STM) support.
- Basilisp does not include Agent support (support is tracked in #413).
- All Vars are reified at runtime and users may use the binding macro as in Clojure.
- Support for Clojure libs is planned.
- Type hints may be applied anywhere they are supported in Clojure (as the :tag metadata key), but the compiler does not currently use them for any purpose.

```lisp
(def
  ^{:doc      "Returns the second element in a Seq."
    :arglists '([seq])}
  second
  (fn* second [seq] (first (rest seq))))
```


## Mochi - Dynamically typed programming language for functional programming and actor-style programming

Mochi |  
  ---------|----------------------------------------------------------------
  sources  |[<https://github.com/i2y/mochi>](https://github.com/i2y/mochi)
  doc | [many examples](https://github.com/i2y/mochi/tree/master/examples)
  v1 ?  | no
  created |  v0.1 on december, 2014

-   translates to Python3's AST/bytecode

### Language features

-   Python-like syntax
-   pipeline operator (multiline ok)

```elixir
range(1, 31)
|> map(fizzbuzz)
|> pvector()
|> print()
```

-   tail-recursion optimization (self tail recursion only)
-   no loop syntax
-   re-assignments are not allowed in function definition
-   persisent data structures (using Pyrsistent)
-   Pattern matching / Data types, like algebraic data types
-   Syntax sugar of anonymous function definition (`->` notation and
    `$1` for the arguments)
-   Actor, like the actor of Erlang (using Eventlet)
-   Macro, like the traditional macro of Lisp
-   Anaphoric macros
-   Builtin functions includes functions exported by itertools module,
    recipes, functools module and operator module

### Install

        pip3 install mochi

### Editors

Editor |  
  ------|----------------------------------------------------------------------------------
  Atom  | [<https://github.com/i2y/language-mochi>](https://github.com/i2y/language-mochi)

### Good reads

* [Heny Müller's talk at EuroPython 2015](https://www.youtube.com/watch?v=bFqQd1eyY10)

## Coconut - Simple, elegant, Pythonic functional programming

Coconut |  
---------|  ------------------------------------------------------------------------
 sources |   [<https://github.com/evhub/coconut>](https://github.com/evhub/coconut)
 doc     | [<https://coconut.readthedocs.io>](https://coconut.readthedocs.io)
 v1 ?    |  yes, on june, 2016
 created |   february, 2015 (v0.1)

-   Coconut compiles to Python (not CPython bytecode, so it supports
    other Python implementations: PyPy, Jython, etc)
-   Coconut code runs on any major Python version, 2 or 3
-   all valid Python 3 is valid Coconut: you can write standard Python3
    in Coconut.

-   **ipython** / jupyter
    [support](http://coconut.readthedocs.io/en/master/DOCS.html#ipython-jupyter-support)
    (installed by default)

### Language features

-   pipelines

```livescript
(1, 2) |*> (+) |> sq |> print
```

For multiline pipes, surround them with parenthesis (python rule that
every newline inside parenthesis is ignored):

```coconut
(
    "hello"
    |> print
)
```

-   pattern matching (`match x in value:`), guards
-   algeabric data types
-   partial application (`$` sign right after a function name)

```elixir
expnums = map(pow$(2), range(5))
expnums |> list |> print
```

-   lazy lists (surround comma-separated lists with `(|` and `|)`)
-   destructuring assignment
-   function composition (with `..`)
```livescript
fog = f..g
```
-   prettier lambdas (`->` syntax)
-   parallel programming
-   tail recursion optimization
-   infix notation (like in Haskell with backticks)
-   underscore digits separators (`10_000_000`)
-   decorators support any expression
```
@ wrapper1 .. wrapper2 $(arg)
```
-   code pass through the compiler
-   ...

### Install

        pip install coconut

### Editors

-   Pygments support

Editor |  
--- | ---
Emacs | https://github.com/NickSeagull/coconut-mode
Sublime | https://github.com/evhub/sublime-coconut
Vim | https://github.com/manicmaniac/coconut.vim


## Hask -  Haskell language features and standard libraries in pure Python.

Hask |  
--- | ---
sources | [https://github.com/billpmurphy/hask](https://github.com/billpmurphy/hask)
doc | on github
v1 ? | no
created | july, 2015

Hask is a pure-Python, zero-dependencies library that mimics most of
the core language tools from Haskell, including:

- **Full Hindley-Milner type system** (with typeclasses) that will typecheck any function decorated with a Hask type signature. Also, typed functions can be **partially applied**.
```python
@sig(H/ "a" >> "b" >> "a")
def const(x, y):
    return x
```
- Easy creation of new **algebraic data types** and new typeclasses, with Haskell-like syntax
- **Pattern matching** with case expressions
```python
def fib(x):
    return ~(caseof(x)
                | m(0)   >> 1
                | m(1)   >> 1
                | m(m.n) >> fib(p.n - 1) + fib(p.n - 2))
```
- Automagical function **currying/partial application** and function composition
- Efficient, **immutable, lazily evaluated** List type with Haskell-style list comprehensions
- All your favorite syntax and control flow tools, including **operator sections**, **monadic error handling**, **guards**, and more
- Python port of (some of) the standard libraries from Haskell's base, including:
    - Algebraic datatypes from the Haskell Prelude, including Maybe and Either
    - Typeclasses from the Haskell base libraries, including Functor, Applicative, Monad, Enum, Num, and all the rest
    - Standard library functions from base, including all functions from Prelude, Data.List, Data.Maybe, and more


Features not yet implemented, but coming soon:

    - Python 3 compatibility
    - Better support for polymorphic return values/type defaulting
    - Better support for lazy evaluation (beyond just the List type and pattern matching)
    - More of the Haskell standard library (Control.* libraries, QuickCheck, and more)
    - Monadic, lazy I/O

### Install

    git clone https://github.com/billpmurphy/hask
    python setup.py install


## Rabbit - a functional language on top of Python (discontinued in favor of Coconut)

Rabbit |  
------ | ----------------------------------------------------------------------
sources |   [<https://github.com/evhub/rabbit>](https://github.com/evhub/rabbit)
doc  | no doc
v1 ?   |   yes, on oct, 2014. DISCONTINUED
created |  v0.1 on may, 2014

From the author's words:
([src](https://www.reddit.com/r/Python/comments/4owzu7/coconut_functional_programming_in_python/d4hhfw0))

> Coconut is my attempt to fix the mistakes I thought I made with
> Rabbit, namely:
>
> -   Coconut is compiled, while Rabbit is interpreted, making Coconut
>     much faster
> -   Coconut is an extension to Python, while Rabbit is a replacement,
>     making Coconut much easier to use

Quicksort:

``` {.txt}
qsort(l) = (
    qsort: (as ~ \x\(x @ x<=a)) ++ a ++ qsort: (as ~ \x\(x @ x>a))
    $ a,as = l
    ) @ len:l
```

## MakrellPy - a functional language with metaprogramming support and simplistic syntax

![](https://github.com/hcholm/makrell-py/blob/main/doc/makrell.png)

MakrellPy |  
--------|------------------------------------------------------------------------
sources |  [<https://github.com/hcholm/makrell-py>](https://github.com/hcholm/makrell-py)
v1 ?    |  no
created |  February, 2024

MakrellPy, part of the Makrell language family, is a general-purpose, functional and homiconic programming language with two-way Python interoperability, metaprogramming support and simplistic syntax. The language family is based on the Makrell Base Format, a general data format that can be used both for programming languages and data interchange. Other family members include MRON, a lightweight alternative to JSON, and MRML, a lightweight alternative to XML and HTML.

### Language features

- Compiles to Python AST, runs on Python with two-way interoperability.
- Simplistic syntax using the Makrell Base Format.
- Functional programming with multiline lambdas, partial application, and function composition.
- Metaprogramming support with custom operators, macros and custom metaprogramming functions.
- Homiconic programming with a simple and consistent syntax for data and code.
- Languages in the Makrell family can be embedded in each other while maintaining the base format.
- The Makrell package includes MRON and MRML support, an API for working with the Makrell Base Format and a basic language server supporting the Language Server Protocol.
- REPL, syntax highlighting and basic diagnostics support for Visual Studio Code.

### Sample code
```
{fun add [x y]
    x + y}

a = {add 2 3}
{print a}  # 5
a | print  # same, with pipe operator

f = [x y] -> {do
    {print "multiline lambda here"}
    x * y
}

{print {f 2 3}}  # function call

add3 = {f 3 _}  # partial application

2 | {+ 3} | {* 5}  # operators as functions

add3mul5 = add3 >> {* 5}  # function composition
```

### Install

    pip install makrell

### Editors

Editor |
------- | --------------------------------------------------------------------------
Visual Studio Code | [<https://marketplace.visualstudio.com/items?itemName=hcholm.vscode-makrell>](https://marketplace.
visualstudio.com/items?itemName=hcholm.vscode-makrell)
Other | MakrellPy is supported by the Language Server Protocol, so it should work with any editor that supports LSP.

# Implemented in another language but target the Python platform. They can use Python libs.


## Erg - General statically typed multiparadigm rusty programming language

![](https://github.com/erg-lang/erg/blob/main/assets/erg_logo_with_slogan.svg)

> A statically typed language that can deeply improve the Python ecosystem 

Erg |  
--- | ---
sources | [<https://github.com/erg-lang/erg>](https://github.com/erg-lang/erg)
doc | [https://erg-lang.github.io/](https://erg-lang.github.io/)
v1 ? | no, v0.4.2 as of September 2022
created | 2022

The Erg compiler is written in Rust.

### Language features

> Erg is a pure object-oriented language. Everything is an object; types, functions, and operators are all objects. On the other hand, Erg is also a functional language. Erg requires some kinds of markers to be placed on code that causes side effects or changes internal state, which can localize the complexity of code. This will greatly improve the maintainability of your code.

> Erg is internally compatible with Python and can import the Python API at zero cost.

```python
    # Functional style (immutable), same as `sorted(list)` in Python
    immut_arr = [1, 3, 2]
    assert immut_arr.sort() == [1, 2, 3]
    # Object-oriented style (mutable)
    mut_arr = ![1, 3, 2]
    mut_arr.sort!()
    assert mut_arr == [1, 2, 3]
    i = !1
    i.update! old -> old + 1
    assert i == 2

    # Functions cannot cause side effects
    inc i: Int! =
        i.update! old -> old + 1
    # SyntaxError: cannot call a procedural method in a function
    # hint: only methods of mutable types can change the state of objects

    # Code that uses a lot of side effects is redundant, so you will naturally write pure code
    Counter! = Inherit Int!
    Counter!.
        new i: Int = Self!::__new__ !i
        inc! ref! self =
            self.update! old -> old + 1

    c = Counter!.new 1
    c.inc!()
    assert c == 2
```


# Other languages that target the Python platform

## Haxe, the cross-platform toolkit

Haxe |  
--- | ---
sources | https://github.com/HaxeFoundation/haxe
official website | https://haxe.org/
doc | https://haxe.org/documentation/introduction/
online REPL |_http://try.haxe.org/
v1 ? | v3

Haxe is an open source toolkit that allows you to easily build
cross-platform tools and applications that target many mainstream
platforms (Python, ActionScript3, C++, C#, Flash, Java, Javascript,
NekoVM, PHP, Lua).

```haxe
class Test {
  static function main() {
    var people = [
      "Elizabeth" => "Programming",
      "Joel" => "Design"
    ];
    for (name in people.keys()) {
      var job = people[name];
      trace('$name does $job for a living!');
    }
  }
}
```
# Domain-specific languages

## ProbLog. Probabilistic Logic Programming.

Probabilistic logic programs are logic programs in which some of the
facts are annotated with probabilities.

ProbLog |  
--- | ---
official website | https://dtai.cs.kuleuven.be/problog/
sources | https://bitbucket.org/problog/problog
doc | http://problog.readthedocs.io/en/latest/
v1 ? | yes, even v2
online tutorial and REPL | https://dtai.cs.kuleuven.be/problog/tutorial.html

ProbLog is built with Python. Its only requirement is Python2.7 or 3.

One can [interact with ProbLog from within Python code](http://problog.readthedocs.io/en/latest/python.html).

### Install

    pip install problog

## PyDatalog. Logic programming to use inside your Python program.

PyDatalog |  
---       | ---
official website | https://sites.google.com/site/pydatalog/
sources          | https://github.com/pcarbonn/pyDatalog
doc              | https://sites.google.com/site/pydatalog/Online-datalog-tutorial
v1 ?             | v0.17 (january, 2016)
PyPy ?           | yes

pyDatalog adds the logic programming paradigm to Python. Logic
programmers can now use the extensive standard library of Python, and
Python programmers can now express complex algorithms quickly.


```python
from pyDatalog import pyDatalog
pyDatalog.create_terms('factorial, N')


factorial[N] = N*factorial[N-1]

factorial[1] = 1

print(factorial[3]==N)  # prints N=6
```

### Installation

`pip install pyDatalog`
`pip install sqlalchemy`

### Example projects

No examples found, only
[testimonials](https://sites.google.com/site/pydatalog/home/datalog-applications).


## RBQL: SQL dialect with Python expressions

RBQL |  
---       | ---
official website | https://rbql.org
sources          | https://github.com/mechatroner/RBQL
v1 ?             | no
PyPy ?           | pip install rbql

RBQL is both a library and a command line tool which provides SQL-like language with Python expressions  
RBQL is integrated into "Rainbow CSV" text editor plugins available for VSCode, Vim, Sublime, Atom  
Main Features:
* Allows to use Python expressions inside _SELECT_, _UPDATE_, _WHERE_ and _ORDER BY_ statements
* Result set of any query immediately becomes a first-class table on it's own
* Works out of the box, no external dependencies

#### Usage example:
```python
import rbql
input_table = [
    ['Roosevelt',1858,'USA'],
    ['Napoleon',1769,'France'],
    ['Dmitri Mendeleev',1834,'Russia'],
    ['Jane Austen',1775,'England'],
    ['Hayao Miyazaki',1941,'Japan'],
]
user_query = 'SELECT a.name, "birth century: {}".format(a.DOB // 100 + 1) WHERE a.name == "Roosevelt" or re.search("an", a.country, re.IGNORECASE) is not None ORDER BY random.random()'
output_table = []
warnings = []
rbql.query_table(user_query, input_table, output_table, warnings, input_column_names=['name', 'DOB', 'country'])
for record in output_table:
    print(','.join([str(v) for v in record]))
```


# Other languages built in RPython

## Monte - secure distributed computation

Monte is a "nascent dynamic programming language reminiscent of Python
and [E](http://erights.org/). It is based upon The Principle of Least
Authority (POLA), which governs interactions between objects, and a
capability-based object model, which grants certain essential safety
guarantees to all objects".

Monte |  
---   | ---
Sources | https://github.com/monte-language
Doc     | https://monte.readthedocs.io/en/latest/intro.html
v0.1 ?  | yes, v2016.1

Built on Pypy.


## Pixie, a lightweight and native lisp

Pixie |  
--- | ---
Sources | https://github.com/pixie-lang/pixie
Doc | Examples: https://github.com/pixie-lang/pixie/tree/master/examples
v0.1 ? | no
REPL, installer, test runner,… | https://github.com/pixie-lang/dust
IRC | `#pixie-lang` on Freenode

Pixie is built in
[RPython](https://pypy.readthedocs.io/en/latest/coding-guide.html),
the same language PyPy is written in, and as such "supports a fairly
fast GC and an amazingly fast tracing JIT".

Inspired by Clojure.

### Features

- Immutable datastructures
- Protocols first implementation
- Transducers at-the-bottom (most primitives are based off of reduce)
- A "good enough" JIT (implemented, tuning still a WIP, but not bad performance today)
- Easy FFI
- object system
- continuations, async I/O inspired by nodejs (see talk)
- Pattern matching (planned)

From the FAQ:

- Pixie implements its own virtual machine. It does not run on the
  JVM, CLR or Python VM. It implements its own bytecode, has its own
  GC and JIT. And it's small. Currently the interpreter, JIT, GC, and
  stdlib clock in at about 10.3MB once compiled down to an executable.
- The JIT makes some things fast. Very fast. Code like the following
  compiles down to a loop with 6 CPU instructions. While this may not
  be too impressive for any language that uses a tracing jit, it is
  fairly unique for a language as young as Pixie.

```lisp
;;  This code adds up to 10000 from 0 via calling a function that takes a variable number of arguments.
;;  That function then reduces over the argument list to add up all given arguments.

(defn add-fn [& args]
  (reduce -add 0 args))

(loop [x 0]
  (if (eq x 10000)
    x
    (recur (add-fn x 1))))
```

- Math system is fully polymorphic. Math primitives (+,-, etc.) are
  built off of polymorphic functions that dispatch on the types of the
  first two arguments. This allows the math system to be extended to
  complex numbers, matrices, etc. The performance penalty of such a
  polymorphic call is completely removed by the RPython generated JIT.

### Good talks

- ["Pixie - A Lightweight Lisp with 'Magical' Powers" by Timothy Baldridge on StrangeLoop, september 2015](https://www.youtube.com/watch?v=1AjhFZVfB9c)

## RSqueak, a Squeak/Smalltalk VM written in RPython

RSqueak |  
--- | ---
Sources | https://github.com/HPI-SWA-Lab/RSqueak
Doc | http://rsqueak.readthedocs.io

with all-in-one multiplatform bundles and 32 bits binaries.
