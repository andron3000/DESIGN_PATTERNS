# Abstract Factory

**Creational design pattern.**

The Abstract Factory Pattern provides a way to encapsulate a group of individual factories(factory methods) that have a common theme without specifying their concrete classes.

### Example

``` Java
public interface Button {
	void paint();
}

public interface GUIFactory {
	public Button createButton();
}

public class WinFactory implements GUIFactory {
	@Override
	public Button createButton() {
		return new WinButton();
	}
}

public class OSXFactory implements GUIFactory {
	@Override
	public Button createButton() {
		return new OSXButton();
	}
}

public class WinButton implements Button {
	@Override
	public void paint() {
		System.out.println("WinButton");
	}
}

public class OSXButton implements Button {
	@Override
	public void paint() {
		System.out.println("OSXButton");
	}
}

public class Main {

	public static void main(final String[] arguments) throws Exception {
		GUIFactory factory = null;
		
		final String appearance = randomAppearance();	// Current operating system

		if (appearance.equals("OSX")) {
			factory = new OSXFactory();
		} else if(appearance.equals("Windows")) {
			factory = new WinFactory();
		} else {
			throw new Exception("No such operating system");
		}
		
		final Button button = factory.createButton();

		button.paint();
	}
	
	/**
	 * This is just for the sake of testing this program, and doesn't have to do
	 * with Abstract Factory pattern.
	 * @return
	 */
	public static String randomAppearance() {
		final String[] appearanceArray = new String[3];

		appearanceArray[0] = "OSX";
		appearanceArray[1] = "Windows";
		appearanceArray[2] = "error";
		final java.util.Random random = new java.util.Random();

		final int randomNumber = random.nextInt(3);

		return appearanceArray[randomNumber];
	}
}
```
### Documentation

https://www.youtube.com/watch?v=FYX9l5OQtJE

### Applicability

Use the Abstract Factory pattern when:

*  a.

