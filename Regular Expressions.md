#Regular Expressions
https://docs.python.org/2/howto/regex.html  


'''
^         matches beginning of line
$         matches end of line
.         matches any character
\s        matches whote space (small-s)
\S        matches non-white space (capital-S)
*         repeats a character zero or more times
*?        repeats a character zero or more times (non-greedy)
+?        repeats a character one or more times (non-greedy)
[aeiou]   matches single character in a listed set
[^XYZ]    matches a single character NOT in a listed set
[a-z0-9]  set of characters can include a range
(         where string extraction starts
)         where string extraction ends
'''

To use, import regular expression library:
'''
import re
'''

Examples:
'''
import re

re.search('^From:', line)   true is search for "From:" at beginning of line

^X.*:                       beginning of line(^) has X, any number of characters (.*), ends with colon(:)
X-this is a test    #=> false
X-this is a test:   #=> true
X-this is: a test   #=> true

^X-.\S+:                      starts with X-(^X-), least 1 nonwhite space(\S), then colon (:)
X-this_is_a_test:   #=> true
X-this is a test:   #=> false
'''

re.search(<regexp>, <text>)   is there a match, returns true or false  
re.findall(<regexp, <text>)   return a list of matches, empty list if not found  

###Greedy Matching  
Return longest string:
'''
x = "From: this is: a test"
'^F.+:'               #=> greedy, "From: this is:"
'^F.+?:'              #=> nongreedy, "From:"

x = "From: me@example.com"
'^From: (\S+@\S+)'    #=> return the part in between (...), "me@example.com"
'^From: .*@([^ ]+)'   #=> '[^ ]' is not a blank, example.com
'^From: .*@(\S+)'     #=> example.com
'''

###Escape special characters
'''
\$      the dollar sign
\^      the caret
'''

