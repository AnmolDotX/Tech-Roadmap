# Programming Language Familiarization: Python, Go, and JavaScript

A practical question bank for building muscle memory when learning a new
programming language.

The goal is not to memorize syntax. The goal is to learn how the
language represents data, handles control flow, manages errors,
organizes code, and implements common data structures.

## How to use this question bank

For each language you learn:

1.  Answer the basic questions by writing small programs from scratch.
2.  Complete the data-structure exercises using that language's
    idiomatic built-ins first.
3.  Reimplement selected structures manually to understand how they
    work.
4.  Complete the language-specific questions.
5.  Run your code, test edge cases, and explain the time and space
    complexity where relevant.
6.  Avoid looking up a complete solution before attempting the problem.
    Consult official documentation when you need to verify language
    behavior.

Suggested order:

1.  Basic syntax and control flow
2.  Functions and code organization
3.  Types, errors, and runtime behavior
4.  Built-in data structures
5.  Data-structure implementation exercises
6.  Language-specific questions
7.  Testing, tooling, and small integration exercises

------------------------------------------------------------------------

# Section 1 --- Basic Language Muscle Memory

Complete these in **Python, Go, and JavaScript**. Keep the behavior the
same, but use each language's idiomatic approach.

## 1.1 Variables, types, and operators

-   [ ] Declare variables using the language's standard declaration
    syntax.
-   [ ] Create values representing an integer, decimal number, string,
    boolean, and a missing/empty value.
-   [ ] Print each value and inspect its type.
-   [ ] Convert a numeric string into an integer and a decimal number.
-   [ ] Convert an integer to a string.
-   [ ] Swap two variables, first with a temporary variable and then
    idiomatically.
-   [ ] Calculate the quotient and remainder of two integers.
-   [ ] Demonstrate the difference between integer division and
    floating-point division.
-   [ ] Compare two values and combine conditions using logical
    operators.
-   [ ] Check whether a number is even or odd.
-   [ ] Determine the largest of three numbers.
-   [ ] Explore what happens when you combine incompatible types.

## 1.2 Input and output

-   [ ] Read a name and print a personalized greeting.
-   [ ] Read two numbers and print their sum, difference, product,
    quotient, and remainder.
-   [ ] Print multiple values in one output statement.
-   [ ] Format a number to two decimal places.
-   [ ] Print a multiline string.
-   [ ] Read input containing multiple space-separated values and parse
    it.

## 1.3 Conditions and branching

-   [ ] Determine whether a number is positive, negative, or zero.
-   [ ] Check whether a year is a leap year.
-   [ ] Convert a numeric score into a grade using ranges.
-   [ ] Find the largest of three values without using a built-in
    maximum function.
-   [ ] Build a simple calculator using an operator and two numbers.
-   [ ] Rewrite a conditional using the language's idiomatic
    alternative, if one exists.
-   [ ] Handle an invalid or unexpected option.

## 1.4 Loops and iteration

-   [ ] Print numbers from 1 to N.
-   [ ] Print all even numbers from 1 to N.
-   [ ] Calculate the sum of numbers from 1 to N.
-   [ ] Calculate a factorial iteratively.
-   [ ] Print a multiplication table.
-   [ ] Count the digits in an integer.
-   [ ] Reverse the digits of an integer.
-   [ ] Determine whether an integer is a palindrome.
-   [ ] Print a simple right-triangle pattern.
-   [ ] Iterate over a collection with both the value and its index.
-   [ ] Iterate over a collection while modifying or filtering it
    safely.
-   [ ] Compare a traditional loop with the language's idiomatic
    iteration construct.

## 1.5 Functions

-   [ ] Write a function that adds two numbers.
-   [ ] Write a function that returns the maximum of two values.
-   [ ] Write a function that accepts optional/default arguments where
    supported.
-   [ ] Write a function that accepts a variable number of arguments
    where supported.
-   [ ] Write a function that returns multiple pieces of information,
    using the language's idiomatic pattern.
-   [ ] Distinguish printing a result from returning a result.
-   [ ] Write a function that validates an email-like string without
    using a third-party package.
-   [ ] Write a recursive factorial function.
-   [ ] Write an iterative version of the same function.
-   [ ] Explain the difference between local and global variables.
-   [ ] Demonstrate how the language passes values or references to
    functions.
