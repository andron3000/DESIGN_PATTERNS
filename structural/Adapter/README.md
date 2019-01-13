# Adapter

**Structural design pattern.**

The Adapter Pattern describes how to convert an object into another object which a clients expects. This pattern mainly adapts one object to another one. Adapters allow objects to work together that couldn’t otherwise because of incompatible interfaces.

Adapter allows to reuse existing coding without changing it, as the adapter ensures the conversion between the different interfaces.

In comparison to a decorator pattern, **the Adapter Pattern only converts objects, while the Decorator Pattern adds new functionality to an existing object**. Therefore, the decorator does not change the existing interface.


### Example

``` Java

```
### Documentation

https://www.youtube.com/watch?v=ANlcc2p9kCUhttps://www.youtube.com/watch?v=uE0SGhA1QbE

### Applicability

Use the Facade pattern when:

* you want to provide a simple interface to a complex subsystem. 

* there are many dependencies between clients and the implementation classes of an abstraction. Introduce a facade to decouple the subsystem from clients and other subsystems, thereby promoting subsystem independence and portability.

* you want to layer your subsystems. Use a facade to define an entry point to each subsystem level.
