# Python Mastery Checklist: 0 → God Tier (Complete Edition)

> **Core insight**: Python "variables" are *names bound to objects*. Assignment rebinds names; mutation changes objects. Master this + the **data model (dunder methods)** + the **import system**, and Python stops being mysterious.

---

## How to Use This Checklist

**Proficiency Levels**
- **L1**: Can use it in small scripts
- **L2**: Can explain it + common pitfalls
- **L3**: Can debug it from first principles
- **L4**: Can design APIs with it, teach it, predict behavior before running

**Completion Standard**: For each item, aim to (1) understand concept, (2) write a small demo, (3) explain tradeoffs/pitfalls, (4) debug when it goes wrong.

**The "nitty gritty" standard**: "I can predict behavior before I run it."

---

# Phase 0 — Meta-Learning & Environment Setup (Foundation)

## 0.1 Learning Habits
- [ ] Maintain a "Python notes repo" with runnable examples and writeups
- [ ] Keep a "surprises list" (things you got wrong once)
- [ ] Practice reading tracebacks top-to-bottom
- [ ] Know how to reduce bugs to minimal repros
- [ ] Know how to bisect issues across Python versions
- [ ] Know how to read: language reference, stdlib docs, PEPs, CPython source

## 0.2 Environment & Execution
- [ ] Install Python; understand multiple versions on one machine
- [ ] Run code via:
  - [ ] REPL (interactive interpreter)
  - [ ] Script (`python file.py`)
  - [ ] Module execution (`python -m package.module`)
- [ ] Understand `sys.path` and how imports find code
- [ ] Virtual environments:
  - [ ] `venv` basics (create/activate, site-packages isolation)
  - [ ] Dependency installation with `pip`
  - [ ] Why virtualenvs matter (isolation, reproducibility)
- [ ] Know "interpreter vs environment vs project" distinction
- [ ] Inspect packages (`pip show`, `pkg.__file__`, `pip list`)
- [ ] REPL workflows: `python -i`, `help()`, `dir()`, `inspect`

---

# Phase 1 — Lexical Structure & Syntax Fundamentals

## 1.1 Tokens & Grammar
- [ ] Identifiers, keywords, soft keywords (e.g., `match`, `case`)
- [ ] Literals: string, numeric, boolean, None
- [ ] Operators and delimiters
- [ ] Grammar basics: expressions vs statements vs blocks