-   [ ] Write a pure function and compare it with one that changes
    external state.

## 1.6 Strings

-   [ ] Find the length of a string.
-   [ ] Access the first and last characters safely.
-   [ ] Reverse a string.
-   [ ] Count vowels and consonants.
-   [ ] Count the frequency of each character.
-   [ ] Check whether a string is a palindrome, ignoring case.
-   [ ] Remove leading/trailing whitespace.
-   [ ] Split a sentence into words and join the words using a
    delimiter.
-   [ ] Find the first occurrence of a substring.
-   [ ] Replace all occurrences of a substring.
-   [ ] Determine whether strings are equal, case-sensitively and
    case-insensitively.
-   [ ] Investigate whether strings are mutable or immutable in the
    language.

## 1.7 Arrays, lists, slices, and collections

-   [ ] Create a collection and add elements.
-   [ ] Access, update, and remove an element.
-   [ ] Iterate over elements and indices.
-   [ ] Find the minimum, maximum, and sum without built-ins.
-   [ ] Find the second-largest distinct value.
-   [ ] Remove duplicates while preserving order.
-   [ ] Reverse a collection in place and create a reversed copy.
-   [ ] Merge two collections.
-   [ ] Filter elements using a condition.
-   [ ] Transform every element using a function.
-   [ ] Sort numbers in ascending and descending order.
-   [ ] Copy a collection and test whether the copy is independent.
-   [ ] Investigate slicing, copying, aliasing, and mutation behavior.

## 1.8 Maps, dictionaries, and sets

-   [ ] Create a key-value collection and read a value by key.
-   [ ] Insert, update, and delete entries.
-   [ ] Check whether a key exists.
-   [ ] Iterate over keys, values, and key-value pairs.
-   [ ] Count word frequency in a sentence.
-   [ ] Group strings by their first character.
-   [ ] Find duplicate values in a collection.
-   [ ] Create a set and remove duplicate values.
-   [ ] Compute union, intersection, and difference of two sets.
-   [ ] Investigate whether map/dictionary iteration order is
    guaranteed.

## 1.9 Errors and exceptions

-   [ ] Trigger and handle an invalid numeric conversion.
-   [ ] Handle division by zero.
-   [ ] Validate a function's input and return or raise an appropriate
    error.
-   [ ] Demonstrate how an error propagates through multiple function
    calls.
-   [ ] Clean up a resource even if an operation fails.
-   [ ] Distinguish expected validation errors from unexpected internal
    failures.
-   [ ] Create a custom error type or exception.
-   [ ] Decide when to return an error value and when to throw/raise an
    exception, according to the language.

## 1.10 Modules, packages, and code organization

-   [ ] Split a program into at least two files.
-   [ ] Import a function or type from another file.
-   [ ] Export a public function and keep an implementation detail
    private.
-   [ ] Create a reusable utility module.
-   [ ] Understand the difference between a script's entry point and an
    importable module.
-   [ ] Install and use one external dependency.
-   [ ] Pin or record dependency versions.
-   [ ] Run the application from the command line.

## 1.11 Types, classes, and interfaces

-   [ ] Define a type representing a user with an ID, name, and email.
-   [ ] Create instances and access their fields.
-   [ ] Add methods that operate on an instance.
-   [ ] Define constructors or factory functions.
-   [ ] Demonstrate encapsulation or the language's closest idiomatic
    equivalent.
-   [ ] Compose one type from another.
-   [ ] Implement an interface, protocol, or structural contract where
    supported.
-   [ ] Explain composition versus inheritance.
-   [ ] Make a function accept an abstraction instead of one concrete
    implementation.
-   [ ] Compare a class-based design with a simple function-based
    design.

## 1.12 Files, JSON, and environment

-   [ ] Read a text file and count its lines.
-   [ ] Write data to a file and read it back.
-   [ ] Parse JSON into structured data.
-   [ ] Serialize structured data into JSON.
-   [ ] Handle malformed JSON.
-   [ ] Read an environment variable.
-   [ ] Load configuration without hardcoding secrets.
-   [ ] Handle missing files and permission errors.
-   [ ] Understand relative versus absolute file paths.

## 1.13 Testing and debugging

