# Proxy

**Structural design pattern.**

The intent of the proxy-pattern is to provide a placeholder for another object to control access to it. It introduces an additional level of indirection. There are several reasons why you would want to do this, hence there are several uses for this pattern.

### Example

``` Java
interface Image {
    public void displayImage();
}

// On System A
class RealImage implements Image {

    private String filename;
    /**
     * Constructor
     * @param filename
     */
    public RealImage(final String filename) {
        this.filename = filename;
        loadImageFromDisk();
    }

    /**
     * Loads the image from the disk
     */
    private void loadImageFromDisk() {
        System.out.println("Loading   " + filename);
    }

    /**
     * Displays the image
     */
    public void displayImage() {
        System.out.println("Displaying " + filename);
    }

}

// On System B
class ProxyImage implements Image {

    private RealImage image;
    private String filename;
    /**
     * Constructor
     * @param filename
     */
    public ProxyImage(final String filename) {
        this.filename = filename;
    }

    /**
     * Displays the image
     */
    public void displayImage() {
        if (image == null) {
           image = new RealImage(filename);
        }
        image.displayImage();
    }

}

class ProxyExample {

   /**
    * Test method
    */
   public static void main(final String[] arguments) {
        final Image image1 = new ProxyImage("HiRes_10MB_Photo1");
        final Image image2 = new ProxyImage("HiRes_10MB_Photo2");

        image1.displayImage(); // loading necessary
        image1.displayImage(); // loading unnecessary
        image2.displayImage(); // loading necessary
        image2.displayImage(); // loading unnecessary
        image1.displayImage(); // loading unnecessary
    }
}
```
### Documentation

https://www.youtube.com/watch?v=V0ly-mMS4fg

### Applicability

Use the Proxy pattern when:

* there is a need for a more universal or sophisticated reference to an object than just a simple pointer.
