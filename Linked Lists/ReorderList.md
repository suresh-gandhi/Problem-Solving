## Problem Statement
We are given a singly linked list: ``` L0 -> L1 -> .... -> Ln-1 -> Ln. ```

We have to reorder the list to: ``` L0 -> Ln -> L1 -> Ln-1 -> ... ```

__Constraints__: We must do this in-place(no extra space) without altering the nodes' values.

## Sample Illustration

__Input__:

          List: head -> 1 -> 2 -> 3 -> 4 -> 5 -> 6 -> null
          
__Output__:

          ReorderedList: head -> 1 -> 6 -> 2 -> 5 -> 3 -> 4 -> null
        
## Intuition

### A closer look into the reordered list structure :eyes:
If we look carefully at the output we have to return(which is nothing but the reordered list), then we can observe that it is actually composed of two smaller lists with one of them sandwiched into another. The animation given below better illustrates this observation:

![intuition1](https://user-images.githubusercontent.com/22399995/37875640-e3cfe506-305f-11e8-97b7-e1c2905c9662.gif)

So basically the problem just reduces to sandwiching of the two lists which are 
* The first half of the original list
* The second half of the original list but in reversed order(See [this](https://www.summigandhi.com/) post on how to reverse a linked list)

We are progressing. Yohoo! :grinning:

### How to sandwich one list into another?
Sandwiching one list into another is just a bit of pointer manipulation. I think it is better understood through an animation rather than text. The animation is given below:

![intuition2](https://user-images.githubusercontent.com/22399995/37876932-53b43b7c-3071-11e8-8c69-79926ca7d7cc.gif)

In a nutshell -> 

1. Simply divide the original list into two parts i.e. __the first half part__ and __the second half part but reversed__.
2. Sandwich the second part into the first part.
3. Return the new list. :blush:

## Java Implementation
          





