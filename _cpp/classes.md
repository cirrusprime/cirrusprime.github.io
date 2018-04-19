---
layout: page
---
Classes are initialised with the use of **constructors**.  Constructors must be named the same as the class name itself.

Objects of certain classes are destroyed (because they've gone out of scope, or have been `delete`d) using **destructors**, which are named the same as the class (and constructor), but prefixed with a tilde, `~`; it takes no arguments and returns no values.  They are used for releasing resources: closing files, freeing up memory, and so on.  They are not obligatory, however.

```c++
class ClassName
{
    public:
        // Constructor
        ClassName()
        {
            // Do stuff
        }
        // Destructor
        ~ClassName()
        {
            // Do other stuff
        }
}
```

## Class members

These are variables (known as "members") and functions (known as "member functions") specific to the class and its objects, which are defined to have different scopes, as given by their respective **access specifiers**.

### Access specifiers

These are the keywords `public`, `private`, and `protected`, followed by a colon, within the class definition.

#### Public class members

These can be accessed from everywhere outside the class within which they are defined.

#### Private class members

These can only be accessed from within the class defining them, but public member functions can be used to access the private ones.  It is the default.

## Example

```c++
class ClassName() {
    public:
        int publicInt;
        int publicFunction(string privateName) {
            return privateName;
        }
    private:
        string name;
}
```

## Good practice

* Define your classes in separate files, with the `classname.h` header file containing the actual class and method declarations (consider it the "what" file, as it declares what the class and its stuff will do), and the `classname.cpp` source file containing the actual methods' code, etc (consider it the "how" file, as it defines how the class and its stuff will do what it does).

## Definitions

When you create your methods and constructors and things in the *source* file, you must `#include` the *header* file first, and use the double-colon `::` (known as the **scope resolution operator**) to define the class's member functions (which have been declared in the header file).

For example, the *header* file, `MyClass.h`, could look like this:
```c++
#ifndef MYCLASS_H
#define MYCLASS_H

class MyClass
{
  public:
    MyClass();
  protected:
  private:
};

#endif // MYCLASS_H
```
and the *source* file, `MyClass.cpp`, could look like this:
```c++
#include "MyClass.h"

MyClass::MyClass()
{
   // Constructor code
}

MyClass::~MyClass()
{
    // Destructor code
}
```

Note that `#ifndef` in the source file means "if not defined"; `#define`, naturally, means "define the MyClass header file if it has not been defined already", and `#endif` naturally ends the condition.  This is necessary to prevent duplication of the definition, in the cases where the same header file is included in multiple source files.

## "Regular" member functions

These, unlike the constructor and destructor functions, must be declared (in the header file) and defined (in the source file) by their return type (`int`, `void`, etc).

### Object selection operator (`.`)

You can access a member (function) on an *instance* of a class using the dot operator, `.`.

## Members and pointers

These are accessed using pointers:

```c++
MyClass obj;
MyClass *ptr = &obj;
```

### Pointer selection operator (`->`)

The **arrow selection operator**, `->`, is used to access the member(s) (function(s)) on a *pointer* to an instance of a class.  If you're not dealing with pointers, and instead straight objects, then you'd use the dot operator, `.`.

```c++
MyClass obj;
MyClass *ptr = &obj;
ptr->myPrint();
```
