#Installing Python
http://docs.python-guide.org/en/latest/starting/install/osx/  
http://docs.python.org/lib/built-in-funcs.html
**list of tutorials**: http://www.analyticsvidhya.com/learning-paths-data-science-business-analytics-business-intelligence-big-data/learning-path-data-science-python/?utm_content=buffer04902&utm_medium=social&utm_source=linkedin.com&utm_campaign=buffer  
**google python tutorial**: https://developers.google.com/edu/python/  

###Printing  
use of **%** in printing  
```
print "Let's not go to %s. 'Tis a silly %s." % (string_1, string_2)
```

###Text Input  
```
original = raw_input("Enter a word: ")
```

###While..else
```
While n < 10:
  if n == <condition>:
    ...
    break
  n += 1
else:
  <executes if above if condition never met>
```

###for...else
```
for i in <list>
  ...
  if i == <condition>:
    ...
    break
else:
  <executes if above if condition never met>
```
###in
```
if c in "aeiouAEIOU"
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
```
dictionary.items()
dictionary.keys()
dictionary.values()
```

###Lists
```
list = []
list = ["a", "b", "c", "d"]
list.remove("b")
list.pop(1)
list.remove(1)
del(list[1])
```
**zip** index several lists in parallel, stops at shortest list  
```
list_a = []
list_b = []

for a, b in zip(list_a, list_b):
  if a != b:
  
```
###Split into substrings
```
text = "Now is the time for all good men"
strings = text.split()      # individual strings
t = " ".join(strings)       # rejoin individual strings together
```

###List comprehension
```
evens_to_50 = [i for i in range(51) if i % 2 == 0]
```

###Slicing Lists  
for indexing a list use `list[<start>:<end>:<stride>]`  
`list[::-1]` reverses a list  

###lambdas
```
languages = ["HTML", "JavaScript", "Python", "Ruby"]
print filter(lambda x: x == "Python", languages)
```
###Bitwise  
Binary notation is **0b01** or **0b1**  
Binary shift right `var >> <n bits>` or `var << <n bits>`  
Binary negate `~`  
Binary XOR `^`  
Flip bits `0b101010 ^ 0b111111`  

###Classes
```
class Animal(object):
  health = "good"
  def __init__(self, name, age):
    self.name = name
    self.age = age
  def show_name(self):
    print self.name
    
panda = Animal("Peter", 4)
panda.show_name()     # => "Peter"
print panda.health    # => "good"
```

**overwriting inheritance (monkey patch)**  
```
class Employee(object):
    """Models real-life employees!"""
    def __init__(self, employee_name):
        self.employee_name = employee_name

    def calculate_wage(self, hours):    # original method
        self.hours = hours
        return hours * 20.00

class PartTimeEmployee(Employee):
    def calculate_wage(self, hours):    # overwrites Employee method
        self.hours = hours
        return hours * 12.00
        
    def full_time_wage(self, hours):
        return super(PartTimeEmployee, self).calculate_wage(hours)  # references the parent class method
        
r = Employee("Ralph")                 # initialize name in Employee
print r.calculate_wage(100)           #=> 2000
w = PartTimeEmployee("David")         # still initializes name in Employee
print w.calculate_wage(100)           #=> 1200

milton = PartTimeEmployee("Milton")   # example references super class
print milton.full_time_wage(10)       #=> 200
```

###__repr__(self)  
automatically prints  

```
class Point3D(object):
    def __init__(self, x, y, z):
        self.x = x
        self.y = y
        self.z = z
        
    def __repr__(self):
        return "(%d, %d, %d)" % (self.x, self.y, self.z)
        
my_point = Point3D(1, 2, 3)
print my_point      #=> (1, 2, 3)
```

###with..as  
Automatically closes the file, no need for .close()  
```
with open("text.txt", "r+") as my_file:
    my_file.write("Hello!")
if not(my_file.closed):   #=> already closed
    my_file.close()
print my_file.closed      #=> True
```
###Reading Files
```
fhand = open(<filename>, <access>)


count = 0
for line in fhand
  count = count + 1
print count

line.startswith("From:")

whole_file = fhand.read()
```
###Lists
List is a ttype of **collection**  
Lists are **mutable**  
```
list = []
list[n] is the nth element of a list
List index starts at 0

list = list()
list = []
list.append(...)
list1 + list2
x in list
list.sort()
list_of_words = string.split()
```

###Tuples
Are not mutable, can not be changed  
Use as temporary variables  
Mort efficient than **lists** since will not change  
Can sort a **list** of **tuples**
```
(1, 3, 2) < (2, 1, 4)  #=> true 1 < 2, then stops comparing
```
