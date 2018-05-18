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

## Constant class objects

They are defined the same way as constant in-built data types, `const ClassName varname;`. Note that all `const` objects *must* be initialised at the point of creation.

### Constant class function definitions

Defining constant class functions can be done by *appending* the `const` specifier to the end of the defining line:

```c++
class MyClass {
    public:
        void MyPrint() const;
};
```

in the header file, and

```c++
void MyClass::MyPrint() const {
    cout << "Hello" << endl;
}
```

in the source file. From this point onwards, it can be used the same way a constant builtin data type would be:

```c++
const MyClass obj;
obj.MyPrint();
```

These cannot be changed once defined as constant.

### Member initialisation lists in class constructors

When working with constant class members, you can’t initialise them within the constructors, as they are defined within the `private:` section, and so you need to use an initialisation list, which starts with a colon, but *does not* end with a semicolon, and looks like this:

```c++
class MyClass {
    public:
        // Constructor
        MyClass(int a, int b)
        // Initialisation list
        : regVar(a), constVar(b) {
        }
    private:
        int regVar;
        const int constVar;
};
```

Although you should really put the initialisation list in the source file’s definition of the constructor, rather than in the header file.

It is **essential** to use initialisation lists for constant variables, and is generally useful to use them for non-constant variables as well.

## Compositions

Classes can be made up of objects of other classes, when the parent class and subclass have a **“has-a” relationship**, in that a member of the parent class *has a* member of the subclass.

## Friend functions

You can declare an external function a `friend` of a class, which allows that function to have access to the private (and public, but that’s kind of given anyway) members of that class. But you have to pass objects to that function by reference, using `&`.

```c++
class MyClass {
    public:
        MyClass() {
            regVar = 0;
        }
    private:
        int regVar;

        friend void someFunc(MyClass &obj);
};

void someFunc(MyClass &obj) {
    obj.regVar = 42;
    cout << obj.regVar;
}
```

You can also define **friend classes**, which has access to the private members of another class.

## The `this` pointer

Every object in C++ has an intrinsic pointer to its own address, the `this` pointer. Inside a member function `this` may be used to refer to the invoking object. Friend functions don’t have a `this` pointer, as they are not members of a class. Useful for function overloading.

## Operator overloading

Overloading means to **redefine** a pre-defined variable or keyword, so as to use it in a different way. For example, `+` and `-` operators can be overloaded (redefined).

They are defined within class definitions via the use of `operator` followed by the operator to be overloaded, *without a space in between the two*: `operator+` will define the overloading of the `+` operator.

For example:

```c++
class MyClass {
    public:
        int var;
        MyClass() {}
        MyClass(int a)
        : var(a) { }

        MyClass operator+(MyClass &obj) {
            MyClass res;
            res.var= this->var+obj.var;
            return res;
        }
};
```

The above overloads the `+` operator within the `MyClass` class to enable `MyClass` objects to be added together in much the same way as integers would be.
