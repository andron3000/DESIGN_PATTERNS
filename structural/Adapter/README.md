# Adapter

**Structural design pattern.**

The Adapter Pattern describes how to convert an object into another object which a clients expects. This pattern mainly adapts one object to another one. Adapters allow objects to work together that couldn’t otherwise because of incompatible interfaces.

Adapter allows to reuse existing coding without changing it, as the adapter ensures the conversion between the different interfaces.

In comparison to a decorator pattern, **the Adapter Pattern only converts objects, while the Decorator Pattern adds new functionality to an existing object**. Therefore, the decorator does not change the existing interface.


### Example

``` Java
interface Shape {
    void draw(int x, int y, int z, int j);
}

class Line {
    public void draw(int x1, int y1, int x2, int y2) {
        System.out.println("Line from point A(" + x1 + ";" + y1 + "), to point B(" + x2 + ";" + y2 + ")");
    }
}

class Rectangle {
    public void draw(int x, int y, int width, int height) {
        System.out.println("Rectangle with coordinate left-down point (" + x + ";" + y + "), width: " + width
                + ", height: " + height);
    }
}

class LineAdapter implements Shape {
    private Line adaptee;

    public LineAdapter(Line line) {
        this.adaptee = line;
    }

    @Override
    public void draw(int x1, int y1, int x2, int y2) {
        adaptee.draw(x1, y1, x2, y2);
    }
}

class RectangleAdapter implements Shape {
    private Rectangle adaptee;

    public RectangleAdapter(Rectangle rectangle) {
        this.adaptee = rectangle;
    }

    @Override
    public void draw(int x1, int y1, int x2, int y2) {
        int x = Math.min(x1, x2);
        int y = Math.min(y1, y2);
        int width = Math.abs(x2 - x1);
        int height = Math.abs(y2 - y1);
        adaptee.draw(x, y, width, height);
    }
}

public class AdapterDemo {
    public static void main(String[] args) {
        Shape[] shapes = {new RectangleAdapter(new Rectangle()),
                          new LineAdapter(new Line())};
        int x1 = 10, y1 = 20;
        int x2 = 30, y2 = 60;
        for (Shape shape : shapes) {
            shape.draw(x1, y1, x2, y2);
        }
    }
}
```
### Documentation

https://www.youtube.com/watch?v=ANlcc2p9kCUhttps://www.youtube.com/watch?v=uE0SGhA1QbE

### Applicability

Use the Facade pattern when:

* you want to provide a simple interface to a complex subsystem. 

* there are many dependencies between clients and the implementation classes of an abstraction. Introduce a facade to decouple the subsystem from clients and other subsystems, thereby promoting subsystem independence and portability.

* you want to layer your subsystems. Use a facade to define an entry point to each subsystem level.
