## Problem Statement

Given a singly linked list, remove n'th node from the end of list and return its head. The given n will always be valid.

__**Note:__ It would be great if you do this in single pass.

### Sample Illustration

Input: 1->2->3->4->5  and  n = 2.

Output: 1->2->3->5.

## Intuition

If we were given the length of the linked list we would simply delete the (L-n+1)'th node from the start and our work was done. 
So, in order to solve this problem we could simply find the length of the linked list ourself and then delete the necessary node.

But, there is a better way to do this and in single pass. 
