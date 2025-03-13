# Kotlin

> This page is adapted from the
> [corresponding Cookbook page](https://cookbook.dairy.foundation/misc/why_kotlin/why_kotlin.html)

Kotlin is a language with very high cross-compatability with Java, 
which means it can be used to write your FTC code.

FIRST provides official instructions for adding Kotlin to your project 
[here](https://ftc-docs.firstinspires.org/en/latest/programming_resources/shared/installing_kotlin/Installing-Kotlin.html).

Kotlin is a language that makes a very solid attempt at modernizing Java. 
It makes writing common Java patterns concise. 
Kotlin also makes it easy to write safer code that is less likely to have strange bugs 
or throw confusing NullPointerExceptions.

Kotlin is unlikely to be particularly useful to you 
if you are not using Object-Oriented aspects of Java already. 
If you are just writing [Linear]OpModes but are not writing your own classes, 
Kotlin is probably not for you. 
While Kotlin certainly does offer some nice features in this environment, 
the challenges that come with using Kotlin may also prove hard to overcome 
unless you are writing more complex and involved code. 
It is also advisable not to try to switch to Kotlin 
at the same time as learning more Object-Oriented skills.

Due to Kotlin's concise nature, 
it can sometimes prove difficult to read. 
Java likes to put everything out in the open and be very direct and specific, 
while Kotlin tends to imply much more.

This guide will cover some very basic comparisons between Kotlin and Java.

## Variables and Values

In Kotlin, variables are marked as either 
`var`, for properties that are both readable and writeable,
or `val`, for properties that can only be read 
(similarly to a `final` variable in Java).

In addition, Kotlin provides `get` and `set` functions 
for properties in classes, as opposed to Java,
which forces the user to write them.

Thus, the following two snippets are effectively equivalent:

<tabs group="vars-vals">
<tab title="Kotlin" group="vars-vals">
<code-block lang="kotlin">
class Variables {
        //var1 and var2 are readable and writeable
        var var1: Integer = 0 
        private var var2: String = "variable string" 
        //specifying the type of the variable is optional
        //if it is instantiated immediately,
        //as Kotlin can infer the type from what it is assigned to

        var1 = 4 //this works!
        //however, var1 = "4" will not compile,
        //as var1 is of type Integer

        //val1 and val2 are read-only
        val val1 = 0
        private val val2 = "value string"
        //val1 = 4 will not compile, because values are only readable
}
</code-block>
</tab>
<tab title="Java" group="vars-vals">
<code-block lang="java">
class Variables {
        //it is convention to make Java variables private 
        //and use getter and setter functions instead
        private int var1 = 0;
        private String var2 = "variable string";
        private final int val1 = 0;
        private final String val2 = "value string";
        //getter and setter functions
        public int getVar1() {
            return var1;
        }
        public void setVar1(int var1) {
            this.var1 = var1;
        }
        public String getVar2() {
            return var2;
        }
        public void setVar2(String string) {
            this.var2 = string;
        }
        //
        public int getVal1() {
            return val1;
        }
        public String getVal2() {
            return var2;
        }
}
</code-block>
</tab>
</tabs>

When you access a property in Kotlin, 
you automatically call the `get` and `set` functions,
even though you are using the field access syntax.

For example, the following two snippets are once more equivalent:

<tabs group="vars-vals-2">
<tab title="Kotlin" group="vars-vals-2">
<code-block lang="kotlin">
fun main {
    val example = Variables()
    println(example.var1)
    example.var1 = 4
    println(example.var1)
}
</code-block>
</tab>
<tab title="Java" group="vars-vals-2">
<code-block lang="java">
public static void main() {
    Variables example = new Variables();
    System.out.println(example.getVar1());
    example.setVar1(4);
    System.out.println(example.getVar1());
}
</code-block>
</tab>
</tabs>

As you can see, the Kotlin code is more concise,
despite the same thing occurring under the hood.

## Constructors and Class Properties

Kotlin allows you to instantiate your properties in a class' *primary constructor*.
The following blocks are equivalent once more:

<tabs group="constructors">
<tab title="Kotlin" group="constructors">
<code-block lang="kotlin">
class ConstructorParams (val val1: String, var var1: Int)
</code-block>
</tab>
<tab title="Java" group="constructors">
<code-block lang="java">
public class ConstructorParams {
    private final String val1;
    private int var1;

    public ConstructorParams(String val1, int var1) {
        this.val1 = val1;
        this.var1 = var1;
    }
    
    public int getVar1() {
        return var1;
    }
    
    public String getVal1() {
        return val1;
    }
    
    public void setVar1(int var1) {
        this.var1 = var1;
    }
}
</code-block>
</tab>
</tabs>

Kotlin also allows you to define custom 
getter and setter functions for your properties,
even though they are accessed like fields as described above.

Again, the examples below are equivalent.

<tabs group="vars-vals">
<tab title="Kotlin" group="vars-vals-2">
<code-block lang="kotlin">
class Square(side: Double) {
    var side = side
        set(value) {
            field = abs(value) 
            //can't have a negative side length!
        }

    val area: Double 
        get() = side * side 
        //even though area is a val,
        //if you change side, 
        //area changes, since it calls the get function
}
</code-block>
</tab>
<tab title="Java" group="vars-vals-2">
<code-block lang="java">
public class Square {
    private double side;

    public ConstructorParams(double side) {
        this.side = side;
    }
    
    public double getSide() {
        return side;
    }
    
    public void setSide(double side) {
        this.side = side;
    }
    
    public double getArea() {
        return side * side;
    }
}
</code-block>
</tab>
</tabs>

## More!

I could spend like 8921 whole pages on Kotlin, 
but instead I ask that if you're interested,
you read the Kotlin language website,
linked on [](Landing.topic)!