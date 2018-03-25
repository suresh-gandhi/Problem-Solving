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

