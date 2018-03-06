## Problem Statement

Given a singly linked list, swap every two adjacent nodes and return its new head.
### Sample Illustration

__Input__: 
      
    100 -> 200 -> 300 -> 400 -> null
     ^
     |
    head

__Output__: 
      
    200 -> 100 -> 400 -> 300 -> null
     ^
     |
    head

## Intuition

Let the length of the given linked list be 'n'.
Then, if we swap first 2 nodes of the given linked list, we are left with a smaller subproblem of size (n-2) that we have to solve now. 
If we go on doing this until the end we will get our desired output.

Here, we noticed that in order to solve the given problem we needed to solve a similar subproblem of smaller size. 
Hence, it would use the concept of recursion and the recurrence relation for the same is:-

```
T(n) = T(n-2) + {work needed to swap first 2 nodes}.
```

## Detailed Procedure

Steps to follow:-

1. Swap first 2 nodes of the given linked list.
2. Save the result for the smaller subproblem of size n-2 using recursion.
3. Link the second node after swapping to the smaller subproblem result saved earlier.

This might be difficult to understand. The code snippet below will make things easy for you.

```
swapPairs(head):
    //As our new head will be the 2nd node from start
    new_head = head->next;
    
    //This line basically says that first solve the subproblem with head->next->next
    head->next = swapPairs(head->next->next);
    temp->next = head;
    return temp;
```