-   [ ] Write tests for a function's normal behavior.
-   [ ] Test empty input, boundary values, and invalid input.
-   [ ] Test a function that returns an error.
-   [ ] Use a debugger or print/logging statements to inspect execution.
-   [ ] Reproduce and fix an off-by-one error.
-   [ ] Run a formatter and linter.
-   [ ] Explain the difference between a unit test and an integration
    test.

------------------------------------------------------------------------

# Section 2 --- Data Structures: Five Questions Each

For every data structure, first use the language's built-in
implementation where available. Then implement the structure manually
when practical. The point is to learn both the data structure and the
language's API, memory model, and conventions.

## 2.1 Dynamic array / list / slice

1.  [ ] Create a collection, append five values, and access an element
    by index.
2.  [ ] Insert and delete an element at a specified index. What is the
    time complexity?
3.  [ ] Remove duplicates while preserving the original order.
4.  [ ] Implement a dynamic array abstraction that tracks length and
    capacity, and grows when full.
5.  [ ] Investigate capacity growth, copying, aliasing, and the cost of
    appending elements in the language.

**Language notes:** Python `list`; JavaScript `Array`; Go arrays and
slices. Go slices are descriptors over an underlying array, so copying a
slice does not necessarily copy its elements.

## 2.2 Strings

1.  [ ] Reverse a string without relying on a one-call reverse helper.
2.  [ ] Count the frequency of each character.
3.  [ ] Determine whether two strings are anagrams.
4.  [ ] Find the first non-repeating character.
5.  [ ] Investigate string immutability, character indexing, Unicode,
    and the difference between bytes and characters.

**Language notes:** Python strings are Unicode sequences; JavaScript
strings use UTF-16 code units; Go strings are byte sequences commonly
containing UTF-8. Correct Unicode handling differs across them.

## 2.3 Hash map / dictionary

1.  [ ] Count the frequency of each word in a paragraph.
2.  [ ] Find the first value that appears more than once using a map.
3.  [ ] Group a list of words by their first character.
4.  [ ] Implement a simple hash table with collision handling, such as
    separate chaining.
5.  [ ] Investigate key equality, hashability, missing-key behavior,
    iteration order, and average versus worst-case lookup complexity.

**Language notes:** Python `dict`; JavaScript `Map` and plain objects;
Go `map`.

## 2.4 Set

1.  [ ] Remove duplicates from a collection.
2.  [ ] Find the intersection of two collections.
3.  [ ] Find the union and difference of two sets.
4.  [ ] Determine whether one set is a subset of another.
5.  [ ] Implement a basic set using a hash map, then investigate how the
    language's built-in set handles membership and equality.

**Language notes:** Python `set`; JavaScript `Set`; Go has no built-in
set type, so a common representation is `map[T]struct{}`.

## 2.5 Stack

1.  [ ] Implement a stack with push, pop, peek, and is-empty operations.
2.  [ ] Reverse a string using a stack.
3.  [ ] Check whether parentheses and brackets are balanced.
4.  [ ] Evaluate a postfix expression.
5.  [ ] Solve the next-greater-element problem using a monotonic stack.

**Language notes:** Python lists are commonly used as stacks; JavaScript
arrays provide stack operations; Go can implement a stack with a slice.

## 2.6 Queue and deque

1.  [ ] Implement enqueue, dequeue, peek, and is-empty operations.
2.  [ ] Simulate a queue of people waiting for service.
3.  [ ] Implement a circular queue with a fixed capacity.
4.  [ ] Use a queue to perform breadth-first traversal of a tree or
    graph.
5.  [ ] Compare a naive array-based queue with a deque or ring buffer.
    Explain the cost of removing from the front.

**Language notes:** Python `collections.deque`; JavaScript commonly
needs a head index or custom deque for efficient front removal; Go can
use a slice or a ring-buffer implementation.

## 2.7 Linked list

1.  [ ] Define a node and build a singly linked list.
2.  [ ] Insert and delete nodes at the head, tail, and a given position.
3.  [ ] Reverse a singly linked list iteratively.
4.  [ ] Detect a cycle using slow and fast pointers.
5.  [ ] Find the middle node and merge two sorted linked lists.

