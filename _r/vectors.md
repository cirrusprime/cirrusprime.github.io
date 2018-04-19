---
layout: page
title: Vectors
---
Vectors in R are effectively lists in e.g. Python; one-dimensional arrays that hold data of various types.

## Creation

Using `c()` (combine) function, with comma-separated elements.

## Naming

If you need to add headers to your vector, use the `names()` function:

```r
my_vector <- c("Ross", "McFluff")
names(my_vector) <- c("First Name", "Last Name")
```

## Summing

The sum of two vectors, as realised by the `+` operator, is element-wise.

The `sum()` function sums across elements within a vector, so if you're wanting a single value from amalgamating your vector's elements, you need to use `sum()` rather than `+`.

## Selections and slicing

Grab a single element from a vector using its index in square brackets, as in Python, C(++), and most everything else!  **Note:** indexing starts at 1, rather than zero (as is the case for most).

Grab a subset of elements using one of the following:

* `vector_name[c(x, y, z)]`, where `x`, `y`, and `z` are the indices you want
* `vector_name[x:z]`, where `x` and `z` are the first and last indices you want *in a consecutive range of indices*, inclusive; **note:** the range is inclusive on *both ends* (unlike Python, for example, where `list[x:z]` would only be inclusive of `x-1`, and not of `z-1` - remember that indices in Python start at zero rather than 1!)
* `vector_name[c("Header Name", "Next Header Name")]`, if you have assigned headers to your vector using the `names()` function; use `"Header Name"` on its own if you want a single index though!

## Comparison operators

As is the case in most languages I've come across so far, the comparison operators for R are much the same as you'd expect:

* `>`: greater than
* `<`: less than
* `>=`: greater than or equal to
* `<=`: less than or equal to
* `==`: equal to
* `!=`: not equal to

You can use these on vectors, and the comparison will be applied to each element in turn, outputting a vector of booleans (a "logical vector").

If you were to pass a logical vector into the square brackets, R Knows What To Do.
