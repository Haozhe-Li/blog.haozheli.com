# Python Notes

## Facts about Python that surprise C++ developers

### Contents
1. [Dynamically typed](#dynamically-typed)
2. [Implicit variable declaration](#implicit-variable-declaration)
3. [Non-lexical scoping](#non-lexical-scoping)
4. [Performance favors library code](#performance-favors-library-code)
5. [Both immutable and mutable types](#both-immutable-and-mutable-types)
6. [Sequences can be unwrapped](#sequences-can-be-unwrapped)
7. [Strings of bytes or characters](#strings-of-bytes-or-characters)
8. [Multiple string literals](#multiple-string-literals)
9. [Strings for documentation](#strings-for-documentation)
10. [Built-in hashes](#built-in-hashes)
11. [Functions and types are values](#functions-and-types-are-values)
12. [Types act like functions](#types-act-like-functions)
13. [ints have no upper bound](#ints-have-no-upper-bound)
14. [Built-in complex numbers](#built-in-complex-numbers)
15. [Two division operators](#two-division-operators)
16. [Every function returns a value](#every-function-returns-a-value)
17. [Many styles of arguments](#many-styles-of-arguments)
18. [Flexible classes and objects](#flexible-classes-and-objects)
19. [No this keyword](#no-this-keyword)
20. [Comprehensions](#comprehensions)
21. [Generators](#generators)
22. [Closures](#closures)
23. [Async functions](#async-functions)

---

### Dynamically typed

- All values in Python are stored as a pair (typecode, other).
- Dynamic typing allows reusing a variable for different types.
- Optional type annotation syntaxes and toolchains are available to detect typing bugs.

### Implicit variable declaration

- Python does not have a special variable declaration syntax.
- Typos in variable names are hard to detect due to implicit declaration.
- Similar rule applies to members of objects.

### Non-lexical scoping

- Python uses non-lexical scoping for variables.
- Variable scopes belong to modules and functions.
- Scopes include local, global, and builtins scope.

### Performance favors library code

- Python's performance favors brevity and library usage.
- Python's implementation in C results in faster execution of library code.

### Both immutable and mutable types

- Immutable types cannot be changed, while mutable types can.
- Common immutable types include bool, int, str, and tuple.
- Common mutable types include list, dict, and set.

### Sequences can be unwrapped

- A sequence of n values can be assigned to n variables.
- Unwrapping also works for implicit assignments and expressions.

### Strings of bytes or characters

- Python differentiates between strings of bytes (bytes) and Unicode characters (str).
- Conversion between bytes and str must be explicit.

### Multiple string literals

- Strings may be delimited using single or double quotes.
- Triple quotes allow newlines inside the literal string.

### Strings for documentation

- String literals at the beginning of functions/classes are saved as docstrings.

### Built-in hashes

- Python's dict and set types are hash maps.
- Keys must be hashable, i.e., immutable types.

### Functions and types are values

- Functions and types are stored as values.
- Functions and types can be reassigned like variables.

### Types act like functions

- Types can be used to convert values of one type to another.
- Some built-in functions behave like types.

### ints have no upper bound

- Integers have no upper bound in Python.
- Operations with very large integers may have performance issues.

### Built-in complex numbers

- Python has a built-in complex number type.
- Complex numbers are stored as a pair of floats.

### Two division operators

- Double-slash division always returns an int result.
- Single-slash division always returns a float result.

### Every function returns a value

- Every function invocation returns a value, defaulting to None.

### Many styles of arguments

- Functions support positional and keyword arguments.
- Functions can have required, optional, positional-only, and keyword-only parameters.
- Functions can also have variadic positional and keyword parameters.

### Flexible classes and objects

- Python classes can have fields, methods, and superclasses.
- Classes can be implemented in C or Python.

### No this keyword

- In Python, class methods use 'self' instead of 'this'.
- Constructors are methods named __init__ and take 'self' as the first argument.

### Comprehensions

- Python supports set-builder-notation-like syntax for looping over collections and creating new collections.

### Generators

- Generators can generate values of a collection on demand.
- Created using comprehension or functions with a 'yield' statement.

### Closures

- Python supports closures: functions with attached copies of referenced variables.

### Async functions

- Functions defined with 'async def' return coroutines.
- Coroutines are used for asynchronous programming.
