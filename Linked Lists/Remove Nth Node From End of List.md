## Problem Statement

Given a singly linked list, remove n'th node from the end of list and return its head. The given n will always be valid.

__**Note:__ It would be great if you do this in single pass.

### Sample Illustration

Input: 1->2->3->4->5  and  n = 2.

Output: 1->2->3->5.

## Intuition

If we were given the length of the linked list we would simply delete the ( Length - n + 1 )'th node from the start and our work was done. 
So, in order to solve this problem we could simply find the length of the linked list in one traversal and then delete the necessary node 
in another traversal.

But, there is a better way to do this and in single pass. To understand this approach we need to consider an interesting puzzle:-

Suppose, there is a straight road with a dead end. And your house is 'N' metres before that dead end. Your need to reach your home using this roadway. The twist is that you are blindfolded and can only walk in forward direction of this roadway. But to your rescue 
you have a rod whose length is adjustable i.e. you can change the length of the rod according to your wish. 
How will you reach your home? :confused:


Problem Animation:- 



The solution for this puzzle is quite simple. Just make the rod length as 'N' metres, hold it in your hand horizontally and go on until you can. You will get stuck exactly N metres before the dead end and hence will be able to reach your home in time and make your mom happy. :wink:

Solution Animation:-

Now, you must be wondering why this riddle was important. The puzzle discussed and our problem are completely analogous in all senses. 
Analogies are listed below:-

- The given linked list is equilvalent to the straight road given in the puzzle.
- The dead end is tantamount to Null mode at last of a linked list.
- The blind man is equilvalent to a traversal pointer(blind because we can't see beyond this node using this pointer)
- The problem demands to find N'th node from last and our puzzle asks way to reach N metres before the dead end.

But, what about the rod? :frowning:

We can build a rod easily by using 2 pointers at a distance of N nodes as shown below.

                1 -> 2 -> 3 -> 4 -> null
                ^         ^
                |---Rod---|
                |         |
              point1    point2
              
Animation of movement of pointers in a linked list until null.

Now as the rod is rigid and its length cannot change, we will have to move both our pointers simultaneously. 
So, now we can reach the n'th node from last using this approach. The next task is deleting this which is quite easy and is 
discussed [here](https://github.com/RohitJain1103/Problem-Solving/blob/master/Linked%20Lists/Delete%20Node%20in%20Linked%20list.md) in detail.

## Detailed Procedure

1. 