## 1.2 Indentation & Structure
- [ ] Significant whitespace and indentation rules
- [ ] Suites (blocks of code)
- [ ] Physical vs logical lines
- [ ] Line joining: implicit (inside brackets) and explicit (`\`)

## 1.3 Comments & Documentation
- [ ] Comments (`#`)
- [ ] Docstrings: where they live, how they're stored (`__doc__`)
- [ ] Encoding cookies (`# -*- coding: utf-8 -*-`)

## 1.4 Literals Deep Dive
- [ ] String literals:
  - [ ] Single/double/triple quotes
  - [ ] Raw strings (`r""`)
  - [ ] F-strings (formatted string literals)
  - [ ] Bytes literals (`b""`)
- [ ] Numeric literals:
  - [ ] Decimal, binary (`0b`), octal (`0o`), hex (`0x`)
  - [ ] Underscores for readability (`1_000_000`)
  - [ ] Scientific notation (`1e10`)

## 1.5 Operators & Precedence
- [ ] Arithmetic: `+`, `-`, `*`, `/`, `//`, `%`, `**`, `@`
- [ ] Comparison: `==`, `!=`, `<`, `>`, `<=`, `>=`
- [ ] Boolean: `and`, `or`, `not`
- [ ] Bitwise: `&`, `|`, `^`, `~`, `<<`, `>>`
- [ ] Membership: `in`, `not in`
- [ ] Identity: `is`, `is not`
- [ ] Assignment: `=`, `:=` (walrus)
- [ ] Operator precedence and associativity rules

---

# Phase 2 — Execution Model & Namespaces

## 2.1 Execution Pipeline
- [ ] Source → tokens → AST → bytecode → execution (conceptual)
- [ ] Module execution happens at import-time (top-level code runs)
- [ ] Code objects (`__code__`), frames, call stack (conceptual)

## 2.2 Namespaces & Scope
- [ ] Namespace types: module globals, function locals, builtins
- [ ] LEGB rule: Local → Enclosing → Global → Builtins
- [ ] `global` and `nonlocal` statements (exact effects)
- [ ] `locals()` and `globals()` behavior and caveats
- [ ] Scope boundaries: modules, functions, classes, comprehensions

## 2.3 Closures
- [ ] Free variables and closure cells
- [ ] Late binding pitfalls (loop variable capture)
- [ ] Fixing late binding: default arguments, `functools.partial`

---

# Phase 3 — The Data Model (The Heart of Python)

## 3.1 Objects, Identity, Mutability
- [ ] Everything is an object; names are references
- [ ] Identity (`id`, `is`) vs equality (`==`)
- [ ] Mutability vs immutability
- [ ] How mutability affects hashing
- [ ] Object lifetime and when objects become unreachable
- [ ] Aliasing: `a = b = []` and mutation effects

## 3.2 Attribute Access Machinery
- [ ] Attribute lookup order: instance → class → base classes
- [ ] `__getattribute__` (always called) vs `__getattr__` (fallback)
- [ ] `__setattr__` and `__delattr__`
- [ ] `__dict__` (instance attribute storage)
- [ ] `__slots__` (memory optimization, attribute restriction)
- [ ] Bound methods and function descriptor behavior

## 3.3 Core Protocols (Dunder Methods)

### Representation
- [ ] `__repr__`: unambiguous, for developers
- [ ] `__str__`: readable, for users
- [ ] `__format__`: custom formatting with format specs

### Comparison & Hashing
- [ ] `__eq__`, `__ne__`
- [ ] `__lt__`, `__le__`, `__gt__`, `__ge__`
- [ ] `__hash__`: invariants with `__eq__`
- [ ] `functools.total_ordering` helper

### Truthiness
- [ ] `__bool__`
- [ ] `__len__` fallback for truthiness

### Iteration
- [ ] `__iter__`: return an iterator
- [ ] `__next__`: return next value or raise `StopIteration`
- [ ] `__reversed__`: custom reverse iteration

### Container Protocol
- [ ] `__len__`
- [ ] `__contains__`: `in` operator
- [ ] `__getitem__`: indexing and slicing
- [ ] `__setitem__`, `__delitem__`
- [ ] `__missing__`: dict subclass hook

### Numeric Operations
- [ ] `__add__`, `__sub__`, `__mul__`, etc.
- [ ] Reflected operations: `__radd__`, `__rsub__`, etc.
- [ ] In-place operations: `__iadd__`, `__isub__`, etc.
- [ ] `__neg__`, `__pos__`, `__abs__`
- [ ] `__index__`: integer conversion for slicing

### Callable
- [ ] `__call__`: make instances callable

### Context Manager
- [ ] `__enter__`
- [ ] `__exit__`: exception handling, suppression

### Async Protocols
- [ ] `__aiter__`, `__anext__`: async iteration
- [ ] `__aenter__`, `__aexit__`: async context manager
- [ ] `__await__`: awaitable objects

### Serialization
- [ ] `__getstate__`, `__setstate__`: pickle customization
- [ ] `__reduce__`, `__reduce_ex__`: advanced pickle
- [ ] `__copy__`, `__deepcopy__`: copy module hooks

### Object Lifecycle
- [ ] `__new__`: object creation (before `__init__`)
- [ ] `__init__`: object initialization
- [ ] `__del__`: destructor (discouraged, understand pitfalls)

## 3.4 Descriptor Protocol
- [ ] Non-data descriptors vs data descriptors
- [ ] `__get__(self, obj, objtype=None)`
- [ ] `__set__(self, obj, value)`
- [ ] `__delete__(self, obj)`
- [ ] `__set_name__(self, owner, name)`
- [ ] How functions become methods (descriptor binding)
- [ ] `property` internals
- [ ] `@classmethod`, `@staticmethod` mechanics

---

# Phase 4 — Built-in Types Deep Dive

## 4.1 Numbers
- [ ] `int`: arbitrary precision, bit operations, `bit_length()`, `bit_count()`
- [ ] `float`: IEEE-754 realities
  - [ ] NaN, inf, -inf
  - [ ] Rounding errors and equality pitfalls
  - [ ] `math.isclose()` for comparison
- [ ] `complex`: real/imag, operations
- [ ] `decimal.Decimal`:
  - [ ] Context, precision, rounding modes
  - [ ] `quantize()` for fixed decimal places
- [ ] `fractions.Fraction`: exact rational arithmetic
- [ ] Numeric tower: coercion rules, `__int__`, `__float__`, `__index__`

## 4.2 Text & Binary Data
- [ ] `str` is Unicode:
  - [ ] Code points vs graphemes (conceptual)
  - [ ] String methods (find, replace, split, join, strip, etc.)
  - [ ] String formatting: f-strings, `.format()`, `%` formatting
  - [ ] Format spec mini-language (`{:>10.2f}`)
- [ ] Encoding/decoding:
  - [ ] `encode()`, `decode()`
  - [ ] Error handlers: `strict`, `ignore`, `replace`, `surrogateescape`
- [ ] `bytes` (immutable) and `bytearray` (mutable)
- [ ] `memoryview` and buffer protocol (zero-copy access)

## 4.3 Collections
- [ ] `list`:
  - [ ] Indexing, slicing (creates copies)
  - [ ] `append`, `extend`, `insert`, `pop`, `remove`
  - [ ] Growth behavior (amortized O(1) append)
  - [ ] List as stack (good), list as queue (bad)
- [ ] `tuple`:
  - [ ] Immutability, hashability (if contents hashable)
  - [ ] Single-element tuple syntax: `(x,)`
  - [ ] Named tuples preview
- [ ] `dict`:
  - [ ] Key requirements: hashable, `__eq__` consistency
  - [ ] Insertion order guaranteed (Python 3.7+)
  - [ ] Views: `keys()`, `values()`, `items()`
  - [ ] `get()`, `setdefault()`, `pop()`, `update()`
  - [ ] Dict comprehensions
  - [ ] `__missing__` for subclasses
- [ ] `set` / `frozenset`:
  - [ ] Uniqueness, membership O(1) average
  - [ ] Set operations: union, intersection, difference, symmetric_difference
  - [ ] Set comprehensions
- [ ] `range`: lazy sequence, memory efficient
- [ ] Copying:
  - [ ] Shallow copy: `copy()`, `list()`, `[:]`, `copy.copy()`
  - [ ] Deep copy: `copy.deepcopy()`
  - [ ] Aliasing pitfalls

## 4.4 Other Built-in Types
- [ ] `bool`: subclass of `int`, `True == 1`, `False == 0`
- [ ] `NoneType`: singleton `None`
- [ ] `type`: the type of types
- [ ] `slice`: slice objects for extended slicing
- [ ] `ellipsis`: `...` literal and uses

---

# Phase 5 — Control Flow & Statements

## 5.1 Conditionals
- [ ] `if / elif / else`
- [ ] Truthiness rules for all types
- [ ] Conditional expressions: `x if cond else y`
- [ ] Short-circuit evaluation: `and`, `or` return operands (not always bool)

## 5.2 Loops
- [ ] `for` loops:
  - [ ] Iteration protocol
  - [ ] Unpacking in loop target
  - [ ] Loop variable binding (exists after loop)
- [ ] `while` loops
- [ ] `break`, `continue`, `pass`
- [ ] Loop `else` blocks (runs if no `break`)

## 5.3 Pattern Matching (`match`/`case`)
- [ ] Literal patterns
- [ ] Capture patterns (bind to name)
- [ ] Wildcard `_`
- [ ] Sequence patterns: `[a, b, *rest]`
- [ ] Mapping patterns: `{"key": value}`
- [ ] Class patterns and `__match_args__`
- [ ] Guards: `case x if x > 0:`
- [ ] OR patterns: `case 1 | 2 | 3:`
- [ ] Irrefutability and name binding rules

## 5.4 Assignment Forms
- [ ] Simple assignment: `x = value`
- [ ] Chained assignment: `a = b = value`
- [ ] Tuple/list unpacking: `a, b = pair`
- [ ] Starred unpacking: `first, *rest, last = seq`
- [ ] Augmented assignment: `x += 1` (mutability implications)
- [ ] Walrus operator: `(x := expr)` scoping rules
- [ ] Attribute assignment vs item assignment

## 5.5 Context Managers (`with`)
- [ ] `with` statement desugaring
- [ ] Multiple context managers
- [ ] Exception flow through `__exit__`
- [ ] Exception suppression (returning `True` from `__exit__`)

## 5.6 Exception Handling
- [ ] `try / except / else / finally` flow (exact order)
- [ ] Exception hierarchy: `BaseException` → `Exception`
- [ ] Catching multiple exceptions: `except (A, B):`
- [ ] Catching with binding: `except E as e:`
- [ ] Bare `except:` (avoid) and `except BaseException:`
- [ ] `raise` forms: raise, re-raise, raise with value
- [ ] Exception chaining: `raise X from Y` (explicit cause)
- [ ] Implicit chaining (`__context__`)
- [ ] `finally` guarantees and gotchas (return/raise interaction)
- [ ] `assert` statements and `-O` flag effect

## 5.7 Other Statements
- [ ] `del` statement
- [ ] `import` / `from ... import`
- [ ] `class` and `def` as statements

---

# Phase 6 — Functions (Complete)

## 6.1 Definition & Documentation
- [ ] `def` statement
- [ ] Docstrings: conventions, `__doc__` attribute
- [ ] Annotations: `def f(x: int) -> str:`
- [ ] `return` statement (implicit `None` return)

## 6.2 Parameters & Arguments
- [ ] Positional arguments
- [ ] Keyword arguments
- [ ] Default values (evaluation time pitfall!)
- [ ] Mutable default argument bug and fix
- [ ] `*args`: variable positional
- [ ] `**kwargs`: variable keyword
- [ ] Keyword-only parameters: `def f(*, kw):`
- [ ] Positional-only parameters: `def f(pos, /):`
- [ ] Combined: `def f(pos, /, standard, *, kw):`
- [ ] Argument binding rules and TypeError causes

## 6.3 Scope & Closures
- [ ] LEGB lookup in functions
- [ ] `global` declaration
- [ ] `nonlocal` declaration
- [ ] Closures: capturing variables from enclosing scope
- [ ] Late binding in closures (loop variable bug)
- [ ] Fixing with default arguments or `functools.partial`

## 6.4 Lambda Functions
- [ ] Syntax: `lambda args: expression`
- [ ] Single expression only
- [ ] When to use vs when to use `def`
- [ ] Lambda in sorting: `sorted(items, key=lambda x: x.attr)`

## 6.5 Higher-Order Functions
- [ ] Functions as first-class objects
- [ ] Passing functions as arguments
- [ ] Returning functions
- [ ] `map()`, `filter()`, `reduce()` (and when to use comprehensions instead)

## 6.6 Decorators
- [ ] Applying decorators: `@decorator`
- [ ] Decorator is just `func = decorator(func)`
- [ ] Writing simple decorators
- [ ] Preserving metadata: `@functools.wraps`
- [ ] Decorators with arguments
- [ ] Class decorators
- [ ] Decorator stacking order
- [ ] Common decorators: `@property`, `@staticmethod`, `@classmethod`

## 6.7 Function Introspection
- [ ] `__name__`, `__qualname__`
- [ ] `__module__`
- [ ] `__code__`: code object
- [ ] `__defaults__`, `__kwdefaults__`
- [ ] `__annotations__`
- [ ] `__closure__`
- [ ] `inspect.signature()`

---

# Phase 7 — Classes & OOP

## 7.1 Class Basics
- [ ] `class` statement and class body execution
- [ ] `__init__` for initialization
- [ ] `self` convention
- [ ] Instance attributes vs class attributes
- [ ] Method types:
  - [ ] Instance methods
  - [ ] `@classmethod`: receives class as first arg
  - [ ] `@staticmethod`: no implicit first arg
- [ ] `@property` for computed attributes
- [ ] Property setters and deleters

## 7.2 Inheritance
- [ ] Single inheritance
- [ ] `super()` for calling parent methods
- [ ] Multiple inheritance
- [ ] Method Resolution Order (MRO)
- [ ] C3 linearization (conceptual)
- [ ] Diamond problem and `super()` correctness
- [ ] `isinstance()` and `issubclass()`

## 7.3 Abstract Base Classes
- [ ] `abc` module
- [ ] `ABC` base class
- [ ] `@abstractmethod`
- [ ] `@abstractproperty` (deprecated, use property + abstractmethod)
- [ ] `__subclasshook__` for virtual subclasses
- [ ] `register()` for virtual subclasses

## 7.4 Dataclasses
- [ ] `@dataclass` decorator
- [ ] Generated methods: `__init__`, `__repr__`, `__eq__`
- [ ] `field()` function:
  - [ ] `default_factory` for mutable defaults
  - [ ] `repr`, `compare`, `hash` options
- [ ] `frozen=True` for immutability
- [ ] `order=True` for comparison methods
- [ ] `slots=True` (Python 3.10+)
- [ ] `kw_only=True` (Python 3.10+)
- [ ] Post-init processing: `__post_init__`
- [ ] Inheritance with dataclasses

## 7.5 Other Data Containers
- [ ] `collections.namedtuple`
- [ ] `typing.NamedTuple`
- [ ] When to use each: dataclass vs namedtuple vs plain class

## 7.6 Metaprogramming
- [ ] `type()` as class factory
- [ ] Metaclasses:
  - [ ] `__new__` in metaclass
  - [ ] `__init__` in metaclass
  - [ ] `__call__` in metaclass
- [ ] `__init_subclass__`: hook for subclass creation
- [ ] `__class_getitem__`: generic syntax support (`MyClass[T]`)
- [ ] `__prepare__`: custom namespace for class body
- [ ] Class decorators as simpler alternative to metaclasses

---

# Phase 8 — Iteration, Generators, Coroutines

## 8.1 Iteration Protocol
- [ ] Iterables: objects with `__iter__`
- [ ] Iterators: objects with `__iter__` and `__next__`
- [ ] `iter()` function and sentinel form: `iter(callable, sentinel)`
- [ ] `StopIteration` exception
- [ ] Iterator exhaustion (one-pass only)

## 8.2 Comprehensions
- [ ] List comprehensions: `[expr for x in iter]`
- [ ] Dict comprehensions: `{k: v for x in iter}`
- [ ] Set comprehensions: `{expr for x in iter}`
- [ ] Generator expressions: `(expr for x in iter)`
- [ ] Nested comprehensions
- [ ] Filtering: `[x for x in iter if cond]`
- [ ] Comprehension scope (own namespace in Python 3)

## 8.3 Generators
- [ ] Generator functions: `def` with `yield`
- [ ] Generator state and suspension
- [ ] `yield` vs `return`
- [ ] Generator expressions (lazy)
- [ ] `yield from` for delegation
- [ ] Generator methods:
  - [ ] `send(value)`: send value into generator
  - [ ] `throw(exc)`: throw exception into generator
  - [ ] `close()`: close generator
- [ ] `StopIteration` value (return value from generator)
- [ ] Generator-based coroutines (historical context)

## 8.4 Async/Await
- [ ] `async def`: coroutine functions
- [ ] `await`: suspend until awaitable completes
- [ ] Awaitables: coroutines, tasks, futures
- [ ] `asyncio` basics:
  - [ ] Event loop concept
  - [ ] `asyncio.run()`
  - [ ] `asyncio.create_task()`
  - [ ] `asyncio.gather()`
  - [ ] `asyncio.wait()`
- [ ] Async iteration: `async for`
- [ ] Async generators: `async def` with `yield`
- [ ] Async context managers: `async with`
- [ ] Timeouts: `asyncio.timeout()`, `asyncio.wait_for()`
- [ ] Cancellation: `CancelledError`, task cancellation
- [ ] Structured concurrency concept

---

# Phase 9 — Modules, Packages, Imports

## 9.1 Modules
- [ ] What is a module (file = module object)
- [ ] Module attributes: `__name__`, `__file__`, `__doc__`
- [ ] `__name__ == "__main__"` idiom
- [ ] Module-level code execution at import time

## 9.2 Packages
- [ ] Regular packages: directories with `__init__.py`
- [ ] Namespace packages: no `__init__.py` (PEP 420)
- [ ] `__init__.py` execution and purpose
- [ ] `__all__` for controlling `from pkg import *`
- [ ] `__path__` for package path manipulation

## 9.3 Import System
- [ ] `import module`
- [ ] `from module import name`
- [ ] `from module import *`
- [ ] `import module as alias`
- [ ] Absolute imports
- [ ] Relative imports: `from . import`, `from .. import`
- [ ] `sys.path` and how Python finds modules
- [ ] Working directory effects
- [ ] `PYTHONPATH` environment variable

## 9.4 Import Mechanics
- [ ] `sys.modules` cache
- [ ] Import hooks (finders and loaders, conceptual)
- [ ] `importlib` module:
  - [ ] `import_module()`
  - [ ] `reload()` and its pitfalls
- [ ] `__import__()` built-in (low-level)
- [ ] Zip imports (`zipimport`)

## 9.5 Common Import Issues
- [ ] Circular imports: symptoms and fixes
- [ ] Import-time side effects
- [ ] Shadowing standard library modules
- [ ] Module not found errors debugging

---

# Phase 10 — Exception Handling (Deep)

## 10.1 Exception Classes
- [ ] Exception hierarchy tree
- [ ] `BaseException` vs `Exception`
- [ ] Common built-in exceptions
- [ ] Custom exception design:
  - [ ] Inherit from `Exception`
  - [ ] Add context attributes
  - [ ] Meaningful `__str__`

## 10.2 Exception Flow
- [ ] `try/except/else/finally` exact semantics
- [ ] Multiple `except` clauses
- [ ] Exception groups (Python 3.11+)
- [ ] `except*` for exception groups

## 10.3 Raising Exceptions
- [ ] `raise ExceptionType(message)`
- [ ] Re-raise: bare `raise`
- [ ] Exception chaining:
  - [ ] Explicit: `raise X from Y`
  - [ ] Implicit: `__context__`
  - [ ] Suppress: `raise X from None`

## 10.4 Traceback Reading
- [ ] Frame-by-frame analysis
- [ ] "During handling of..." messages
- [ ] `traceback` module for manipulation
- [ ] `sys.exc_info()`

## 10.5 Best Practices
- [ ] Catch specific exceptions
- [ ] Don't silence exceptions without reason
- [ ] Use context managers for cleanup
- [ ] Log exceptions properly
- [ ] Re-raise with context when wrapping

---

# Phase 11 — File I/O & Resource Management

## 11.1 File Basics
- [ ] `open()` function
- [ ] Text mode vs binary mode
- [ ] File modes: `r`, `w`, `a`, `x`, `b`, `+`
- [ ] Context managers for files: `with open(...) as f:`

## 11.2 Reading Files
- [ ] `read()`: entire file
- [ ] `readline()`: single line
- [ ] `readlines()`: list of lines
- [ ] Iteration: `for line in file:`
- [ ] Chunked reading for large files

## 11.3 Writing Files
- [ ] `write()`: write string/bytes
- [ ] `writelines()`: write iterable
- [ ] Buffering behavior
- [ ] Flushing: `flush()`

## 11.4 Encodings
- [ ] UTF-8 as default (Python 3)
- [ ] `encoding` parameter
- [ ] `errors` parameter
- [ ] BOM handling
- [ ] `locale.getpreferredencoding()`

## 11.5 Paths
- [ ] `pathlib.Path` (modern approach)
  - [ ] Path construction and joining
  - [ ] Path parts: parent, name, stem, suffix
  - [ ] Globbing: `glob()`, `rglob()`
  - [ ] File operations: `read_text()`, `write_text()`, etc.
- [ ] `os.path` (legacy)
- [ ] Path manipulation safety

## 11.6 Filesystem Operations
- [ ] `os` module: `mkdir`, `makedirs`, `remove`, `rename`
- [ ] `shutil`: `copy`, `copytree`, `rmtree`, `move`
- [ ] Permissions (conceptual)
- [ ] Symbolic links
- [ ] Atomic operations: temp file + rename pattern

## 11.7 Temporary Files
- [ ] `tempfile.NamedTemporaryFile`
- [ ] `tempfile.TemporaryDirectory`
- [ ] `tempfile.mkstemp`, `tempfile.mkdtemp`
- [ ] Automatic cleanup

## 11.8 Context Managers (Writing)
- [ ] Class-based: `__enter__`, `__exit__`
- [ ] Generator-based: `@contextlib.contextmanager`
- [ ] `contextlib.ExitStack` for dynamic context management
- [ ] Async context managers: `@contextlib.asynccontextmanager`

## 11.9 Serialization
- [ ] `json`: `dump`, `load`, `dumps`, `loads`
  - [ ] Custom encoders/decoders
  - [ ] Handling non-serializable types
- [ ] `csv`: reader, writer, DictReader, DictWriter
- [ ] `pickle`:
  - [ ] **Security warning**: never unpickle untrusted data
  - [ ] Protocol versions
  - [ ] Custom `__getstate__`/`__setstate__`
- [ ] `tomllib` (Python 3.11+): TOML reading
- [ ] `configparser`: INI files

---

# Phase 12 — Standard Library Mastery

## 12.1 Functional Tools
- [ ] `itertools`:
  - [ ] Infinite: `count`, `cycle`, `repeat`
  - [ ] Combinatoric: `product`, `permutations`, `combinations`
  - [ ] Terminating: `chain`, `islice`, `takewhile`, `dropwhile`
  - [ ] Grouping: `groupby` (requires sorted input)
- [ ] `functools`:
  - [ ] `lru_cache`, `cache` (memoization)
  - [ ] `partial` (partial application)
  - [ ] `reduce`
  - [ ] `singledispatch` (generic functions)
  - [ ] `total_ordering`
  - [ ] `wraps` (decorator helper)
- [ ] `operator`:
  - [ ] `itemgetter`, `attrgetter`
  - [ ] Operator functions: `add`, `mul`, etc.

## 12.2 Collections
- [ ] `collections`:
  - [ ] `deque`: efficient append/pop both ends
  - [ ] `Counter`: counting hashable objects
  - [ ] `defaultdict`: dict with default factory
  - [ ] `OrderedDict`: insertion-ordered (historical)
  - [ ] `ChainMap`: multiple dict view
  - [ ] `namedtuple`: tuple with named fields
- [ ] `heapq`: min-heap operations
- [ ] `bisect`: binary search and sorted insertion
- [ ] `array`: efficient homogeneous arrays

## 12.3 Text Processing
- [ ] `re` (regular expressions):
  - [ ] Pattern syntax
  - [ ] `match`, `search`, `findall`, `finditer`
  - [ ] `sub`, `split`
  - [ ] Groups and backreferences
  - [ ] Flags: `IGNORECASE`, `MULTILINE`, `DOTALL`, `VERBOSE`
  - [ ] Compiled patterns
  - [ ] Backtracking pitfalls (ReDoS)
- [ ] `string`: constants, Template
- [ ] `textwrap`: wrapping and indentation
- [ ] `difflib`: sequence comparison

## 12.4 Time & Date
- [ ] `datetime`:
  - [ ] `date`, `time`, `datetime`, `timedelta`
  - [ ] Naive vs aware datetimes
  - [ ] `timezone` objects
  - [ ] Formatting: `strftime`, `strptime`
- [ ] `zoneinfo`: IANA timezone database
  - [ ] DST handling pitfalls
- [ ] `time`: `time()`, `sleep()`, `perf_counter()`, `monotonic()`
- [ ] `calendar`: calendar calculations

## 12.5 Data Structures
- [ ] `dataclasses`
- [ ] `enum`:
  - [ ] `Enum`, `IntEnum`, `StrEnum`
  - [ ] `Flag`, `IntFlag`
  - [ ] `auto()`
- [ ] `types`: SimpleNamespace, function types

## 12.6 OS & System
- [ ] `os`: environment, process, filesystem
- [ ] `sys`: interpreter state, path, modules
- [ ] `platform`: platform information
- [ ] `subprocess`:
  - [ ] `run()` (preferred)
  - [ ] `Popen` for complex cases
  - [ ] Pipes and deadlocks
  - [ ] `shell=True` security risks
  - [ ] Text vs binary mode
- [ ] `shlex`: safe shell-like parsing
- [ ] `signal`: signal handling (conceptual)

## 12.7 Networking
- [ ] `socket`: low-level networking
  - [ ] TCP vs UDP
  - [ ] Client and server patterns
- [ ] `ssl`: TLS/SSL wrapper
  - [ ] Certificate verification
  - [ ] Context configuration
- [ ] `http.client`, `http.server`
- [ ] `urllib.request`, `urllib.parse`
- [ ] `email`: email handling

## 12.8 Concurrency
- [ ] `threading`:
  - [ ] `Thread` class
  - [ ] `Lock`, `RLock`
  - [ ] `Condition`, `Event`, `Semaphore`
  - [ ] `Barrier`
  - [ ] Thread-local data
- [ ] `queue`: thread-safe queues
- [ ] `multiprocessing`:
  - [ ] `Process` class
  - [ ] `Pool` for parallel execution
  - [ ] IPC: `Queue`, `Pipe`
  - [ ] Shared memory
  - [ ] Start methods: fork, spawn, forkserver
- [ ] `concurrent.futures`:
  - [ ] `ThreadPoolExecutor`
  - [ ] `ProcessPoolExecutor`
  - [ ] `Future` objects
  - [ ] `as_completed()`, `wait()`

## 12.9 Debugging & Profiling
- [ ] `pdb`: interactive debugger
  - [ ] `breakpoint()` function
  - [ ] Stepping: `n`, `s`, `c`, `r`
  - [ ] Inspection: `p`, `pp`, `l`, `w`
- [ ] `traceback`: traceback manipulation
- [ ] `logging`:
  - [ ] Levels: DEBUG, INFO, WARNING, ERROR, CRITICAL
  - [ ] Handlers: StreamHandler, FileHandler, etc.
  - [ ] Formatters
  - [ ] Logger hierarchy
- [ ] `warnings`: warning control
- [ ] `timeit`: micro-benchmarking
- [ ] `cProfile`, `pstats`: CPU profiling

## 12.10 Testing
- [ ] `unittest`:
  - [ ] Test cases and test suites
  - [ ] Assertions
  - [ ] setUp/tearDown
  - [ ] Mock and patch
- [ ] `doctest`: tests in docstrings

## 12.11 Other Useful Modules
- [ ] `copy`: shallow and deep copy
- [ ] `weakref`: weak references (cache patterns)
- [ ] `contextlib`: context manager utilities
- [ ] `abc`: abstract base classes
- [ ] `inspect`: runtime introspection
- [ ] `dis`: bytecode disassembly
- [ ] `ast`: abstract syntax tree
- [ ] `secrets`: cryptographic randomness
- [ ] `hashlib`: secure hashes
- [ ] `hmac`: keyed hashing
- [ ] `base64`: encoding
- [ ] `struct`: binary data packing
- [ ] `sqlite3`: embedded database

---

# Phase 13 — Type Hints & Static Analysis

## 13.1 Basic Type Hints
- [ ] Function annotations: `def f(x: int) -> str:`
- [ ] Variable annotations: `x: int = 5`
- [ ] Built-in generics: `list[int]`, `dict[str, int]`
- [ ] `tuple` types: `tuple[int, str]`, `tuple[int, ...]`

## 13.2 Union Types
- [ ] `Union[X, Y]` or `X | Y` (Python 3.10+)
- [ ] `Optional[X]` = `X | None`

## 13.3 Special Types
- [ ] `Any`: opt out of type checking
- [ ] `object`: base of all types
- [ ] `None` as a type
- [ ] `NoReturn` / `Never`: functions that don't return
- [ ] `Literal["a", "b"]`: specific values
- [ ] `Final`: constants
- [ ] `NewType`: distinct type aliases
- [ ] `ClassVar`: class-level attributes

## 13.4 Generics
- [ ] `TypeVar`: type variables
- [ ] `Generic` base class
- [ ] Variance:
  - [ ] Covariant (`covariant=True`)
  - [ ] Contravariant (`contravariant=True`)
  - [ ] Invariant (default)
- [ ] Bounded type variables: `TypeVar('T', bound=SomeClass)`
- [ ] Constrained type variables: `TypeVar('T', int, str)`

## 13.5 Protocols & Structural Typing
- [ ] `Protocol` class
- [ ] `@runtime_checkable`
- [ ] Implicit protocol satisfaction (duck typing)

## 13.6 Callable Types
- [ ] `Callable[[ArgTypes], ReturnType]`
- [ ] `ParamSpec`: preserve parameter types
- [ ] `Concatenate`: add parameters

## 13.7 TypedDict
- [ ] Defining typed dictionaries
- [ ] Required vs optional keys
- [ ] `total=False`

## 13.8 Advanced Typing
- [ ] `@overload`: multiple signatures
- [ ] Type narrowing:
  - [ ] `isinstance()` checks
  - [ ] `TypeGuard`
  - [ ] Pattern matching narrowing
- [ ] Self type (`Self` in Python 3.11+)
- [ ] Recursive types
- [ ] Forward references: string annotations

## 13.9 Type Checkers
- [ ] mypy basics
- [ ] pyright basics
- [ ] Configuration: strictness levels
- [ ] Stub files (`.pyi`)
- [ ] Inline type: ignore comments
- [ ] Gradual typing strategy

## 13.10 Runtime Behavior
- [ ] Annotations stored in `__annotations__`
- [ ] `get_type_hints()` for resolving
- [ ] Stringized annotations and `from __future__ import annotations`
- [ ] Type hints don't enforce at runtime (usually)

---

# Phase 14 — Concurrency & Parallelism

## 14.1 Understanding the GIL
- [ ] What the GIL is (Global Interpreter Lock)
- [ ] What it protects (interpreter state)
- [ ] What it doesn't help (your data structures)
- [ ] When it's released (I/O, some C extensions)
- [ ] CPython-specific (PyPy, etc. may differ)

## 14.2 Threading
- [ ] When threads help: I/O-bound work
- [ ] When threads don't help: CPU-bound (GIL)
- [ ] Race conditions and data races
- [ ] Thread safety and synchronization
- [ ] Deadlock patterns and prevention
- [ ] Thread-local storage

## 14.3 Multiprocessing
- [ ] When processes help: CPU-bound work
- [ ] Process isolation (no shared memory by default)
- [ ] IPC mechanisms: queues, pipes, shared memory
- [ ] Pickling constraints (what can be sent)
- [ ] Start methods and their implications
- [ ] Process pools

## 14.4 Async I/O
- [ ] Event loop model
- [ ] Cooperative multitasking (you must `await`)
- [ ] When async helps: many I/O operations
- [ ] Tasks vs coroutines
- [ ] Concurrent execution: `gather`, `wait`, `as_completed`
- [ ] Async generators and iterators
- [ ] Cancellation and cleanup
- [ ] Backpressure concepts

## 14.5 Choosing the Right Model
- [ ] CPU-bound: multiprocessing
- [ ] I/O-bound (few connections): threading
- [ ] I/O-bound (many connections): async
- [ ] Hybrid approaches
- [ ] `concurrent.futures` as unified interface

## 14.6 Synchronization Primitives
- [ ] Locks: `Lock`, `RLock`
- [ ] Semaphores
- [ ] Events
- [ ] Conditions
- [ ] Barriers
- [ ] Queues for communication

---

# Phase 15 — Testing & Quality Engineering

## 15.1 Test Types
- [ ] Unit tests: isolated component testing
- [ ] Integration tests: component interaction
- [ ] End-to-end tests: full system
- [ ] Smoke tests: basic sanity checks

## 15.2 Testing with pytest
- [ ] Test discovery conventions
- [ ] Assertions (plain `assert`)
- [ ] Fixtures:
  - [ ] Function, class, module, session scope
  - [ ] `conftest.py`
  - [ ] Parametrized fixtures
- [ ] Parametrization: `@pytest.mark.parametrize`
- [ ] Markers: skip, xfail, custom markers
- [ ] Plugins ecosystem

## 15.3 Mocking
- [ ] `unittest.mock` module
- [ ] `Mock` and `MagicMock`
- [ ] `patch()` decorator/context manager
- [ ] Patching where it's used (import location pitfall)
- [ ] Fakes vs mocks vs stubs
- [ ] Spec and autospec

## 15.4 Test Design
- [ ] Arrange-Act-Assert pattern
- [ ] Test isolation
- [ ] Determinism: seed randomness, control time
- [ ] Test readability
- [ ] Edge cases and boundary conditions

## 15.5 Property-Based Testing
- [ ] Concept: generate many test cases
- [ ] Hypothesis library (conceptual)
- [ ] Finding edge cases automatically

## 15.6 Coverage
- [ ] What coverage measures
- [ ] Coverage.py usage
- [ ] Branch coverage
- [ ] Limitations: coverage ≠ correctness

## 15.7 Code Quality Tools
- [ ] Linters: Ruff, Flake8, Pylint
- [ ] Formatters: Black, YAPF
- [ ] Import sorting: isort
- [ ] Security scanning: Bandit
- [ ] Pre-commit hooks

---

# Phase 16 — Packaging & Distribution

## 16.1 Virtual Environments
- [ ] Why isolation matters
- [ ] `venv` module
- [ ] Activation scripts
- [ ] `pip` inside venvs
- [ ] Requirements files: `requirements.txt`

## 16.2 Package Structure
- [ ] Project layout conventions:
  - [ ] Flat layout
  - [ ] src layout
- [ ] `pyproject.toml`: the modern standard
- [ ] `setup.py` (legacy understanding)
- [ ] `setup.cfg` (legacy understanding)

## 16.3 Build Systems
- [ ] Build backends: setuptools, flit, hatch, poetry
- [ ] Wheels vs source distributions
- [ ] Building: `python -m build`
- [ ] What goes into a wheel

## 16.4 Dependencies
- [ ] Declaring dependencies
- [ ] Optional dependencies (extras)
- [ ] Dependency resolution
- [ ] Version specifiers: `>=`, `~=`, `==`
- [ ] Lock files concept
- [ ] Pinning for reproducibility

## 16.5 Distribution
- [ ] PyPI (Python Package Index)
- [ ] `twine` for uploading
- [ ] TestPyPI for testing
- [ ] Entry points / console scripts
- [ ] Versioning strategies

## 16.6 Editable Installs
- [ ] `pip install -e .`
- [ ] How it affects imports
- [ ] Development workflow

---

# Phase 17 — Security

## 17.1 Dangerous Functions
- [ ] `pickle`: arbitrary code execution
  - [ ] Never unpickle untrusted data
  - [ ] Alternatives: JSON, msgpack
- [ ] `eval()` and `exec()`:
  - [ ] Never use with user input
  - [ ] Safer alternatives when needed
- [ ] `input()` in Python 2 (historical)
- [ ] `os.system()`, `subprocess` with `shell=True`

## 17.2 Secrets Management
- [ ] `secrets` module for tokens
- [ ] Environment variables for configuration
- [ ] Never commit secrets to version control
- [ ] Secrets in logs and error messages

## 17.3 Cryptography
- [ ] `hashlib` for hashing
- [ ] `hmac` for message authentication
- [ ] Password hashing: don't roll your own
- [ ] `secrets.compare_digest` for timing-safe comparison

## 17.4 TLS/SSL
- [ ] Certificate verification (don't disable it)
- [ ] Hostname checking
- [ ] SSL context configuration
- [ ] Certificate pinning concept

## 17.5 Dependency Security
- [ ] Supply chain attacks
- [ ] Dependency pinning and hashes
- [ ] Security advisories
- [ ] Scanning tools: pip-audit, safety

## 17.6 Input Validation
- [ ] Never trust user input
- [ ] Injection attacks: SQL, command, path traversal
- [ ] Sanitization vs validation
- [ ] Type coercion attacks

---

# Phase 18 — Performance & Optimization

## 18.1 Measurement First
- [ ] Profile before optimizing
- [ ] `timeit` for microbenchmarks
  - [ ] Warmup and noise
  - [ ] Avoid wrong conclusions
- [ ] `cProfile` for CPU profiling
- [ ] Wall time vs CPU time
- [ ] Memory profiling concepts

## 18.2 Big-O Intuition
- [ ] List operations: O(1) append, O(n) insert/search
- [ ] Dict/set operations: O(1) average lookup
- [ ] String concatenation: O(n²) pitfall
- [ ] Choosing right data structures

## 18.3 Python-Specific Patterns
- [ ] Avoid quadratic string concatenation (use `join`)
- [ ] List comprehensions vs loops (often faster)
- [ ] Built-in functions in C (faster)
- [ ] Generator streaming (memory efficiency)
- [ ] `__slots__` for memory
- [ ] Local variable caching (attribute access in loops)

## 18.4 Memory Model
- [ ] Reference counting
- [ ] Cyclic garbage collector
- [ ] Generations concept
- [ ] Common leak patterns:
  - [ ] Caches without bounds
  - [ ] Cycles with `__del__`
  - [ ] Global/module-level collections
- [ ] `weakref` for caches
- [ ] `__slots__` memory savings

## 18.5 When Python Isn't Enough
- [ ] NumPy for numerical work
- [ ] Native extensions concept
- [ ] PyPy JIT compilation
- [ ] Cython concept

---

# Phase 19 — CPython Internals

## 19.1 AST (Abstract Syntax Tree)
- [ ] `ast.parse()`: source to AST
- [ ] AST node types
- [ ] `ast.walk()`: traverse tree
- [ ] `ast.NodeVisitor`, `ast.NodeTransformer`
- [ ] Compile AST to code: `compile()`
- [ ] Use cases: linters, code generators, transformers

## 19.2 Bytecode
- [ ] What bytecode is
- [ ] `dis` module for disassembly
- [ ] `dis.dis()` on functions
- [ ] Code objects: `__code__`
- [ ] Bytecode instructions (conceptual)
- [ ] How comprehensions compile differently

## 19.3 Import System Internals
- [ ] `sys.modules` cache
- [ ] Finders and loaders concept
- [ ] `importlib` machinery
- [ ] Import hooks
- [ ] `__spec__` attribute
- [ ] Why `reload()` is problematic

## 19.4 Object Model Internals
- [ ] `PyObject` structure (conceptual)
- [ ] Reference count field
- [ ] Type object
- [ ] Small object allocator
- [ ] Object interning (small integers, strings)

## 19.5 Execution Model
- [ ] Frame objects
- [ ] Call stack
- [ ] Code objects
- [ ] Trace functions (`sys.settrace`)
- [ ] Profile hooks (`sys.setprofile`)

## 19.6 GIL Implementation
- [ ] When GIL is acquired/released
- [ ] `sys.setswitchinterval()`
- [ ] Impact on threading
- [ ] Free-threaded Python (PEP 703) concept

---

# Phase 20 — Alternative Implementations

## 20.1 PyPy
- [ ] JIT compilation
- [ ] Performance characteristics
- [ ] C extension compatibility (limited)
- [ ] Different GC behavior
- [ ] When to consider PyPy

## 20.2 Other Implementations
- [ ] MicroPython/CircuitPython (embedded)
- [ ] Jython (JVM)
- [ ] IronPython (.NET)
- [ ] GraalPython (conceptual)
- [ ] Behavioral differences across implementations

## 20.3 Portability Considerations
- [ ] Avoid CPython-specific features when targeting multiple implementations
- [ ] C extension compatibility
- [ ] GC behavior differences

---

# Phase 21 — C Extensions & FFI

## 21.1 C-API Fundamentals
- [ ] Python objects in C
- [ ] Reference counting ownership
- [ ] PyObject pointers
- [ ] GIL management in C

## 21.2 ctypes
- [ ] Loading shared libraries
- [ ] Defining C types
- [ ] Function signatures
- [ ] Pointer types
- [ ] Structures and arrays
- [ ] Callbacks

## 21.3 cffi
- [ ] ABI vs API mode
- [ ] Inline definitions
- [ ] Out-of-line compilation
- [ ] When to prefer over ctypes

## 21.4 Buffer Protocol
- [ ] `memoryview` usage
- [ ] Zero-copy data sharing
- [ ] NumPy array interface

## 21.5 Extension Modules
- [ ] Writing C extensions (conceptual)
- [ ] Cython (Python-like to C)
- [ ] pybind11, nanobind (C++)
- [ ] ABI compatibility and manylinux

---

# Phase 22 — Pythonic Design & Idioms

## 22.1 Core Philosophies
- [ ] "Explicit is better than implicit"
- [ ] "Simple is better than complex"
- [ ] "Readability counts"
- [ ] EAFP vs LBYL
- [ ] Duck typing

## 22.2 API Design
- [ ] Designing to protocols, not classes
- [ ] Iterator/generator-based streaming APIs
- [ ] Context managers for resource management
- [ ] Exceptions vs sentinel values
- [ ] `None` as default vs explicit sentinel

## 22.3 Common Footguns to Avoid
- [ ] Mutable default arguments
- [ ] Shadowing builtins
- [ ] Identity vs equality confusion
- [ ] Relying on unspecified ordering
- [ ] Accidental shared mutable state
- [ ] Circular imports
- [ ] Late binding in closures

## 22.4 Testability
- [ ] Dependency injection patterns
- [ ] Avoiding global state
- [ ] Pure functions where possible
- [ ] Mockable interfaces

---

# Phase 23 — Continuous Learning

## 23.1 Version Tracking
- [ ] For each Python release:
  - [ ] Read "What's New"
  - [ ] Track deprecations and removals
  - [ ] Update your code accordingly
  - [ ] Add examples to your notes

## 23.2 PEP Reading
- [ ] Maintain a PEP reading list
- [ ] For features you use:
  - [ ] Read Motivation section
  - [ ] Read Specification
  - [ ] Understand trade-offs

## 23.3 Sharp Edges Catalog
- [ ] Record every surprising behavior
- [ ] Minimal repro
- [ ] Expected vs actual
- [ ] Root cause analysis
- [ ] Prevention pattern

---

# Appendix A — Proof Exercises

> Complete these without looking anything up to verify mastery.

## Fundamentals
- [ ] Demonstrate aliasing: `a = b = []`, mutate, explain
- [ ] Show `is` vs `==` surprises with integers
- [ ] Demonstrate mutable default argument bug and fix

## Functions & Closures
- [ ] Show late-binding closure bug, fix two ways
- [ ] Write decorator with arguments
- [ ] Write decorator that preserves metadata

## OOP & Data Model
- [ ] Implement container class (`__len__`, `__getitem__`, `__iter__`)
- [ ] Implement custom descriptor
- [ ] Demonstrate `__new__` vs `__init__` with immutable type
- [ ] Show MRO with diamond inheritance, explain `super()` order

## Iteration & Generators
- [ ] Convert pipeline to generator pipeline
- [ ] Implement iterator and generator versions of same API
- [ ] Use `yield from` for delegation

## Context Managers
- [ ] Write class-based context manager
- [ ] Write generator-based context manager
- [ ] Show exception suppression rules

## Concurrency
- [ ] Implement same workload three ways: threads, processes, async
- [ ] Demonstrate race condition and fix with lock

## Performance & Internals
- [ ] Profile slow code and fix with measurements
- [ ] Inspect bytecode for comprehension vs loop
- [ ] Write AST tool that counts function definitions
- [ ] Safe subprocess pattern (no shell injection)

## Packaging
- [ ] Build package with console entry point
- [ ] Explain import resolution in your package

---

# Appendix B — Notes Template

For each topic, capture:

```
Concept: [Name]
What it is: [Brief explanation]
Why it exists: [Problem it solves]
Common pitfall: [What goes wrong]
Minimal example: [Runnable code]
Debug strategy: [How to diagnose issues]
Related: [Modules, PEPs, protocols]
```

---

# Quick Reference: Proficiency Self-Test

For any topic, ask yourself:

1. **Can I use it?** (L1)
2. **Can I explain it to someone else?** (L2)
3. **Can I debug it when it breaks?** (L3)
4. **Can I design systems with it?** (L4)

Aim for L3+ on core topics (Phases 1-11), L2+ on advanced topics (Phases 12-22).

---

*This checklist is a living document. Update it as Python evolves and as you discover new sharp edges.*

