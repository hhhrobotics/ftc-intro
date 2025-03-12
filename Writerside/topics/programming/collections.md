# Collections

A collection is a group of objects that can be treated as a single unit. 
In Java, collections are used to store, retrieve, manipulate, and communicate aggregate data.

## Arrays

An array is a fixed-size collection of elements of the same type.
The elements of an array can be accessed by their index, the position of the element in the array.
In Java, arrays can be of any type, including primitive types and reference (object) types.

Here is an example of creating an array of integers:

```java
public class Main {
    public static void main(String[] args) {
        int[] numbers = new int[5]; //creates an array of 5 integers
        numbers[0] = 1; //note that the index starts at 0
        numbers[1] = 2;
        numbers[2] = 3;
        numbers[3] = 4;
        numbers[4] = 5;
    }
}
```

0-based indexing means that the first element of the array is at index 0, the second element is at index 1, and so on.
Most programming languages use 0-based indexing for collections, including arrays.

Arrays have a fixed size, which means that once an array is created, its size cannot be changed.
In the example above, the array `numbers` has a size of 5, and you cannot add or remove elements from it.
This means you would not be able to say `numbers[5] = 6;` because the array only has indices 0-4.

You can also initialize an array with values:

```java
public class Main {
    public static void main(String[] args) {
        int[] numbers = {1, 2, 3, 4, 5}; //creates an array of integers with values
    }
}
```

```admonish warning
Arrays are not `Collection` objects in Java.

This means do not have any methods, 
only the length property to get the size of the array,
and the index operator `[]` to access elements by index.
This means that arrays are not as flexible as other collection types in Java.
```

## Lists

> You must import the `List` interface,
> or any other collection interface or class you want to use,
> such as `ArrayList` or `LinkedList`,
> from the `java.util` package.
> 
> Most IDEs will automatically import the necessary classes for you when you use them,
> including Android Studio, which is used in FTC.

A list is a dynamic collection of elements that can grow or shrink in size.
In Java, the `List` interface is a common way to work with lists. 
Some common implementations of the `List` interface are `ArrayList` and `LinkedList`.

When creating a list, you must specify the type of elements it will contain,
using angle brackets (`<>`) and the element type.
For example, `List<Integer>` creates a list of integers.

The type of the list must be a reference type, not a primitive type,
so you must use the wrapper classes for primitive types (e.g., `Integer` for `int`, `Double` for `double`).

If the list will contain elements of different types, you can use the `List<Object>` type,
as `Object` is the superclass of all classes in Java.
Similarly, if all elements extend a common superclass or implement a common interface,
you can use that superclass or interface as the type of the list.
However, when you retrieve elements from the list, you can only use methods defined by the superclass or interface,
unless you cast the elements to their actual type.

Here is an example of creating an `ArrayList` of integers:

```java
import java.util.ArrayList;

public class Main {
    public static void main(String[] args) {
        ArrayList<Integer> numbers = new ArrayList<>(); //creates an ArrayList of integers
        numbers.add(1); //adds an element to the ArrayList
        numbers.add(2);
        numbers.add(3);
        numbers.add(4);
        numbers.add(5);
    }
}
```

The `ArrayList` class provides methods to add, remove, and access elements in the list.
You can add elements to the end of the list using the `add` method, as shown in the example above.
`ArrayList` automatically grows in size as elements are added to it, 
unlike arrays, which have a fixed size.

Another type of list is the `LinkedList`, which is a doubly linked list implementation of the `List` interface.
`LinkedList` provides methods to add, remove, and access elements in the list, similar to `ArrayList`,
but the underlying data structure is different.
This guide will not cover the implementation details of either class,
but many resources are available online if you are interested in learning more. 

Another way to create a `List` with initial values is to use the `Arrays.asList` method,
which is a static method in the `Arrays` class that creates a `List` from an array:

```java
import java.util.List;
import java.util.Arrays;

public class Main {
    public static void main(String[] args) {
        List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5); //creates a List of integers with values
    }
}
```

The `Arrays.asList` method creates an immutable `List`, which means you cannot add or remove elements from it,
unlike `ArrayList`, which is mutable.

## List Methods

The `List` interface provides many methods to work with lists.
Here are some common methods:
- `add`: Adds an element to the end of the list.
- `get`: Retrieves an element at a specified index.
- `set`: Replaces an element at a specified index.
- `remove`: Removes an element at a specified index.
- `size`: Returns the number of elements in the list.
- `contains`: Checks if the list contains a specified element.
- `indexOf`: Returns the index of the first occurrence of a specified element, or -1 if not found.
- `isEmpty`: Checks if the list is empty.
- `clear`: Removes all elements from the list.
- `addAll`: Adds all elements from another collection to the list.
- `sorted`: Sorts the list in natural order according to the `compareTo` method of the element type.

The `sorted` method requires the `List` element type to implement the `Comparable` interface,
which defines a natural ordering for the elements.
