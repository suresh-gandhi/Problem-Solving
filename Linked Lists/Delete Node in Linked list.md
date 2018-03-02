## Problem statement

Given an access to a node in a linked list, we have to write a function to delete that node. And also:
  * The list is a singly linked list.
  * The given access is not of the tail of the linked list.

## Sample Illustration

__Input__: 
      
    head ->  100 -> 200 -> 300 -> 400 -> null
                     ^
                     |
                   access
            
__Output__:

    head ->  100 -> 300 -> 400 -> null
              
 
## Intuition

Clearly we cannot delete the given node because if we delete this node there would be no links between the left part and right part of this node(i.e. the linked list would become disconnected).
So what to do now? :confused: 

If we were given the previous pointer to the node(that is to be deleted) then we could simply set:
```
previous_node->next = node_to_be_deleted->next 
```
and our work was done.

![delete-node-snapshot_new](https://user-images.githubusercontent.com/22399995/36889005-0a2b2d18-1e1e-11e8-9175-5f3ffd9a75ca.PNG)

So all we need is a pointer to the previous_node. A simple and natural way is to traverse the linked list from the start till a node behind this node (__previous_node__). But this would require us to traverse the whole list in the worst case. :hushed:

A good observation that one might come up with is that the __given_node__ is also a previous node of the __ahead_node__. Hence we can easily delete the __ahead_node__ using the similar logic as stated above. But we also want to take care of retaining the data of __ahead_node__. So before deleting we could simply copy its value and put it inside the given_node. 

In this way we dont have to traverse the whole list and we can do the things in constant time. :blush:

## Detailed Procedure

1. Set node.value to be equal to node.next.value .

2. Delete the next node by setting node.next as node.next.next .
  
#### Note:
- It is assumed that the given node is not the tail of any linked list.
- We also need to free the memory for the next node in some languages such as C++, but not in Java as it is automatically done by the garbage collector.

## C++ Implementation

```
/**
 * Definition for singly linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode(int x) : val(x), next(NULL) {}
 * };
 */
 
class Solution {
public:
    void deleteNode(ListNode* node) {
        
        //Step 1
        node->val = node->next->val;
        
        //This is just for saving the next node so as to free it later
        ListNode* waste = node->next;
        
        //Step 2
        node->next = node->next->next;
        
        //Freeing the memory
        free(waste);
    }
};
```


## Java Implementation

```
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) { val = x; }
 * }
 */
 
class Solution {
    public void deleteNode(ListNode node) {
        node.val = node.next.val;
        node.next = node.next.next;
        return;
    }
}

```

Animation for the C++ implementation could be seen below:-

![delete-node](https://user-images.githubusercontent.com/22693609/36656680-7c1a007a-1aef-11e8-84bf-76c01fcac55d.gif)

## Think

  * Why it is given in the problem that the access is not of the tail. What would happen otherwise? Which line of the code could lead to null pointer exception then?
  
  * How would our approach change if the given linked list is a doubly linked list?
