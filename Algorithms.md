# Algorithms

## Recursion

**Morphism** is a function which transforms one data structure to another. All recursion schemes are morphisms, with their prefixes giving a hint about the kind of transformation they involve.

There are 4 recursion schemes:
* Catamorphisms
* Anamorphisms
* Hylomorphisms
* Paramorphism

### Catamorphisms
A function “tears down” a data structure by recursing on it with a function that collapses a functor into its contained type. Visitor pattern is a specific example of catamorphism. When implementing a catamorphism, the goal is provide access to the key structural information of a type in a safe an exhausitive manner. 

The catamorphism for Optional can be written in terms of two functions: present and empty. Callers of the catamorphism provide both lambda’s (or other implementations) of both function types, only one of which is selectively executed depending on the state. This is effectively similar to pattern matching.

```scala
val present = Option[Int] = Some(10)
val a = present match {
    case Some(i) => i + 1
    case None => -1
}
```


# References

[Catamorphisms for Java developers](https://hackernoon.com/catamorphisms-for-java-developers-e3cc10b43d03)

