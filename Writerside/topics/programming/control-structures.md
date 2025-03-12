# Control Structures

Control structures are used to control the flow of a program. 
They are used to execute code based on certain conditions. 
In this chapter, we will discuss conditional statements and loops in Java.

## Conditional Statements

Conditional statements are used to execute code based on certain conditions.
In Java, the conditional statements are `if`, `else if`, and `else`.

### `if` Statement

The `if` statement is used to execute a block of code if a condition is `true`.
If the condition is `false`, the code block is skipped.

You might remember that a boolean is a data type that can have one of two values: `true` or `false`.
In Java, you can use a boolean expression as the condition in an `if` statement,
so you don't need to explicitly set the condition to a variable first.

Here is an example of an `if` statement:

```java
public class Main {
    public static void main(String[] args) {
        int x = 10;

        if (x > 0) { //this is true, so the code block will be executed
            System.out.println("x is positive");
        }
    }
}
```

### `else` Statement

The `else` statement is used to execute a block of code if the condition in the `if` statement is `false`.

Here is an example of an `if` statement with an `else` statement:

```java
public class Main {
    public static void main(String[] args) {
        int x = -10;

        if (x > 0) { //this is not true, so the code block will be skipped
            System.out.println("x is positive");
        } else { //this will be executed instead
            System.out.println("x is negative");
        }
    }
}
```

### `else if` Statement

The `else if` statement is used to check multiple conditions.
It is used after an `if` statement and before an `else` statement.

Here is an example of an `if` statement with an `else if` statement:

```java
public class Main {
    public static void main(String[] args) {
        int x = 0;

        if (x > 0) { //this is not true, so the code block will be skipped
            System.out.println("x is positive");
        } else if (x < 0) { //this is not true either, so the code block will be skipped
            System.out.println("x is negative");
        } else { //this will be executed instead
            System.out.println("x is zero");
        }
    }
}
```

Note that the `else if` statement is optional, and you can have multiple `else if` statements in a row.
In addition, `else if` is different from simply using multiple `if` statements in a row,
because `else if` will only execute the code block for the first `true` condition it finds.
while multiple `if` statements will execute the code block for each `true` condition.

Here is an example of using multiple `if` statements:

```java
public class Main {
    public static void main(String[] args) {
        int x = 1;

        if (x > 0) { //this is true, so the code block will be executed
            System.out.println("x is positive");
        } if (x < 0) { //this is not true, so the code block will not be executed
            System.out.println("x is negative");
        } if (x == 0) { //this is not true, so the code block will be skipped
            System.out.println("x is zero");
        } if (x != 0) { //this is also true, so the code block will be executed; if we used else if, this code block would not be executed, as a previous condition was true
            System.out.println("x is not zero");
        }
    }
}
```

## Loops

Loops are used to execute a block of code multiple times.
In Java, there are four main types of loops: `for`, `for-each`, `while`, and `do-while`.

### `for` Loop

The `for` loop is used to execute a block of code a specified number of times.

Here is an example of a `for` loop that prints the numbers from 1 to 5:

```java
public class Main {
    public static void main(String[] args) {
        for (int i = 1; i <= 5; i++) {
            System.out.println(i);
        }
    }
}
```

As you can see, the `for` loop has three parts:
- The initialization part (`int i = 1`) is executed once before the loop starts.
- The condition part (`i <= 5`) is evaluated before each iteration of the loop. If it is `true`, the loop continues; if it is `false`, the loop ends.
- The update part (`i++`) is executed after each iteration of the loop.

The condition part can be any boolean expression, and the update part can be any valid Java statement.
Another example of a `for` loop is shown below:

```java
public class Main {
    public static void main(String[] args) {
        for (int i = 10; i >= 1; i--) {
            System.out.println(i); //prints the numbers from 10 to 1
        }
    }
}
```

### `for-each` Loop

The `for-each` loop is used to iterate over an array or a collection, which we will discuss in the [](collections.md)
chapter.
It is sometimes called an "enhanced for loop" because it simplifies the process of iterating over a collection.

Here is an example of a `for-each` loop that prints the elements of an array:

```java
public class Main {
    public static void main(String[] args) {
        int[] numbers = {1, 2, 3, 4, 5};

        for (int number : numbers) {
            System.out.println(number);
        }
    }
}
```

This is equivalent to the following `for` loop:

```java
public class Main {
    public static void main(String[] args) {
        int[] numbers = {1, 2, 3, 4, 5};

        for (int i = 0; i < numbers.length; i++) {
            System.out.println(numbers[i]);
        }
    }
}
```

### `while` Loop

The `while` loop is used to execute a block of code as long as a condition is `true`.

Here is an example of a `while` loop that prints the numbers from 1 to 5:

```java
public class Main {
    public static void main(String[] args) {
        int i = 1;

        while (i <= 5) {
            System.out.println(i);
            i++;
        }
    }
}
```

As you can see, the `while` loop has only one part: the condition part.
The condition part can be any boolean expression.

Most `for` loops can be rewritten as `while` loops, and vice versa.

### `do-while` Loop

The `do-while` loop is similar to the `while` loop, but the condition is instead evaluated *after* the block of code is executed.

Here is an example of a `do-while` loop that prints the numbers from 1 to 5:

```java
public class Main {
    public static void main(String[] args) {
        int i = 1;

        do {
            System.out.println(i);
            i++;
        } while (i <= 5);
    }
}
```