**Language notes:** Python classes, JavaScript objects/classes, and Go
structs with pointers can all represent nodes. Also compare these manual
implementations with standard library linked-list facilities, if
available.

## 2.8 Trees and binary search trees

1.  [ ] Define a binary tree node and construct a small tree.
2.  [ ] Implement preorder, inorder, and postorder traversal.
3.  [ ] Implement breadth-first level-order traversal.
4.  [ ] Insert, search, and delete values in a binary search tree.
5.  [ ] Calculate tree height and determine whether a binary tree is
    balanced.

**Language notes:** Use a class or dataclass in Python, an object/class
in JavaScript, and a struct with pointers in Go. Compare recursive and
iterative traversals.

## 2.9 Heap / priority queue

1.  [ ] Use the language's standard library to create a min-heap or
    priority queue, if available.
2.  [ ] Insert values and repeatedly retrieve the smallest value.
3.  [ ] Find the k largest or k smallest values in a collection.
4.  [ ] Merge two sorted collections using a heap.
5.  [ ] Implement a binary min-heap with insert, peek, and extract-min.

**Language notes:** Python provides `heapq`; JavaScript has no built-in
general-purpose heap; Go's `container/heap` uses an interface
implementation.

## 2.10 Graph

1.  [ ] Represent a graph using an adjacency list.
2.  [ ] Add vertices and edges to a directed and an undirected graph.
3.  [ ] Implement depth-first search (DFS).
4.  [ ] Implement breadth-first search (BFS) and find the shortest path
    in an unweighted graph.
5.  [ ] Detect a cycle in a graph or determine whether all vertices are
    reachable.

**Language notes:** Compare maps of lists/slices with arrays indexed by
vertex IDs. Choose a representation appropriate to the graph's size and
density.

## 2.11 Optional: Trie

1.  [ ] Build a trie and insert words.
2.  [ ] Search for a complete word.
3.  [ ] Check whether any word starts with a given prefix.
4.  [ ] Return all words matching a prefix.
5.  [ ] Compare a trie with a hash set for prefix search, memory use,
    and lookup behavior.

## 2.12 Optional: LRU cache

1.  [ ] Implement a cache with a maximum capacity.
2.  [ ] Support `get` and `put` operations.
3.  [ ] Move a key to the most-recently-used position whenever it is
    accessed.
4.  [ ] Evict the least-recently-used entry when capacity is exceeded.
5.  [ ] Target average O(1) `get` and `put` using a hash map plus a
    doubly linked list.

------------------------------------------------------------------------

# Section 3 --- Python-Specific Familiarization

Complete these after Section 1. Focus on Python behavior and idioms
rather than translating another language's style.

## 3.1 Python syntax and object model

-   [ ] What is the difference between `list`, `tuple`, `set`, and
    `dict`?
-   [ ] What is the difference between mutable and immutable objects?
-   [ ] What does assignment do when two variables refer to the same
    list?
-   [ ] What is the difference between `==` and `is`?
-   [ ] What are truthy and falsy values?
-   [ ] How do `None`, `False`, `0`, and an empty collection differ?
-   [ ] What are list, set, and dictionary comprehensions?
-   [ ] What are unpacking and starred expressions?
-   [ ] What are positional-only, keyword-only, default, and variadic
    arguments?
-   [ ] Why can a mutable default argument cause bugs?
-   [ ] What are `*args` and `**kwargs`?
-   [ ] What is the difference between shallow copy and deep copy?

## 3.2 Functions, scope, and iteration

-   [ ] What is LEGB name resolution?
-   [ ] What is a closure?
-   [ ] What is a generator, and how does `yield` work?
-   [ ] What are iterables and iterators?
-   [ ] How do `enumerate`, `zip`, `any`, and `all` work?
-   [ ] What are decorators, and how can one wrap a function?
-   [ ] When should you use a generator instead of building a list?
-   [ ] What is the difference between a generator expression and a list
    comprehension?

## 3.3 Classes and typing

-   [ ] What is the role of `self`?
-   [ ] What is the difference between instance, class, and static
    methods?
-   [ ] What do `__init__` and `__repr__` do?
-   [ ] What are dunder methods and operator overloading?
-   [ ] What is a dataclass, and when is it useful?
-   [ ] What are inheritance, composition, and method resolution order
    (MRO)?
