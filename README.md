#  Java-8-Learning

This repo consists of the code used to play around with java 8 features.

## Topics Covered

  - Lambda Expressions
  - Functional Interfaces
  - Method referencing
  - Default methods in Interfaces
  - In-built Functional Interfaces
  - Optional
  - Streams
  - Map, Time APIs
  
## Major points

  - Interfaces can have default functions. Use `default` qualifier.
  - No need of anonymous classes for comparators
  - Functional Interfaces with one abstract method make lambda expression possible. Use `@FunctionalInterface` annotation.
  - `::` symbol with method make referencing static methods, object methods, constructors possible.
  - `::new` allows to reference constructors of the classes being accessed.
  - Local Variables outside of the scope of lambda expressions can be accessed without `final` keyboard. But, they should be implicitly final.
  - Instance members and static members of the class can be accessed from within the lambda expression in the method of the same class.
  - Default methods defined in interface cannot be accessed from lambda expressions.
  - In-built Functional Interfaces:
    - `Predicate` are boolean returning functional interfaces / functions. Keywords: `test`, `negate` --> Can be used to defined opposite predicates
    - `Function` are one argument, one result lambda expressions using composition functions like `andThen`, `compose`. Keywords: `apply`
        - `BiFunction` takes in 2 arguments instead of 1. rest all same.
        - Check out `java.util.function` java-package for more.
    - `Supplier` don't take arguments. Mostly initialized to a factory / constructor references. Keywords: `get`
    - `Consumer` takes in one argument but doesn't return anything. Keywords: `accept`
    - `Comparator` takes in two arguments of similar type. Keywords: `compare`, `reversed` --> Can be used to define opposite comparisons
  - `Optional`, Now built-in. Prevents Null-pointer exception. Keywords: `isPresent()`, `get()`, `ifPresent(Consumer<>)`, `orElse(<Same Type>)`, `orElseGet(Supplier)`, `orElseThrow(Supplier)`
  - Streams
    - Terminal (produces resultant object) or Intermediate (produces streams)
    - Operates on Collections (Maps are not supported at the moment)
    - Parallel (`parallelStream()`) or sequential (`stream()`)
    - `filter(<predicate>)`
    - `forEach(<consumer>)` (Terminal)
    - `sorted(<optional comparator>)` - Intermediate, returns a stream; the original collection is untouched
    - `map(<Function>)` - Intermediate
    - Match Operations: `anyMatch`, `allMatch`, `noneMatch`. Takes in predicate and returns in boolean and are terminal (of course!)
    - `count()` - terminal operation; returning the number of objects in the stream
    - `reduce(<two arg lambda expressions>)` - terminal; reduce the stream using the lambda expression
  - Map
    - `forEach(<consumer>)` called directly on map
    - `entrySet()` - gives a set of entries (id, val) pairs, `keys()`, `values()` are set of keys and values respectively
    - `putIfAbsent(key, value)` - updates map only if the key is not present
    - `computeIfAbsent(key, <function>)` - takes in key and a mapping function
    - `computeIfPresent(key, <bifunction>)` - useful to update existing map like increment, decrement counters
    - `merge(key, value, <bifunction>)` - gives both key and new value rather than dabba function
    - `remove(key, value)` - returns value or `null` if not present.
    - `getOrDefault(key, defaultVal)` - self-explanatory
  - Time API
    - Inspired by `Joda-Time` but internal implementation is different.
    - `Instant`, `Clock`, `ZoneID` for Time Zones
    - `LocalTime` represents a time without a timezone. Use `zone` to create a local time object in a particular time zone.
    - Check out `java.time.` java package for more details
    - `LocalDate` - Immutable; analogous to `LocalTime`
    - `LocalDateTime` - combination of both
    - `DateTimeFormatter` along with `FormatStyle` enumerations allows to define a custom time format.
    - Temporal classes with utility methods: `ChronoUnit`, `ChronoField`
  - Annotations
    - Pre-define repeatable annotations and then add repeatable annotations which are internally post-processed for you.
    
## Sources

  - [java8-tutorial](https://github.com/winterbe/java8-tutorial)
  - [Java8 Sorting tutorial](http://www.leveluplunch.com/java/tutorials/007-sort-arraylist-stream-of-objects-in-java8/)
    

## License

The Unlicense

This is free and unencumbered software released into the public domain.

Anyone is free to copy, modify, publish, use, compile, sell, or
distribute this software, either in source code form or as a compiled
binary, for any purpose, commercial or non-commercial, and by any
means.

In jurisdictions that recognize copyright laws, the author or authors
of this software dedicate any and all copyright interest in the
software to the public domain. We make this dedication for the benefit
of the public at large and to the detriment of our heirs and
successors. We intend this dedication to be an overt act of
relinquishment in perpetuity of all present and future rights to this
software under copyright law.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND,
EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF
MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT.
IN NO EVENT SHALL THE AUTHORS BE LIABLE FOR ANY CLAIM, DAMAGES OR
OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE,
ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR
OTHER DEALINGS IN THE SOFTWARE.

For more information, please refer to <http://unlicense.org/>