# Inheritance

Inheritance is the process by which a new class is created from another class.

- The original class is called **superclass**, **base class** or **parent class**
- The new class is called **subclass**, **derived class** or **child class**
  - A subclass automatically has **all non-private members** of the superclass, while can have additional members

```java
class Bar extends Foo {
  // new members
}
```

## Parent Class And Child Class

**Java does not allow multiple inheritance!**

- The first parent class is called **ancestor class**
- The last child class is called **descendent class**

## Overriding A Method Definition

- Method overriding is achieved when a subclass overrides (hides) **non-static methods** defined in the superclass with its own methods
  - The new method definition must have the **same** method signature and return type
  - The new method definition **cannot narrow the accessibility**, but widen it

```java
class Foo {
  // members

  protected String getLorem() {
    return "Lorem ipsum dolor sit amet";
  }
}

class Bar extends Foo {
  // members

  @Override // NOTE: Capital 'O' is required
  public String getLorem() {
    return "The quick brown fox jumps over the lazy dog";
  }
}
```

## The `super` Keyword

... which points to the parent class.

```java
class Bar extends Foo {
  // members

  public String getFooLorem() {
    return super.getLorem();
  }
}
```

## The `super()` Constructor

- **Constructor of the superclass**
  - **`super()` must be the _first_ statement of the constructor (if there is)**
- Every constructor automatically calls its superclass constructor
  - Java implicitly add a `super()` call in each constructor that does not explicitly call `super()` as its first statememt
- _If a class only defines non-default constructors, and its subclasses does not include an explicit `super()` call, this will be flagged as a compile-time error._

```java
class Foo {
  private String str;

  public Foo() {
    this.str = "Lorem ipsum dolor sit amet";
  }

  public Foo(String s) {
    this.str = s;
  }
}

class Bar extends Foo {
  private int nice = 0;

  public Bar() {} // This automatically calls Foo() in class Foo

  public Bar(String s, int nice) {
    // Calling Foo(String s) from class Foo
    // If not, Foo() in class Foo is automatically called
    super(s);
    this.nice = nice;
  }
}
```

## The `this()` Constructor

- **Constructor of the current class**
- Used to call _another constructor_ in the same class
  - The same restrictions as `super()` apply

```java
class Foo {
  private String str;

  public Foo() {
    this.str = "Lorem ipsum dolor sit amet";
  }

  public Foo(String s) {
    this.str = s;
  }
}

class Bar extends Foo {
  private int nice = 0;

  public Bar(String s, int nice) {
    super(s);
    this.nice = nice;
  }

  public Bar(String s) {
    this(s, -20); // This calls Bar(String s, int nice)
  }
}
```
