# Variables and Types

Variables are used to store data in a program. 
They are like containers that hold data. 
The data stored in a variable can be changed during the execution of the program,
unless the variable is declared as a constant.

`System.out.println()` is a function built in to Java that prints its argument to the console.

## Declaring and Instantiating Variables

To declare a variable, you need to specify the type of the variable and a name for the variable.
Here is an example of declaring a variable of type `int`:

```java
public class Main {
    public static void main(String[] args) {
        int number;
        String word;
        boolean flag;
    }
}
```

To instantiate a variable, you need to assign a value to the variable.
Here is an example of instantiating a variable of type `int`:

```java
public class Main {
    public static void main(String[] args) {
        int number;
        number = 5;

        int anotherNumber = 10; // you can also declare and instantiate a variable in one line
        String word = "word";
        String sentence = "This is a sentence.";
        
        boolean flag = true;
    }
}
```

You can also declare and instantiate multiple variables in one line:

```java
public class Main {
    public static void main(String[] args) {
        int number1, number2, number3;
        number1 = 1;
        number2 = 2;
        number3 = 3;
    }
}
```

## Constants

A constant is a variable whose value cannot be changed once it has been assigned.
In Java, you can declare a constant using the `final` keyword.

Here is an example of declaring a constant:

```java
final int MAX_NUMBER = 100;
```

## Variable Types

Variables can be classified into different types based on the data they store.
Here are some basic variable types in programming:
- **int**: Stores integer numbers (e.g., -3, -2, -1, 0, 1, 2, 3, 4, 5)
- **double**: Stores decimal numbers (e.g., 1.0, 2.5, 3.14)
- **String**: Stores text (e.g., "Hello, World!")
- **boolean**: Stores true or false values

Types declared with a capital letter (e.g., `String`) are objects (explained in [](classes-objects.md)),
while types declared with a lowercase letter (e.g., `int`) are primitive types,
which are the basic data types provided by Java and do not have any methods.
Some classes are also provided by Java,
such as `String` and `ArrayList`.

### What is the difference between a primitive type and an object?

Primitive types are simple data types that are built into the Java language.
They are not objects and do not have methods.

Objects are instances of classes that can have methods and properties.
For example, `String` is a class in Java that represents a sequence of characters.
When you create a `String` variable, you are creating an object of the `String` class.

This distinction is important because objects can have methods and properties that you
can use to manipulate the data they store, while primitive types do not have these capabilities.
For example, you can call the `length()` method on a `String` object to get the length of the string,
but you cannot call any methods on an `int` variable because it is a primitive type.

Here is an example:

```java
String str = "Hello, World!";
int len = str.length();
```

