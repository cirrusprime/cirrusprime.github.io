---
layout: page
---
**Inheritance** is important for object-oriented programming.  This enables ("derived") classes to be defined which are "subsets" of other ("base") classes, thus making it easier to create self-contained, more manageable classes.

The first thought I had about the use of this for my current research area was to have an `atom` class, the objects of which can be contained within instances of a `molecule` class.  So the `molecule` class would contain as many objects of the `atom` class (with their own associated properties) as makes up the given molecule, with the additional properties contained within the molecule itself, such as interatomic forces, connections between said atoms, their positions in relation to the molecule's "container", and so on.