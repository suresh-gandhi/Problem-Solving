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

1. Save the result for the smaller subproblem of size n-2 using recursion.
2. Reverting the direction of next pointer in between 1st and 2nd node(could be said as swapping too).
3. Link the given linked list's first node(or simpply called head) to the smaller subproblem result saved earlier.

This might be difficult to understand. The pseudo code and the corresponding animation below will make things easy for you.

```
swapPairs(head):
    //As our new head will be the 2nd node from start
    new_head = head->next;
    
    //Reverting the direction of next pointers                           
    new_head->next = head;
    
    //Linking the given linked list's 1st node to the smaller subproblem of size (n-2) saved earlier
    head->next = swapPairs(head->next->next);                                           
    
    //Finally, setting our new head as given linked list's second node
    return new_head;
```

Animation here:-  






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
    //Inverts the first 2 nodes and then recurse for the rest
    ListNode* swapPairs(ListNode* head) {
        //If the given node is NULL or size of the given linked list is 1, we should return the head
        if(head == NULL || head->next == NULL)
            return head;
        
        ListNode *new_head = head->next;
        
        //Reverting the direction of next pointers
        new_head->next = head;
        
        //Linking the given linked list's 1st node to the smaller subproblem of size (n-2) saved earlier
        head->next = swapPairs(head->next->next);                                           
    
        return new_head;
    }
};
```