-   [ ] What are type hints, and are they enforced at runtime by
    default?
-   [ ] What are `Protocol`, `TypedDict`, and generics used for?
-   [ ] What is duck typing?
-   [ ] What are properties and descriptors at a basic level?

## 3.4 Exceptions, resources, and modules

-   [ ] How do `try`, `except`, `else`, and `finally` differ?
-   [ ] How do you define and raise a custom exception?
-   [ ] What does `with` do?
-   [ ] What are context managers?
-   [ ] Why should files be opened with a context manager?
-   [ ] What does `if __name__ == "__main__":` mean?
-   [ ] How do Python imports and packages work?
-   [ ] What is a virtual environment?
-   [ ] What is the purpose of `pyproject.toml`?
-   [ ] How do you install and pin dependencies?

## 3.5 Python runtime and concurrency

-   [ ] What is the Global Interpreter Lock (GIL), and how does it vary
    by Python implementation/version?
-   [ ] When should you use threads, processes, or asynchronous I/O?
-   [ ] What do `async` and `await` mean?
-   [ ] What is an event loop?
-   [ ] Why does calling blocking I/O inside an async function cause
    problems?
-   [ ] What are `asyncio.gather` and task cancellation?
-   [ ] What is the difference between CPU-bound and I/O-bound work?
-   [ ] How do reference counting and garbage collection work at a high
    level?

## 3.6 Python mini-exercises

-   [ ] Implement a word-frequency counter using `Counter`.
-   [ ] Group records using `defaultdict`.
-   [ ] Sort a list of dictionaries using a `key` function.
-   [ ] Write a generator that reads a large file line by line.
-   [ ] Create a context manager or use `contextlib`.
-   [ ] Write a decorator that measures a function's execution time.
-   [ ] Use `dataclasses` to model a task.
-   [ ] Add type hints to a small module and run a static type checker.
-   [ ] Write unit tests with `pytest`.
-   [ ] Implement a small async program that runs multiple I/O tasks
    concurrently.

------------------------------------------------------------------------

# Section 4 --- Go-Specific Familiarization

Go emphasizes simple syntax, explicit error handling, composition, and
built-in concurrency primitives.

## 4.1 Types, declarations, and control flow

-   [ ] What is the difference between `var`, `:=`, and `const`?
-   [ ] What are zero values in Go?
-   [ ] What is the difference between an array and a slice?
-   [ ] How do `len` and `cap` differ?
-   [ ] What happens when appending to a slice exceeds its capacity?
-   [ ] What is a nil slice, and how does it differ from an empty slice?
-   [ ] What is the difference between a map and a struct?
-   [ ] Why are map iteration order and map concurrency behavior
    important?
-   [ ] How do `range`, `switch`, and `select` work?
-   [ ] What are named return values, and when should you avoid them?

## 4.2 Functions, methods, and interfaces

-   [ ] How do multiple return values work?
-   [ ] Why do many Go functions return `(value, error)`?
-   [ ] What is the difference between a function and a method?
-   [ ] What is the difference between a value receiver and a pointer
    receiver?
-   [ ] When should you use a pointer?
-   [ ] How are interfaces implemented implicitly?
-   [ ] What is a nil interface, and why can it be surprising?
-   [ ] What is the difference between embedding and inheritance?
-   [ ] When should an interface be declared by the consumer?
-   [ ] What are type assertions and type switches?
-   [ ] What are generics, and when are they useful?
-   [ ] What are `defer`, `panic`, and `recover`, and when should each
    be used?

## 4.3 Pointers, memory, and errors

-   [ ] What do `&` and `*` mean?
-   [ ] What is a nil pointer?
-   [ ] What is the difference between passing a struct value and a
    pointer?
-   [ ] How can escape analysis move values to the heap?
-   [ ] How does Go's garbage collector work at a high level?
-   [ ] How should errors be wrapped and inspected using `fmt.Errorf`,
    `%w`, `errors.Is`, and `errors.As`?
-   [ ] Why is comparing error strings often inferior to inspecting
    error types or sentinels?
-   [ ] How do you create a custom error type?
-   [ ] Why should `panic` generally not be used for ordinary
    application errors?

## 4.4 Concurrency

