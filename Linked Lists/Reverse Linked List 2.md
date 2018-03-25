## Problem Statement

Reverse a singly linked list from position m to n. Given m, n surely satisfies the condition:  1 ≤ m ≤ n ≤ length of list. 
Try to do it without making new linked list and in one-traversal.

## Sample Illustration

__Input:__ 1->2->3->4->5->6->NULL, m = 2 and n = 4,

__Output:__ 1->4->3->2->5->6->NULL.

## Intuition

As we need to do it in one traversal, we cannot find the length of the linked list and then revert the required region. It also 
means we need to keep track of the node number. The main logic behind reversion of linked list is discussed 
[here](https://github.com/RohitJain1103/Problem-Solving/blob/master/Linked%20Lists/Reverse%20Linked%20List.md). Now we can simply 
