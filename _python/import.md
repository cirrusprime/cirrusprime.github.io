---
layout: page
---
Typical commands used to import stuff:

```python
import math # Imports module in its entirety, and can be referenced by its name
import pandas as pd # Imports module in its entirety, but can be referenced by the given (shorter) name
from numpy import matplotlib.pyplot as plt # Imports only a specific subset of stuff from numpy, and that specific subset can be referenced by the given (shorter) name
```

You can also do `from module import *`, but this is generally a bad idea, so avoid wherever possible please!

Access stuff within an `import`ed module using the dot notation `.`.

Find out what stuff is included in a module using `dir(module)`, which returns a list of strings of all the properties and methods.  Note that it doesn't distinguish between variables and functions in the list.

Find out more information about new, mysterious kinds of stuff from the imported modules by using `type()`, `dir()`, and of course the trusty `help()`.
