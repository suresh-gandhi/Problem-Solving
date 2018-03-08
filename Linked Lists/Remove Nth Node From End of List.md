## Problem Statement

Given a singly linked list, remove n'th node from the end of list and return its head. The given n will always be valid.

__**Note:__ It would be great if you do this in single pass.

### Sample Illustration

Input: 1->2->3->4->5  and  n = 2.

Output: 1->2->3->5.

## Intuition

If we were given the length of the linked list we would simply delete the ( Length - n )'th node from the start and our work was done. 
So, in order to solve this problem we could simply find the length of the linked list in one traversal and then delete the necessary node in another traversal.

![length_calculation](https://user-images.githubusercontent.com/22693609/37134479-b59d6450-22be-11e8-9732-365b076dbcf0.png)


But, there is a better way to do this and in single pass. To understand this approach we need to consider an interesting puzzle:-

Suppose, there is a straight road with a dead end. And your house is 'N' metres before that dead end. Your need to reach your home using this roadway. The twist is that you are blindfolded and can only walk in forward direction of this roadway. But to your rescue 
you have a stick whose length is adjustable i.e. you can change the length of the stick according to your wish. 
How will you reach your home? :confused:


Problem Animation:- 



The solution for this puzzle is quite simple. Just make the stick length as 'N' metres, hold it in your hand horizontally and go on until you can. You will get stuck exactly N metres before the dead end and hence will be able to reach your home in time and make your mommy happy. :wink:



Solution Animation:-



Now, you must be wondering why this riddle was important. The puzzle discussed and our problem are completely analogous in all senses. 
Analogies are listed below:-

- The given linked list is equilvalent to the straight road given in the puzzle.
- The dead end could be seen same as NULL node at last of a linked list.
- The blind man is equilvalent to a traversal pointer(blind because we can't see beyond this node using this pointer)
- The problem demands to find N'th node from last and our puzzle asks way to reach N metres before the dead end.

But, what about the stick? :frowning:

We can build a rod easily by using 2 pointers at a distance of N nodes as shown below.

                1 -> 2 -> 3 -> 4 -> null
                ^         ^
                |--Stick--|
                |         |
              point1    point2

Now as the stick is rigid and its length cannot change, we will have to move both our pointers simultaneously. The animation below 
will make it clear.

![pointers rod analogy](https://user-images.githubusercontent.com/22693609/37135412-3e181560-22c3-11e8-8050-a448a2324f86.gif)

So, now we can reach the n'th node from last using this approach. But, to delete this node we must do it from the previous node. So instead of reaching this node we will try to reach the previous node.(See the note below for special case). We can then finally delete the required node and celebrate our achievement. :relieved:

**Note:- If there is no previous node to this or the node to delete is the first node, then our result should be simply Head->next.(here 'Head' is the head of the given Linked List).

## Detailed Procedure

1. 


## C++ Implementation

```
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode(int x) : val(x), next(NULL) {}
 * };
 */

class Solution {
public:
    ListNode* removeNthFromEnd(ListNode* head, int n) {
        
        //These are the 2 pointers for making the rod
        ListNode *first,*second;
        first = second = head;
        
        //Shifting second node n nodes ahead to make the rod of length 'n'
        for(int i=0;i<n;i++)
            second = second->next;
        
        //Special case: First node deletion
        //If the rod's other end has already reached dead end, then simply return the node next to head
        if(!second){
            ListNode* new_head = head->next;
            free(head);
            return new_head;
        }
      
        //Move the rod until the rod's second end has reached the node prevoius to NULL
        while(second->next){
            //As the rod is rigid, moving both the pointers equally
            first = first->next;
            second = second->next;
        }
        
        
        ListNode* waste = first->next;
        
        //Deleting the required node
        first->next = first->next->next;
        
        //Waste removal part
        free(waste);
        
        return head;
    }
};
```
