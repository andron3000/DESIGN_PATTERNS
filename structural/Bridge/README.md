# Bridge

**Structural design pattern.**

The bridge pattern is a design pattern used in software engineering that is meant to "decouple an abstraction from its implementation
so that the two can vary independently".

### Example

``` Java
public interface Color {

	public void applyColor();
}

public abstract class Shape {
	//Composition - implementor
	protected Color color;
	
	//constructor with implementor as input argument
	public Shape(Color c){
		this.color=c;
	}
	
	abstract public void applyColor();
}

public class Triangle extends Shape{

	public Triangle(Color c) {
		super(c);
	}

	@Override
	public void applyColor() {
		System.out.print("Triangle filled with color ");
		color.applyColor();
	} 

}

public class Pentagon extends Shape{

	public Pentagon(Color c) {
		super(c);
	}

	@Override
	public void applyColor() {
		System.out.print("Pentagon filled with color ");
		color.applyColor();
	} 

}

public class RedColor implements Color{

	public void applyColor(){
		System.out.println("red.");
	}
}

public class GreenColor implements Color{

	public void applyColor(){
		System.out.println("green.");
	}
}

public class BridgePatternTest {

	public static void main(String[] args) {
		Shape tri = new Triangle(new RedColor());
		tri.applyColor();
		
		Shape pent = new Pentagon(new GreenColor());
		pent.applyColor();
	}

}
```
### Documentation

https://www.youtube.com/watch?v=moMF84Mp1tw

### Applicability

Use the Bridge pattern when:

*  you want to avoid a permanent binding between an abstraction and its implementation. This might be the case, for example, when the implementation must be selected or switched at run-time.

*  changes in the implementation of an abstraction should have no impact on clients; that is, their code should not have to be recompiled.

*  both the abstractions and their implementations should be extensible by subclassing. In this case, the Bridge pattern lets you combine the different abstractions and implementations and extend them independently.
