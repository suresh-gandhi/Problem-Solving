## Problem Statement

In a singly Linked list remove all nodes that have value as 'val'.

## Sample Illustration

__Input:__ 1 --> 6 --> 2 --> 3 --> 4 --> 6 --> 5, val = 6.

__Output:__ 1 --> 2 --> 3 --> 4 --> 5

## Intuition

To delete a desired node in a linked list we just need the previous pointer to that node. Desired node in this case would be node with 
value 'val'. So, if we have to delete a node we could simply do:-
```
previous_node->next = present_node->next
```

![remove linked list elements1](https://user-images.githubusercontent.com/22693609/37551932-84959df0-29d0-11e8-9174-a074942f2279.gif)


But what to do if we have to delete the head node too? 
For that we just return head->next as our result.

## Detailed Procedure

Here, 'present' pointer refers to the current node and 'past' pointer refers to the previous node.

Steps to follow are as follows:-

- Assign past as head and present as head->next.
- Do this until present has reached NULL:
  - If the current node doesn't have value as 'val', then simply move past and present pointers forward.
  - Else delete the current node by linking present->next to past->next and move the present pointer forward.

- If the head node has value equal to 'val' just return head->next as result.

__**Note:__ The code snippet below is simplified just for better understanding purposes and is not the best way for implementation. It doesn't frees the memory and causes memory leakage.

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
    ListNode* removeElements(ListNode* head, int val) {
        
        //Special case of 0 length linked list
        if(!head) return NULL;
        
        //past refers to previous node and present for current node
        ListNode *past = head,*present = head->next;
        
        //This loop will delete the all the required nodes except the head
        while(present){
            
            //If the present node is to be deleted
            if(present->val == val)
                past->next = present->next;
            
            //If node is not to be deleted, we update the past
            else
                past = past->next;
            
            //Moving present forward always
            present = present->next;
        }
        
        //If we need to delete the head node too
        if(head->val==val)
            return head->next;
        
        return head;
    }
};
```

//////Code Animation//////

## Think

- In the code above we had to separately see for the head node deletion. Could you think of a more general solution to this problem? (__Hint__ - Use Dummy node at first)
