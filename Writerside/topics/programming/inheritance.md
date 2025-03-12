# Inheritance

Inheritance is a mechanism in which one class acquires the properties and behavior of another class. 
It represents an "is-a" relationship. 
It is used for code reusability and method overriding.

For example, consider a `Vehicle` class that has properties like `make`, `model`, and `year`.
You can create a `Car` class that inherits from the `Vehicle` class and adds properties like `numDoors` and `numSeats`.

Here is an example of inheritance in Java:

```java
class Vehicle {
    public String make;
    public String model;
    public int year;

    public Vehicle(String make, String model, int year) {
        this.make = make;
        this.model = model;
        this.year = year;
    }
}

class Car extends Vehicle {
    public int numDoors;
    public int numSeats;

    public Car(String make, String model, int year, int numDoors, int numSeats) {
        super(make, model, year);
        this.numDoors = numDoors;
        this.numSeats = numSeats;
    }
}
```

The `super` keyword is used to call the constructor of the superclass (`Vehicle` in this case) from the subclass (`Car`).
Java requires that the constructor of the superclass be called as the first statement in the constructor of the subclass.

You can create an object of the `Car` class and access its properties like this:

```java
public class Main {
    public static void main(String[] args) {
        Car myCar = new Car("Toyota", "Camry", 2020, 4, 5);
        System.out.println(myCar.make); // Output: Toyota
        System.out.println(myCar.numDoors); // Output: 4
    }
}
```

## Method Overriding

Method overriding is a feature that allows a subclass to provide a specific implementation of a method that is already provided by its superclass.
It is used to achieve runtime polymorphism (this sounds fancy, but it just means that the method that gets called is determined at runtime based on the type of the object).

For example, consider a `Vehicle` class with a `start` method.
You can create a `Car` class that overrides the `start` method to provide a specific implementation for starting a car.

Here is an example of method overriding in Java:

```java
class Vehicle {
    public void start() {
        System.out.println("Vehicle is starting");
    }
}

class Car extends Vehicle {
    @Override
    public void start() {
        System.out.println("Car is starting");
    }
}
```

The `@Override` annotation is used to indicate that the method in the subclass is overriding a method in the superclass.
This annotation is optional but recommended, as it helps catch errors if the method in the superclass is changed or removed.

You can call the `start` method on an object of the `Car` class like this:

```java
public class Main {
    public static void main(String[] args) {
        Car myCar = new Car();
        myCar.start(); // Output: Car is starting
    }
}
```

## Polymorphism

Polymorphism is the ability of an object to take on many forms.
In Java, polymorphism is achieved through method overriding and method overloading.

For example, consider the `start` method in the `Vehicle` and `Car` classes.

Method overriding allows the `start` method in the `Car` class to provide a specific implementation that is different from the `start` method in the `Vehicle` class.

Consider the following example using method overriding:

```java
class Main {
    public static void main(String[] args) {
        Vehicle myVehicle = new Car("Toyota", "Camry", 2020, 4, 5);
        Car myCar = new Car("Toyota", "Corolla", 2022, 4, 5);
        myVehicle.start(); // Output: Car is starting
        myCar.start(); // Output: Car is starting
    }
}
```

In both cases, the `start` method of the `Car` class is called, even though the `myVehicle` variable is declared as a `Vehicle` type.
This is because the actual object is of type `Car`, and Java determines which method to call based on the type of the object at runtime.

## The Object Class

In Java, every class is a subclass of the `Object` class.
The `Object` class is the root class of the Java class hierarchy and provides some common methods that are inherited by all classes.

Some of the commonly used methods from the `Object` class are:
- `toString()`: Returns a string representation of the object.
- `equals(Object obj)`: Indicates whether some other object is "equal to" this one.

If a class does not explicitly extend another class, it implicitly extends the `Object` class.

The `toString` method is often overridden in classes to provide a meaningful string representation of the object,
as Java will call the `toString` method when you try to print an object using `System.out.println`,
or when you concatenate an object with a string using the `+` operator.
The default implementation of the `toString` method in the `Object` class returns a string that consists of the class name and the memory address of the object,
which is not very useful for most cases.

Here is an example of overriding the `toString` method in Java:

```java
class Person {
    private String name;
    private int age;

    public Person(String name, int age) {
        this.name = name;
        this.age = age;
    }

    @Override
    public String toString() {
        return "Person{name='" + name + "', age=" + age + "}";
    }
}

public class Main {
    public static void main(String[] args) {
        Person person = new Person("Alice", 30);
        System.out.println(person); // Output: Person{name='Alice', age=30}
    }
}
```

## Abstract Classes

An abstract class is a class that cannot be instantiated (you cannot create objects of an abstract class).

