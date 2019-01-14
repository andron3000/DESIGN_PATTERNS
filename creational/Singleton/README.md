# Singleton

**Creational design pattern.**

Ensure a class only has one instance, and provide a global point of access to it.

### Example

``` Java
public class LazyInitializedSingleton {

    private static LazyInitializedSingleton instance;
    
    private LazyInitializedSingleton(){}
    
    public static LazyInitializedSingleton getInstance(){
        if(instance == null){
            instance = new LazyInitializedSingleton();
        }
        return instance;
    }
}
```
### Documentation

https://www.youtube.com/watch?v=u11nr3ifLd0

### Applicability

Use the Singleton pattern when:

*   there must be exactly one instance of a class, and it must be accessible to clients from a well-known access point. 
