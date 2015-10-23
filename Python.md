###Printing  
use of **%**  
```
print "Let's not go to %s. 'Tis a silly %s." % (string_1, string_2)
```

###Text Input  
```
original = raw_input("Enter a word: ")
```

###Import Modules
```
"""Standard import method"""
import math
math.sqrt(n)

"""Import without having to specify math. """
from math import sqrt
sqrt(n)

from math import *
sqrt(n)
```

```
import math            # Imports the math module
everything = dir(math) # Sets everything to a list of things from math
print everything       # Prints 'em all!
```

###Dictionaries  
Python dictionaries are like hash tables  
```
dict = {}                 # initialize empty dictionary
dict['panda'] = "bear"    # set an entry value
del dict['panda']         # delete an entry
```

###Lists
```
list = []
list = ["a", "b", "c", "d"]
list.remove("b")
list.pop(1)
list.remove(1)
del(list[1])