Abstract classes are used to define common behavior that can be shared by multiple subclasses.

To declare an abstract class in Java, you use the `abstract` keyword. 
Its methods can be either abstract (with no implementation) or concrete (with an implementation).
Abstract methods are declared with the `abstract` keyword just like classes and have no body,
while concrete methods have a body and are implemented in the abstract class.

Subclasses of an abstract class must provide implementations for all the abstract methods of the superclass.

Here is an example of an abstract class in Java:

```java
abstract class Shape {
    public abstract double area();
}

class Circle extends Shape {
    private double radius;

    public Circle(double radius) {
        this.radius = radius;
    }

    @Override
    public double area() {
        return Math.PI * radius * radius;
    }
}
```

In this example, the `Shape` class is declared as abstract, and it has an abstract method `area`. 
The `Circle` class extends the `Shape` class and provides a specific implementation of the `area` method.
This allows you to create objects of the `Circle` class and call the `area` method on them.

Here is an example of using the `Circle` class:

```java
public class Main {
    public static void main(String[] args) {
        Circle myCircle = new Circle(5);
        System.out.println(myCircle.area()); // Output: 78.53981633974483
        
        Shape myShape = new Circle(10);
        System.out.println(myShape.area()); // Output: 314.1592653589793
    }
}
```

Again, even though the `myShape` variable is declared as a `Shape` type, 
the `area` method of the `Circle` class is called because the actual object is of type `Circle`.

Because abstract classes cannot be instantiated, you cannot create objects of the `Shape` class directly.
That means the following code would result in a compilation error:

```java
public class Main {
    public static void main(String[] args) {
        Shape myShape = new Shape(); // Compilation error
    }
}
```

## Interfaces

An interface is a reference type in Java that is similar to a class but can only contain constants, method signatures, default methods, static methods, and nested types.

Interfaces are also used to define common behavior that can be shared by multiple classes.
They are often used for achieving abstraction and multiple inheritance in Java,
as a class can `implement` multiple interfaces but can only `extend` one class.

To declare an interface in Java, you use the `interface` keyword.

Here is an example of an interface in Java:

```java
interface Animal {
    void eat();
    void sleep();
}

class Dog implements Animal {
    @Override
    public void eat() {
        System.out.println("Dog is eating");
    }

    @Override
    public void sleep() {
        System.out.println("Dog is sleeping");
    }
}
```

Just like abstract classes, interfaces cannot be instantiated, and their methods do not have a body.
Note that abstract methods in interfaces do not need the `abstract` keyword, as they are implicitly abstract.

Interfaces can also have default methods, which provide a default implementation for the method,
and static methods, such as those described in the [](classes-objects.md) section.

## Interface vs. Abstract Class

Interfaces and abstract classes are similar in that they both define common behavior that can be shared by multiple classes.
However, there are some key differences between them:

| Feature               | Abstract Class                                                | Interface                                                                      |
|-----------------------|---------------------------------------------------------------|--------------------------------------------------------------------------------|
| Declaration           | `abstract class ClassName`                                    | `interface InterfaceName`                                                      |
| Instantiation         | Cannot be instantiated                                        | Cannot be instantiated                                                         |
| Method Implementation | Can have both abstract and concrete methods                   | Can have abstract, default, and static methods                                 |
| Multiple Inheritance  | A class can extend only one class, including abstract classes | A class can implement multiple interfaces                                      |
| Fields                | Can have instance variables                                   | Can only have constants (static final fields)                                  |
| Constructor           | Can have constructors                                         | Cannot have constructors                                                       |
| Access Modifiers      | Can have any access modifiers (public, protected, etc.)       | Methods are implicitly public and abstract (except default and static methods) |
| Inheritance           | Use `extends` keyword                                         | Use `implements` keyword                                                       |

## Java Provided Interfaces

Java provides several built-in interfaces that define common behavior for classes that implement them.
Some of the commonly used interfaces in Java are:
- `Comparable`: Used to define a natural ordering of objects.
- `Runnable`: Used to define a task that can be executed by a thread.
- `Iterable`: Used to define an object that can be iterated over.

These interfaces are part of the Java API and are used in various Java classes and libraries.

Here is an example of using the `Comparable` interface in Java:

```java
class Person implements Comparable<Person> {
    private String name;
    private int age;

    public Person(String name, int age) {
        this.name = name;
        this.age = age;
    }

    @Override
    public int compareTo(Person otherPerson) {
        return this.age - otherPerson.age;
    }
}
```

In this example, the `Person` class implements the `Comparable` interface and provides a specific implementation for the `compareTo` method.
This allows you to compare `Person` objects based on their age.