We have 4 active languages: **Dogelang**, **Mochi**, **Hy** and **Coconut** !

<!-- generetae the toc with npm install markdown-toc -->

<!-- toc -->

- [List of languages that compile to Python](#list-of-languages-that-compile-to-python)
  * [Dg - it's a Python ! No, it's a Haskell !](#dg---its-a-python--no-its-a-haskell-)
    + [Language features](#language-features)
    + [Install](#install)
    + [Editors](#editors)
    + [Example projects](#example-projects)
  * [Hy - A dialect of Lisp that's embedded in Python](#hy---a-dialect-of-lisp-thats-embedded-in-python)
    + [Language features](#language-features-1)
    + [Install](#install-1)
    + [Editors](#editors-1)
    + [Example projects](#example-projects-1)
    + [Good reads](#good-reads)
  * [Mochi - Dynamically typed programming language for functional programming and actor-style programming](#mochi---dynamically-typed-programming-language-for-functional-programming-and-actor-style-programming)
    + [Language features](#language-features-2)
    + [Install](#install-2)
    + [Editors](#editors-2)
    + [Good reads](#good-reads-1)
  * [Coconut - Simple, elegant, Pythonic functional programming](#coconut---simple-elegant-pythonic-functional-programming)
    + [Language features](#language-features-3)
    + [Install](#install-3)
    + [Editors](#editors-3)
  * [Rabbit - a functional language on top of Python (discontinued in favor of Coconut)](#rabbit---a-functional-language-on-top-of-python-discontinued-in-favor-of-coconut)
- [Misc](#misc)
  * [Pixie, a lightweight and native lisp built in RPython](#pixie-a-lightweight-and-native-lisp-built-in-rpython)
    + [Features](#features)
    + [Good talks](#good-talks)
  * [ProbLog. Probabilistic Logic Programming](#problog-probabilistic-logic-programming)
    + [Install](#install-4)

<!-- tocstop -->

# List of languages that compile to Python

## Dg - it's a Python ! No, it's a Haskell !

 <img src="https://pyos.github.io/dg/images/seriousdawg.jpg", title="NOT'REALLY®" </img>


Dogelang  |  
--- | ---
sources |[<https://github.com/pyos/dg>](https://github.com/pyos/dg)
doc | [<https://pyos.github.io/dg/>](https://pyos.github.io/dg/)
v1 ? | yes, april 2015
created | june, 2012

-   compiles to CPython 3.4. Dg is an alternative syntax to Python 3.
-   compatible with all the libraries
-   runs on PyPy (Got to wait for a JIT-enabled PyPy 3.3 first, though.)

### Language features

-   function calls without parenthesis:

        print "wow" "two lines" sep: "\n"

-   reverse pipe operator:

        print $ "> {}: {}".format "Karkat" "Reference something other than Doge"

-   pipe and reverse pipe (on the same line, unlike Mochi)

```dg
print <| 'What' + 'ever.' : 'This is the same thing ' + 'in a different direction.' |> print
```

-   function notation (arrow `->` notation)

```dg
function = arg1 arg2 -> : print (arg1.replace "Do " "Did ") arg2 sep: ", " end: ".\n"
function "Do something" "dammit"
```

-   infix notation (with backticks)
-   function composition (with `<-`)
-   first class operators

        f = (+)
        f 1 2 == 3

-   partial application (and `bind` is `functools.partial`)

        f = (2 *)
        f 10 == 20

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

### Example projects


Project |  
--- | ---
dogeweb , a functional web framework atop asyncio |   [<https://pyos.github.io/dogeweb/>](https://pyos.github.io/dogeweb/)

## Hy - A dialect of Lisp that's embedded in Python

<img src='http://docs.hylang.org/en/latest/_images/hy-logo-small.png', title='' </img>

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

``` {.example}
(-> (read) (eval) (print) (loop))
```

``` {.commonlisp}
(import [sh [cat grep wc]])
(-> (cat "/usr/share/dict/words") (grep "-E" "^hy") (wc "-l"))  ; => 210
```

-   [anaphoric
    functions](http://docs.hylang.org/en/latest/contrib/anaphoric.html)

``` {.example}
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

```
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

-   pipelines : (1, 2) |\*\> (+) |\> sq |\> print For multiline pipes,
    surround them with parenthesis (python rule that every newline
    inside parenthesis is ignored):

```coconut
(
    "hello"
    |> print
)
```

-   pattern matching (`match x in value:`), guards
-   algeabric data types
-   partial application (`$` sign right after a function name) : expnums
    = map(pow\$(2), range(5)) : expnums |\> list |\> print
-   lazy lists (surround coma-separated lists with `(|` and `|)`)
-   destructuring assignment
-   function composition (with `..`) : fog = f..g
-   prettier lambdas (`->` syntax)
-   parallel programming
-   tail recursion optimization
-   infix notation (like in Haskell with backticks)
-   underscore digits separators (`10_000_000`)
-   decorators support any expression : @ wrapper1 .. wrapper2 \$(arg)
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

# Misc

## Pixie, a lightweight and native lisp built in RPython

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

## ProbLog. Probabilistic Logic Programming

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
