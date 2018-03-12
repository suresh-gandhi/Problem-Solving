## Problem Statement

Given a singly linked list, cluster all odd nodes together followed by the cluster of even nodes. While clustering you must not change 
the relative order inside these clusters.
It is also to be noted that here we are talking about the node number and not the value in the nodes. 

__**Note:__  It would be nice if you solve it without making a new linked list.

## Sample Illustration

__Input:__ 1->2->3->4->5->NULL,

__Output:__ 1->3->5->2->4->NULL.

## Intuition

For clustering all the odd nodes together we must link the 1st node to 3rd node, 3rd node to 5th and so on. And for clustering all the 
even nodes we must link the 2nd node to 4th node, 4th node to 6th and so on. And finally link the end of cluster1 to start of cluster2 and 
we are good to go.

![odd even linked list1](https://user-images.githubusercontent.com/22693609/37279827-ee9fd5d4-2611-11e8-8834-b33cba6d3eee.gif)


## Detailed Procedure

Now, for making the odd cluster we must maintain 2 pointers, one as its head and the other as its tail. Same goes for even cluster too. 
Inserting part in each of the cluster just adds the new node to its tail.
And at last we just link the end of cluster1 to start of cluster2.

#### Steps to follow are as follows:-

1. We first set the oddhead, oddtail and evenhead, eventail as head and head->next respectively.

2. Do until eventail is NULL or eventail is just before NULL:-
      - Link the odd part by just setting oddtail->next = oddtail->next->next and similarly for the even part too.
      - Move both the pointers forward.
      
3. Finally link the oddtail to evenhead to get the desired output.

**If this doesn't makes sense, then just see the code snippet and the corresponding animation below.**

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
    ListNode* oddEvenList(ListNode* head) {
        
        //If given linked list is NULL, we just return as it is
        if(!head)
            return head;
        
        ListNode *oddhead = head, *evenhead = head->next;
        
        //This is the tail part of the 2 clusters which is used for linking
        ListNode *oddtail = oddhead, *eventail = evenhead;
        
        //Do until eventail has become null OR just before null
        while(eventail && eventail->next){
            
            //Linking the odd part
            oddtail->next = oddtail->next->next;
            
            //Linking the even part
            eventail->next = eventail->next->next;
            
            //Moving both the pointers ahead
            oddtail = oddtail->next;
            eventail = eventail->next;
        }
        
        //Linking the 1st cluster to 2nd cluster
        oddtail->next = evenhead;
        
        return oddhead;
        }
};
```