-   [ ] What is a goroutine?
-   [ ] How do unbuffered and buffered channels differ?
-   [ ] What happens when sending to or receiving from a nil channel?
-   [ ] What happens when sending to or receiving from a closed channel?
-   [ ] How do you close a channel safely?
-   [ ] How does `select` work?
-   [ ] What is a data race?
-   [ ] When should you use `sync.Mutex` or `sync.RWMutex`?
-   [ ] What does `sync.WaitGroup` solve?
-   [ ] What does `context.Context` do?
-   [ ] How do cancellation and deadlines propagate?
-   [ ] How do you run the race detector?
-   [ ] When is a channel a better fit than a mutex, and vice versa?

## 4.5 Go tooling and mini-exercises

-   [ ] Create a module with `go mod init`.
-   [ ] Add and manage a dependency.
-   [ ] Format code with `gofmt`.
-   [ ] Run `go vet` and `go test`.
-   [ ] Write table-driven tests.
-   [ ] Benchmark a function using Go's testing tools.
-   [ ] Inspect allocations with benchmarks and profiling tools.
-   [ ] Build a small CLI that parses flags and reads environment
    variables.
-   [ ] Use `encoding/json` to marshal and unmarshal structs.
-   [ ] Use struct tags to control JSON field names.
-   [ ] Build a worker pool using goroutines and channels.
-   [ ] Implement graceful cancellation using `context.Context`.
-   [ ] Understand the purpose of `internal/` and `cmd/` directories in
    Go projects.
-   [ ] Build and run a small HTTP server using `net/http` before using
    a framework.

------------------------------------------------------------------------

# Section 5 --- JavaScript-Specific Familiarization

JavaScript has dynamic typing, prototype-based objects, and an event
loop. For backend work, focus on modern JavaScript and Node.js behavior.

## 5.1 Values, scope, and functions

-   [ ] What are the differences between `var`, `let`, and `const`?
-   [ ] What are function scope, block scope, and lexical scope?
-   [ ] What is hoisting?
-   [ ] What is the temporal dead zone?
-   [ ] What are closures?
-   [ ] How do `==` and `===` differ?
-   [ ] What are truthy and falsy values?
-   [ ] How do `null` and `undefined` differ?
-   [ ] What is the difference between primitive values and objects?
-   [ ] How does pass-by-value work when the value is an object
    reference?
-   [ ] How do rest parameters and spread syntax work?
-   [ ] What are default parameters and destructuring?
-   [ ] What is the difference between arrow functions and regular
    functions?
-   [ ] How does `this` behave in different calling contexts?

## 5.2 Objects, prototypes, and classes

-   [ ] How do you create, read, update, and delete object properties?
-   [ ] What is the prototype chain?
-   [ ] How does prototypal inheritance work?
-   [ ] How do JavaScript classes relate to prototypes?
-   [ ] How do instance methods, static methods, and private fields
    work?
-   [ ] What do `Object.keys`, `Object.values`, and `Object.entries`
    return?
-   [ ] What is the difference between object spread and
    `Object.assign`?
-   [ ] What are shallow copies, and how can nested mutation occur?
-   [ ] When should you use `Map` instead of a plain object?
-   [ ] What is the difference between `Map`, `WeakMap`, `Set`, and
    `WeakSet`?

## 5.3 Async JavaScript and the event loop

-   [ ] What is a callback?
-   [ ] What is a Promise?
-   [ ] How do `.then()`, `.catch()`, and `.finally()` work?
-   [ ] How does `async/await` relate to Promises?
-   [ ] How do you handle rejected Promises?
-   [ ] What are the call stack, task queue, and microtask queue?
-   [ ] How do `setTimeout` callbacks and Promise callbacks differ in
    scheduling?
-   [ ] What is the difference between sequential and concurrent
    asynchronous work?
-   [ ] How do `Promise.all`, `Promise.allSettled`, `Promise.race`, and
    `Promise.any` differ?
-   [ ] What happens when one Promise rejects inside `Promise.all`?
-   [ ] How can you limit concurrency when processing many tasks?
-   [ ] What is event-loop blocking, and how can CPU-heavy work affect a
    Node.js server?

## 5.4 Node.js runtime and modules

