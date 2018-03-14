## Problem Statement

Given a sorted singly linked list, delete all duplicates (i.e. nodes with duplicate values) such that finally each element appears only once.

## Sample Illustration

1. Input:   1->1->1->2, 

   Output:  1->2.
   
2. Input:   1->1->2->2->3->3,

   Output:  1->2->3.

## Intuition

One subtle thing to notice here is that after deletion process we are only left with the first elements of each unique value.

![remove duplicates from sorted list1](https://user-images.githubusercontent.com/22693609/37385609-9fd5f1f8-277a-11e8-8d88-1c865e9f9475.png)

So, we should basically find a way to delete all the nodes except these first occuring nodes. For that we could simply link these first 
occuring nodes only.

![remove duplicates from sorted list2](https://user-images.githubusercontent.com/22693609/37389131-15b4ba22-2789-11e8-95c4-1aa3129798b6.gif)

## Detailed Procedure




__**Note:__ The code snippet below is simplified just for better understanding purposes and is not the best way for implementation. 
It doesn't frees the memory and causes memory leakage.


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
    ListNode* deleteDuplicateNodes(ListNode* head) {
        
        //If we are given NULL Linked List
        if(!head) 
            return head;
        
        //'first' refers to first occurences
        //'duplicates' refers to duplicate nodes
        ListNode *first = head , *duplicates;
        
        //Do until first is NULL
        while(first){
            
            duplicates = first;
            
            //Move duplicates forward if it has same value as first
            //And duplicates must not be NULL too
            while( duplicates    &&   duplicates->val == first->val ) 
                duplicates = duplicates->next;  //Memory leakage
            
            //Linking the first occurences
            first->next = duplicates; 
            
            //Updating first pointer
            first = first->next;
            
        }
        
        return head;
    }
};
```
