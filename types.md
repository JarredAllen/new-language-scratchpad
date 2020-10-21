# Types
---

This language will have built-in types, for integers, floats (both are 64 bits), characters, bytes, etc.

There will also be structs which compose multiple types into one.
They are declared with a syntax like this:
```
struct Foo {
    name :: type,
    name :: type,
    ...
}
```

There are three memory management systems which a structure can use: copied, owned, or garbage-collected:

 * Copied values can be easily duplicated, and so they are duplicated when an assignment is done
   * Built-in numbers, etc. are of this type
   * Structs default to this behavior if all fields are copied

 * Owned values follow ownership semantics like Rust's, and are freed when they go out of scope.
   * Nothing defaults to this type

 * Garbage-collected values are allocated on the heap and pointed to.
   * Structs default to this type if they contain a value which cannot be trivially copied
   * Note to self: Look at Go to see how to do this for a compiled language

To change the memory management type of a struct, you can modify it using a syntax like this:
```
@mem->copied
struct Copied { ... }

@mem->owned
struct Owned { ... }

@mem->gc
struct GarbageCollected { ... }
```

This `@` syntax is a part of the language for modifying items, and will eventually be extendable by code in the language.
The `->` syntax is for getting a name from a namespace (I'm not 100% on this, but I don't want to reuse `::` from types here)

This language also has no memory aliasing rules (of the sort found in Rust), because combining that with garbage collection sounds like a headache.
