https://class.coursera.org/interactivepython2-007

###Mouse Interaction

Top three excuses for losing a video game:
- I lagged
- My Mom distracted me
- I got hacked

Code example: http://www.codeskulptor.org/#examples-mouse_input.py  

In CodeSkulptor:  
- Docs
- Control Objects
- Mouse button clicks

```
def mouse_clickhandler(position)    # position is a tuple of two integers
  pass

frame.set_mouseclick_handler(mouseclick_handler)
```

###List Methods

myList = [...]  

4 **in** myList  
myList.**index**(\<value\>) = index for number \<value\> in the myList  
myList .**append**(\<value\>)  adds \<value\> to the list  
myList.**pop**(\<index\>)  deletes the \<index\> entry in myList  

Code example: http://www.codeskulptor.org/#examples-list_methods.py  

###Iteration
```
for \<variable\> in \<list\>:
```
Code example: http://www.codeskulptor.org/#examples-list_selection.py  

Code example: http://www.codeskulptor.org/#examples-list_removal.py  

**NEVER REMOVE ITEMS FROM A LIST WHILE ITERATING OVER THE LIST**  

Code example: http://www.codeskulptor.org/#examples-iteration.py  

###Dictionaries

list[\<key\>] = \<value\>  
list = \{\<key\>:\<value\>, ...\}  

Code example: http://www.codeskulptor.org/#examples-dictionaries.py  

###Images
```
im = simplegui.load_image(URL)
canvas.draw_image(im, image.center, image.size, canvas.center, canvas.size)
```

Code example: http://www.codeskulptor.org/#examples-images.py  


