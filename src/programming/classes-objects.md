# Classes and Objects

A class is a way to define a new data type.
It is a blueprint for creating objects.
Classes can contain fields (variables) and methods (functions).
When you create an object from a class, you are creating an instance of that class.

In Java, you declare a class using the `class` keyword.

A class has two main parts: fields (also called properties) and methods.

## Fields

Fields are variables that belong to a class.
They define the state of an object.
Fields can be of any data type, including primitive types (e.g., `int`, `double`, `boolean`) and objects (e.g., `String`, `ArrayList`).

For example, a `Car` class might have fields like `make`, `model`, and `year`.

Here is an example of a class with fields:

```java
class Car {
    public String make;
    public String model;
    public int year;
}
```

Since the fields are declared as `public`, they can be accessed from outside the class:

```java
Car myCar = new Car();
myCar.make = "Toyota";
myCar.model = "Corolla";
```

If a field is declared as `private`, it can only be accessed from within the class.

## Methods

Methods are functions that belong to a class.
They define the behavior of an object.

For example, a `Car` class might have methods like `start`, `stop`, and `drive`.

Here is an example of a class with methods:

```java
class Car {
    public void start() {
        System.out.println("Car started");
    }

    public void stop() {
        System.out.println("Car stopped");
    }

    public void drive(double distance) {
        System.out.println("Car is driving " + distance + " miles");
    }
}
```

The `start` and `stop` methods do not take any parameters, 
while the `drive` method takes a `double` parameter `distance`, 
which it can use in the method body.

Methods can also return values; 
a method that returns a value has a return type specified before the method name,
whereas a method that does not return a value has a return type of `void`, like the `start` and `stop` methods above.

Here is an example of a method that returns a value:

```java
class Car {
    public double getMilesPerGallon() {
        return 30.0;
    }
}
```

Here is how you can call methods in Java:

```java
Car myCar = new Car();
myCar.start();
myCar.drive(10.5);
double mpg = myCar.getMilesPerGallon();
```

### Constructors

A constructor is a special method that is called when an object is created.
It is often used to initialize the fields of an object 
or perform any setup that is needed when the object is created.
In Java, a constructor has the same name as the class and no return type.
They are called using the `new` keyword.

Here is an example of a class with a constructor:

```java
class Car {
    public String make;
    public String model;
    public int year;

    public Car(String make, String model, int year) {
        this.make = make;
        this.model = model;
        this.year = year;
    }
}
```

In this example, the `Car` class has a constructor that takes three parameters (`make`, `model`, and `year`),
and initializes the fields of the object with those values.
It uses the `this` keyword to refer to the fields of the object being created,
to distinguish them from the parameters with the same names.

Here is how you can create an object using the constructor:

```java
Car myCar = new Car("Toyota", "Corolla", 2020);
```

### Getters and Setters

Getters and setters are methods that allow you to access and modify the fields of an object,
as often you want to keep fields private to prevent direct access from outside the class.
They can also be used to enforce constraints on the values of the fields,
or perform additional logic when getting or setting a field.

Here is an example of a class with getters and setters:

```java
class Car {
    private String make;
    private String model;
    private int year;

    public String getMake() {
        return make;
    }

    public void setMake(String make) {
        this.make = make;
    }

    public String getModel() {
        return model;
    }

    public void setModel(String model) {
        this.model = model;
    }

    public int getYear() {
        return year;
    }

    public void setYear(int year) {
        if (year >= 1900 && year <= 2022) {
            this.year = year;
        } else {
            throw new IllegalArgumentException("Invalid year");
        }
    }
}
```

In this example, the `make`, `model`, and `year` fields are declared as `private`,
and getters and setters are provided to access and modify them.
The `setYear` method checks if the year is within a valid range before setting it,
and throws an exception if it is not.
The exception means that the program will stop running and display an error message if an invalid year is passed to the `setYear` method.

Here is how you can use getters and setters:

```java
Car myCar = new Car();
myCar.setMake("Toyota");
myCar.setModel("Corolla");
myCar.setYear(2020);
```

Sometimes you may see getters and setters referred to as "accessor" and "mutator" methods, respectively.
In addition, some classes only have getters and no setters,
which means that the fields are read-only and cannot be modified after the object is created,
except by methods within the class.

## Static Fields and Methods

Static fields and methods belong to the class itself, rather than to individual objects.
They are shared by all instances of the class.
They are accessed using the class name, rather than an object reference.

Here is an example of a class with static fields.

```java
class Car {
    public static final double MILES_PER_GALLON = 30.0;
}
```

In this example, the `MILES_PER_GALLON` field is declared as `static`,
which means that it is shared by all instances of the `Car` class.
It is also declared as `final`, which means that it is a constant and cannot be changed after it is initialized.

To use static methods or fields, you can access them using the class name:

```java
double mpg = Car.MILES_PER_GALLON;
double root2 = Math.sqrt(2.0); 
```

`Math` is a class in Java that contains static methods for mathematical operations,
such as `sqrt` for calculating the square root used in the example above.

Notice how we do not need to create an object of the `Math` class to use its static methods,
or of the `Car` class to access its static field.