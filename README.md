# Notes

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

- out/ref
- covariant & contravariant
- hiding
- using keyword
- Nullable
- override/new
- Comparing interfaces
- Comparison IEquitable
- Explicit/IMplicit Interfaces

Java

- Object instantiation
- this
- Interface ( cast to new reference types )
- Exceptions
- Checked Execptions
- Collection Hashing List
- throwing null pointer exception
- finally

Scala

- Friend/Companion
- Option types
- Generics

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
