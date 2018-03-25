## Problem Statement
We are given a singly linked list: ``` L0 -> L1 -> .... -> Ln-1 -> Ln. ```

We have to reorder the list to: ``` L0 -> Ln -> L1 -> Ln-1 -> ... ```

__Constraints__: We must do this in-place(no extra space) without altering the nodes' values.

## Sample Illustration

__Input__:

          List: head -> 1 -> 2 -> 3 -> 4 -> 5 -> 6 -> null
          
__Output__:

          ReorderedList: head -> 1 -> 6 -> 2 -> 5 -> 3 -> 4 -> null
          