-   [ ] What is Node.js, and how does it differ from browser JavaScript?
-   [ ] What are the roles of V8 and libuv at a high level?
-   [ ] What is the difference between CommonJS and ES modules?
-   [ ] How do `package.json` and lockfiles work?
-   [ ] What are npm scripts?
-   [ ] How do environment variables work in Node.js?
-   [ ] How do streams and buffers work?
-   [ ] Why should large files often be processed as streams?
-   [ ] How do you handle filesystem errors?
-   [ ] What are process signals and graceful shutdown?
-   [ ] How do you handle uncaught exceptions and unhandled Promise
    rejections responsibly?
-   [ ] How do worker threads differ from child processes?

## 5.5 TypeScript fundamentals (recommended for larger projects)

-   [ ] What is the difference between a type and an interface?
-   [ ] What are union and intersection types?
-   [ ] What are generics?
-   [ ] What are type narrowing and discriminated unions?
-   [ ] Why should `unknown` generally be preferred over `any` at
    untrusted boundaries?
-   [ ] What are optional properties and optional chaining?
-   [ ] What are utility types such as `Partial`, `Pick`, `Omit`, and
    `Record`?
-   [ ] How do you type an asynchronous function?
-   [ ] How do you type an API request and response?
-   [ ] Why do TypeScript types not automatically validate incoming JSON
    at runtime?

## 5.6 JavaScript mini-exercises

-   [ ] Implement a word-frequency counter using `Map`.
-   [ ] Remove duplicates using `Set`.
-   [ ] Group objects by a property using `Map` or `reduce`.
-   [ ] Implement a Promise-based delay function.
-   [ ] Run multiple async tasks concurrently and handle partial
    failures.
-   [ ] Implement a concurrency limiter.
-   [ ] Use `AbortController` to cancel a fetch request.
-   [ ] Read a large file using streams in Node.js.
-   [ ] Write a small HTTP server using Node.js built-in APIs.
-   [ ] Write tests using Node's built-in test runner or a testing
    framework.
-   [ ] Implement a typed API client in TypeScript with runtime response
    validation.

------------------------------------------------------------------------

# Section 6 --- Comparative Exercises

Solve the same exercise in Python, Go, and JavaScript. Then compare the
implementation, readability, error handling, and runtime behavior.

-   [ ] Parse a line of text into words and count word frequency.
-   [ ] Sort a collection of records by multiple fields.
-   [ ] Read a large file without loading it entirely into memory.
-   [ ] Parse JSON and handle invalid input safely.
-   [ ] Implement a stack and a queue.
-   [ ] Implement a hash table or explain the built-in implementation's
    behavior.
-   [ ] Write a function that returns a value plus an error or
    exception.
-   [ ] Run several I/O operations concurrently.
-   [ ] Build a small HTTP server with one health endpoint.
-   [ ] Write tests for normal, boundary, and failure cases.

## Comparison notes

For each exercise, answer:

1.  What is the idiomatic implementation in this language?
2.  Which built-in types or standard-library packages help?
3.  What behavior surprised me?
4.  What are the time and space complexities?
5.  How does the language handle errors?
6.  What happens with mutation, copying, and references?
7.  How would I test this code?
8.  What would change if this code ran in a production backend?

------------------------------------------------------------------------

# Section 7 --- Completion Checklist

A language is ready for practical project work when you can do the
following without relying on a tutorial for every step:

-   [ ] Write small programs using variables, conditions, loops, and
    functions.
-   [ ] Use the language's built-in collections confidently.
-   [ ] Explain mutation, copying, references, and equality.
-   [ ] Organize code into modules or packages.
-   [ ] Define and use types, classes, structs, or interfaces
    idiomatically.
-   [ ] Handle errors using the language's normal conventions.
-   [ ] Read and write files and JSON.
-   [ ] Install dependencies and run the standard tooling.
-   [ ] Write and run automated tests.
-   [ ] Explain the language's basic concurrency model.
-   [ ] Implement and analyze common data structures.
-   [ ] Build a small command-line tool or HTTP server.
-   [ ] Read official documentation and investigate unfamiliar behavior
    independently.

## Recommended rule

**Do not measure progress by the number of questions checked off.**
Measure it by whether you can implement the behavior from a blank file,
explain why the implementation works, test edge cases, and identify the
language-specific trade-offs.
