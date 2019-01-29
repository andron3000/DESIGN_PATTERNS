# Flyweight

**Structural design pattern.**

Flyweight design pattern is used when we need to create a lot of Objects of a class. 
Since every object consumes memory space that can be crucial for low memory devices, 
such as mobile devices or embedded systems, 
flyweight design pattern can be applied to reduce the load on memory by sharing objects.

### Example

``` Java
public interface Shape {
   void draw();
}

public class Circle implements Shape {
   private String color;
   private int x;
   private int y;
   private int radius;

   public Circle(String color){
      this.color = color;		
   }

   public void setX(int x) {
      this.x = x;
   }

   public void setY(int y) {
      this.y = y;
   }

   public void setRadius(int radius) {
      this.radius = radius;
   }

   @Override
   public void draw() {
      System.out.println("Circle: Draw() [Color : " + color + ", x : " + x + ", y :" + y + ", radius :" + radius);
   }
}

public class ShapeFactory {

   // Uncomment the compiler directive line and
   // javac *.java will compile properly.
   // @SuppressWarnings("unchecked")
   private static final HashMap circleMap = new HashMap();

   public static Shape getCircle(String color) {
      Circle circle = (Circle)circleMap.get(color);

      if(circle == null) {
         circle = new Circle(color);
         circleMap.put(color, circle);
         System.out.println("Creating circle of color : " + color);
      }
      return circle;
   }
}

public class FlyweightPatternDemo {
   private static final String colors[] = { "Red", "Green", "Blue", "White", "Black" };
   public static void main(String[] args) {

      for(int i=0; i < 20; ++i) {
         Circle circle = (Circle)ShapeFactory.getCircle(getRandomColor());
         circle.setX(getRandomX());
         circle.setY(getRandomY());
         circle.setRadius(100);
         circle.draw();
      }
   }
   private static String getRandomColor() {
      return colors[(int)(Math.random()*colors.length)];
   }
   private static int getRandomX() {
      return (int)(Math.random()*100 );
   }
   private static int getRandomY() {
      return (int)(Math.random()*100);
   }
}
```
### Documentation

https://www.youtube.com/watch?v=AEmYXzSOIDk

### Applicability

Use the Flyweight pattern when:

* the number of Objects to be created by application should be huge.

* the object creation is heavy on memory and it can be time consuming too. 

* the object properties can be divided into intrinsic and extrinsic properties, 
extrinsic properties of an Object should be defined by the client program..
