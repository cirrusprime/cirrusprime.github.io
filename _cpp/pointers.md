---
layout: page
---
## Initialising Pointers

Initialising a pointer is done with an asterisk: `int *ptr;` will initialise a pointer, `ptr`, and specifies the data type **of the variable whose address it points to** is an integer.

## Assigning Values to Pointers

Typically, you provide a value to your given pointer by assigning it a **referenced** variable, using an ampersand: `ptr = &var;` will assign the **address in memory** of the existing variable, `var` (as a hexadecimal value), to your pointer, `ptr`.

**Note** that you don’t need to include the asterisk here, which is a point of confusion I’ll get to in a second, because its use in the initialisation is purely to indicate that a pointer is being made.

Now your pointer has a value - the memory address of your variable - you can refer to the value of that variable, **and not its memory address**, using the **dereference operator**. The aforementioned point of confusion comes in here, because the dereference operator is also given by an asterisk. Its usage is distinct from pointer-initialisation, which had been confusing the hell out of me until it was just clarified as Completely Different and Unrelated!

## Clearing Up (My Own) Confusion

Consider the dereference operator, `*`, as the **complement** to the reference operator, `&`. The dereference operator takes a memory address as input, and outputs the value stored in that address, whereas the reference operator takes a variable name as input, and outputs the memory address where that variable is stored.

Pointers can be used, once assigned, to manipulate variable values, just as if you were using the variable itself; consider them “aliases” to their respective variables. This was another point that left me stuck. *Why design something that aliases something else, when you could just use that something else in the sodding first place*, I thought. Well, up until now, I didn’t know much at all about how memory gets assigned when you run a program. And to be fair, I still don’t. But at least now I can distinguish between the stack, where the local variables in your program get assigned their memory addresses, and the heap, the as-yet-unused memory where any new variables get plopped at runtime, and where pointers come in really handy.

## Dynamic Memory Allocation

See, the heap memory allocation, happening at runtime, is initiated using `new`: `int *ptr2 = new int`, since `new` takes the data type following it, grabs the required memory for such a data type, and returns the address of said grabbed memory. Now, because you hadn’t got a variable predefined in your program to be used in such a way, the *only* way you can access this shiny new `int` is through `ptr2`. Remember, `ptr2` will give the memory address of the new `int`, whereas `*ptr2` will give (or allow you to assign) the new `int`’s value. This is **dynamic memory allocation** in action.

When you’re done using a dynamically-allocated memory address, simply do a `delete ptr2` and it’s gone, freeing up the memory for anything else that needs it next. The pointer itself, though, is stored on the stack, so that isn’t deleted. If you leave that pointer free, and not actually pointing to anything, that makes it a **dangling pointer**. If you declare a pointer and don’t use it until much later in the program, for similar reasons, it might be best to initialise it to `NULL` (a “null pointer”), so at least it’s pointing somewhere and not hovering ominously over your code, threatening to explode it all at any time…

While you can do similar things with any data type, including arrays, you need to note a different syntax for the deleting of the respective pointer, thus: `delete [] arrayptr;`.
