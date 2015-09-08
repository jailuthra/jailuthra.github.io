---
layout: post
title: "Modifying the for-loop variable in python"
tags: [python]
---
{% include JB/setup %}

This is a short article demonstrating how changing the for loop variable can affect the elements of the list we iterate upon through the for loop, and how it's connected with mutability of the data type of the elements of the list

For those coming from C/C++ background, [this article](http://robertheaton.com/2014/02/09/pythons-pass-by-object-reference-as-explained-by-philip-k-dick/) is really helpful in understanding the difference on how python passes variables (by-reference, by-value, or something else) between functions, loops etc.


```python
a = 2
print(a)
```

    2



```python
b = a
print(b)
```

    2



```python
b = 3
print(b)
print(a)
```

    3
    2


NOTE: when you changed b, it didn't affect a


```python
a = [1,2,3,4,5]
print(a)
```

    [1, 2, 3, 4, 5]



```python
b = a
print(b)
```

    [1, 2, 3, 4, 5]



```python
b.append(6)
print(b)
print(a)
```

    [1, 2, 3, 4, 5, 6]
    [1, 2, 3, 4, 5, 6]


NOTE: appending 6 to b, changed the original list a as well

this happens because lists are mutable types, 
so when you do b = a, and a is a list, then python points the b variable to the chunk of memory where a was pointing,
but your changes on b reflect on a, because when you work on lists anything you do changes the data at the memory location your variable is pointing!

whereas, in integers, when you do a = 2, then a = a + 1, it makes a new memory location holding the new value a + 1 (ie 3),
and points a there. Python does not change the chunk of memory holding 2, which still sits at its old location.

similarly in the prev example, when we do b = a, we tell b to point to the chunk of memory a also points to (which holds the int literal 2),  
but when we do b = 3, we create a new chunk of memory, holding the literal 3, and tell b to point there  
this does not affect the value of the previous chunk (which held 2), which is still accessible using the variable a.

Now in for loops also, when you create a variable for the loop what python does is,


```python
l = [1,2,3,4,5]
for i in l:
    i = i+2
print(l)
```

    [1, 2, 3, 4, 5]


at every step, it will do: i = l[0], i = l[1] and so on
now l[0] and l[1] are ints so when you change i, you don't affect l[0], as integers are immutable
but if l[0] was a list, then you will change it by changing i, like shown in the following example


```python
l = [[1,2],[3,4]]
for i in l:
    i.append(len(i)+1)
print(l)
```

    [[1, 2, 3], [3, 4, 3]]


As you can see, you were able to change the elements of the lists, because the elements itself were lists, which are mutable!

What the for loop did was, it assigned i = l[0], then did i.append(len(i)+1), now as both i and l[0] point to the same chunk of memory (holding the list), and you mutated that chunk of memory by appending to the list, you changed the values of both *i* and the first element of list *l[0]*

Google about mutability in python to learn more :)

**tldr:** 

You can't change the integer literal a chunk of memory holds, so everytime you think you're changing an integer variable in python, you're creating a new chunk of memory and pointing your variable there. This is **Immutability**

Whereas when you change an element of a list, or append to it, you actually change the data itself the chunk of memory your list variable points to is holding, thus all the different variables that point to that location change. This is **Mutability**
