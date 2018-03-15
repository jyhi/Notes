# Creating Java Classes

- Modularity
- Information hiding
- Code reuse

## Classes vs. Objects

- A **class** is a programmer-defined **type**
  - _Template_ defined for later object creation
- A value of a class type is called an **object** (or **instance**) of it

## Class Definition in UML

|       | Fields / Methods |
| ----- | ---------------- |
| **+** | Public           |
| **-** | Private          |
| **#** | Protected        |

## The `new` Operator

Used to **create an object**.

```java
ClassName classVar = new ClassName();
```

## Instance Variables

```
[<modifiers>] type <fields_name> [=default_value]
```

Instance variables not initialized explicitly will be assigned a default value.

## Methods

```
[<modifiers>] <return_type> <name>([argument_list]) {
  [<statement>]
}
```

Methods are invoked using **the name of the object** which has the method:

```java
person1.getName();
person1.setAge(25);
```

## The `this` Keyword

`this` means the name for the calling object.

When parameter names and field names are not the same, then `this` can be omitted.

## Local Variables

A variable declared **within a method definition** is called a local variable.

## Global Variables

Java **does not have global variables**.

## Constructor

A **constructor** is a special kind of method that is designed to initialize the instance the instance variables for a new object:

```java
public ClassName(Parameters param) { code }
```

- Called by the `new` keyword
  - which is **the only valid way** to call it
- A constructor **must** have the **same** name as the class name
- A constructor has **no type returned** (not even `void`)
- Constructors are often _overloaded_
- If no constructors are given, a **default constructor w/o argument** is created by Java
  - If there is any, the default one won't be provided
