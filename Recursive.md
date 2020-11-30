# _Bobby's Site_ ![Icon](PageIcon.png)

[Home](README.md) | [About me](About.md) | [Turtle House](House.md) | [Recursive Turtle](Recursive.md) | [Random Number Reader/Writer](Numbers.md)

## Recursive Turtle _(1040)_

![Python Icon](http://www.pngall.com/wp-content/uploads/2016/05/Python-Logo-PNG-Image.png)
###### [Image Source](http://www.pngall.com/)

Here is the code from my python recursive turtle (square) program:

```
from turtle import Turtle
import random

firstrun = True

def getcolor(number):
    if(number == 1):
        return "red"
    elif(number == 2):
        return "green"
    else:
        return "blue"

def recursive_square(turtle, fwd, finalfwd, space):
    global firstrun
    if(firstrun): # set position
        turtle.penup()
        turtle.goto(-250,-250)
        turtle.pendown()
        firstrun = False
    # draw square
    turtle.color(getcolor(random.randint(1,3)))
    turtle.forward(fwd)
    turtle.left(90)
    turtle.color(getcolor(random.randint(1,3)))
    turtle.forward(fwd-space)
    turtle.left(90)
    turtle.color(getcolor(random.randint(1,3)))
    turtle.forward(fwd-space)
    turtle.left(90)
    turtle.color(getcolor(random.randint(1,3)))
    turtle.forward(finalfwd)
    turtle.left(90)
    if(fwd > 50):
        recursive_square(turtle, fwd-50, finalfwd-50, space) # recursive
    else: # finish final square
        turtle.right(90)
        turtle.color(getcolor(random.randint(1,3)))
        turtle.forward(35)

def main():
    bob = Turtle()
    bob.speed(10)
    recursive_square(bob, 500, 450, 20)

# run
main()
```
