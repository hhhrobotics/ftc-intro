# Functions and Methods

Functions are a way to group code together and reuse it. 
In Java, functions can only be defined inside classes,'
and are called methods.
They are defined by specifying the return type, the name, and the parameters.

Here is an example of a method that takes two integers as parameters and returns their sum:

```java
class Math {
    public static int add(int a, int b) {
        return a + b;
    }
}
```

The `class` and `static` keywords are explained in [](classes-objects.md).

The `add` method takes two `int` parameters `a` and `b`, and returns their sum.

Here is how you can call the `add` method in Java:

```java
public class Main {
    public static void main(String[] args) {
        int sum = Math.add(3, 5);
        System.out.println(sum); // Output: 8
    }
}
```

Some examples of methods are featured in the [classes and objects](classes-objects.md) section.

## Method Overloading

Method overloading is a feature that allows a class to have more than one method with the same name,
but different signatures (number or type of parameters).

Here is an example of method overloading:

```java
class Math {
    public static int add(int a, int b) {
        return a + b;
    }

    public static double add(double a, double b) {
        return a + b;
    }
}
```

In this example, the `Math` class has two `add` methods:
- One that takes two `int` parameters and returns an `int`.
- One that takes two `double` parameters and returns a `double`.

Java determines which method to call based on the number and types of arguments passed to it.

Here is how you can call the overloaded `add` methods in Java:

```java
public class Main {
    public static void main(String[] args) {
        int sum1 = Math.add(3, 5);
        double sum2 = Math.add(3.5, 5.5);
        System.out.println(sum1); // Output: 8
        System.out.println(sum2); // Output: 9.0
    }
}
```

## Varargs (Variable Arguments)

Varargs (variable arguments) is a feature that allows a method to accept a variable number of arguments.
In Java, varargs are specified by using an ellipsis (`...`) after the parameter type.
The varargs parameter must be the last parameter in the method signature,
and it is treated as an array inside the method.
Arrays are explained in the [](collections.md) section.

Here is an example of a method that uses varargs to calculate the sum of multiple integers:

```java
class Math {
    public static int sum(int... numbers) {
        int sum = 0;
        for (int number : numbers) {
            sum += number;
        }
        return sum;
    }
}
```

