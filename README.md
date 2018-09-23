C++
===

- Constructor (Sequence of building)
- Destructor
- Memory management
- Size of objects
- Inheritance
- Move Constructor
- Avoid extra copying
- Signature and performatnce
- Operator functions

__Operator overloading using Member function__

```C++
class Increment {
    public: 
      int operator + (const int& a) {
          return a + 1;
      }
};

int main() {
    Animal a {};
    cout << a + 7 << endl;
    return 0;
}
```

- Operator overloading to add Custom Class + int.
- Should overload other common ones as well.
- When in doubt do what integers do.

__Operator overloading using Friend function__

```C++
class Increment {
  friend int operator + (int n, Increment a) {
      return n + 1;
  }
};

int main() {
    Increment i {};
    cout << 7 + i << endl;
    return 0;
}
```

- Use a friend in so that you can do int + increment. 
- Member method will only be able to do increment + int.

__Conversion Operator__


```C++
class Animal { 
  operator char* () {
      return "Hello World";
  }  
};

int main() {
    Animal a {};
    cout << a << endl;
    return 0;
}
```
- Above program will print hello world. As compiler knows how to convert Animal to character array.
- Better than overriding << and outputstream.

C#
===

__Value and Reference Types__

- Structs are value types. Live on Stack.
- Classes are reference types. Live in Heap.


__Operator Overloading__

```C#
class A {
  public static A operator + (A left, A right) { .... }
  public static int operator int (A a) { .... }
}
```
- Similar to C++
- Functions should be static
- Also has conversion operators

__Function overriding__

- Functions are not virtual by default.
- Virtual functions can be overriden. 
- New creates a new function of same name that has no relation with function of base class.
- Writing override in function signature is compulsory.

__Extension Methods__

```C#
public static class Extensions {
  public static int getLength(this String str) {
    return str.length();
  }
}
```

- Class must be public static.
- Function must also be static.
- Adds extra functionality over existing classes.
- Cannot access private members of class.

__Exceptions__

- Only unchecked exceptions, similar to RunTime exceptions in Java.

__Out and Ref keywords__
```C#
class Example {
  static void main(String[] args) {
    int V1 = 0; // Must be initialized 
    int V2;     // Optional

    Example1(ref V1);
    Example2(out V2);
  }

  static void Example1(ref int value) {
    value = 1;
  }
  static void Example2(out int value) {
    value = 2;
  }
}
```
- Ref must be initialized
- Out may not be initialized

- covariant & contravariant
- hiding
- using keyword
- Nullable
- Comparing interfaces
- Comparison IEquitable
- Explicit/IMplicit Interfaces

Java
====

__Inheritance with Contructors__

```java
public class Animal {
  String name;
  Animal(String name) { this.name = name; }
}

public class Lion {
  Lion(String name) { super(name); }
  public void roar() { // Roar }
}
```
- Call super first. Then do your own things.

__Object Instantiation__

```java
Animal a = new Lion("Simba");
Lion l = a;
// a.roar() // Not allowed.
l.roar();   // Allowed
```

__this keyword__
- Used to refer to current class.
- Can be used to call a different constructor of the same class.
- Can be used as function parameter to sent *this* object to a function.


__Interface ( cast to new reference types )__

```java
interface Runner { void run(); }
class Animal implements Runner {}
```
```java
class Main {
  static void run(Runner r) { r.run(); }
  public static void main(String[] args) {
    Animal a = new Animal();
    run(a);
  }
}
```
- Casting can be implicit (as shown above) or explicit.

__Exceptions__

- Checked Execptions
- Collection Hashing List
- throwing null pointer exception
- finally

Scala
=====

__Friend/Companion__

```scala
class Hello {
  def sayHello() {
    println("Hello World")
  }
}
object Hello {
  def sayHi() {
    println("I don't need an object")
  }
}
```
```scala
Hello h = new Hello()
h.sayHello()
Hello.sayHi()
```
- No static keyword in Scala.
- To add static methods to a class, use a class/object(singleton) pair of the same name.

__Option types__

```scala
def getOperation(str: String): Option[String] = {
  if(str == "+")
    return Some("Add");
  else
    return None
}
```

```scala
val operation: Option[String] = getOperation();
```

- Can now do `operation.isDefined()` or provide a default value or use pattern matching.

__Covariance and Contravariance__

http://blog.kamkor.me/Covariance-And-Contravariance-In-Scala/

Object Oriented Design
======================

__Where to put functions__

```C++
if (f needs to be virtual) 
{
  make f a member function of C;  
}
else if (f is operator>> or operator<<) 
{
  make f a non-member function;
  if (f needs access to non-public members of C)
  {
    make f a friend of C;
  }
} 
else if (f needs type conversions on its left-most argument) 
{
  make f a non-member function;
  if (f needs access to non-public members of C)
  {
    make f a friend of C;
  }
} 
else if (f can be implemented via the public interface)
{
  make f a non-member function;
}
else
{
  make f a member function of C;
}
```
