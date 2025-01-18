# Understanding Static Variables and Static Blocks in Java

### When to Use Static Variables:
- When you want to store a value that should be shared across all instances of a class (e.g., constants like PI or a counter for object creation).
- When you need a single instance of a class (Singleton pattern).

#### Can be accessed using:
- **ClassName.staticVariable**
- **objectReference.staticVariable** (though using the class name is preferred).

---

## Example 1: Using Static Variable for Area of a Circle

```java
package com.surya;

public class AreaOfCircle {

    private static double pi = 3.14;

    public double getArea(int r) {
        return pi * r * r;
    }

    public static void main(String[] args) {
        AreaOfCircle circle = new AreaOfCircle();
        double area = circle.getArea(5);
        System.out.println(area);
    }
}
## Example 2 :
package com.surya;
public class Printer {
	private static int counter;
	public void print() {
		System.out.println("printing started");
		for (int i = 0; i <= 3; i++) {
			System.out.println("Printing. . ...");
		}
		counter++;
		System.out.println("printing ended");
	}
	public static void main(String[] args) {
		Printer p1 = new Printer();
		p1.print();
		p1.print();
		p1.print();
		Printer p2 = new Printer();
		p2.print();
		p2.print();
		p2.print();

		System.out.println("how many times printer used " + Printer.counter);

	}

}

What are static blocks?
Static Blocks or Static Initializers in Java
three ways to initialize static variables in Java:
1.	At the Time of Declaration: Static variables can be initialized directly at the time of their declaration. This is the simplest and most straightforward method.
private static int count = 10;
2.	Using a Static Block: A static block (or static initializer) is used to initialize static variables when more complex initialization or setup is needed. The static block is executed once when the class is loaded into memory.
static {
    count = 10;
}
3.	Using a Static Method: A static method can be used to initialize static variables. This approach provides more flexibility, allowing additional logic or conditions to be applied during initialization.
public static void initialize() {
    count = 10;
}

In Java, static blocks or static initializers are special code blocks used to initialize static fields or perform logic that needs to be executed once when the class is loaded into memory.








Key Characteristics:
1.	Executed Once:
o	Static blocks are executed exactly once, and this happens when the class is loaded by the JVM.
o	This is even before any object of the class is created or any constructor is called.
2.	Purpose:
o	To initialize static variables.
o	To execute one-time logic, such as setting up a database connection or loading configuration files.
3.	Scope:
o	Static blocks can access static variables and methods directly, but cannot directly access instance variables or methods (since they belong to the object, not the class).
4.	Order of Execution:
o	If there are multiple static blocks in a class, they are executed in the order in which they appear in the code.
________________________________________











package com.surya;

public class AreaOfCircle {

	private static double pi;


	static {
		pi=3.14;
	}

	public double getArea(int r) {

		return pi * r * r;

	}

	public static void main(String[] args) {

		AreaOfCircle circle = new AreaOfCircle();

		double area = circle.getArea(5);

		System.out.println(area);

	}

}


Note similarly we have also an instance block in order to initialise the instance variable this will be executed before the before the constructor execution

When it executes: The instance block runs each time an object of the class is created, before the constructor is executed.

public class Example {
    private int count;

    // Instance initializer block
    {
        count = 10;  // Initialize instance variable
        System.out.println("Instance block executed.");
    }

    public Example() {
        System.out.println(count);
    }

    public static void main(String[] args) {
        Example obj = new Example();  // Create an object, triggering the instance block and constructor
        System.out.println("Count: " + obj.count);
    }
}

