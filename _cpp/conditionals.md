---
layout: page
---
## `if`, `else if`, `else`



## `switch`

For use when the value of an expression is expected to take one of a specific set of integer values.

Syntax:

```c++
switch (grade) {
  case 9:
    std::cout << "Freshman\n";
    break;
  case 10:
    std::cout << "Sophomore\n";
    break;
  case 11:
    std::cout << "Junior\n";
    break;
  case 12:
    std::cout << "Senior\n";
    break;
  default:
    std::cout << "Invalid\n";
    break;
}
```

