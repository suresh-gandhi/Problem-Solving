## Problem statement

Write a function to delete a node (except the tail) in a linked list, when given access to only that node.

Suppose that the given linked list is 100 -> 200 -> 300 -> 400 and you are given the second node with value 200, then after your function call the given linked list should become 100 -> 300 -> 400 .

## Intuition

If we were given the previous pointer to the node(that is to be deleted) then we could simply set:
```
previous_node->next = node_to_be_deleted->next 
```
and our work was done.

![temp1](https://user-images.githubusercontent.com/22693609/36655032-47b62ac4-1ae6-11e8-9ae2-c9beb16b7f30.PNG)

The **main logic behind deletion** is this linking of previous node to the right node. But, we don't have the previous node here!

One important thing to notice here is that **we cannot delete the given node** because if we delete this node 
there would be no links between the left part and right part of this node(i.e. the linked list would become disconnected).
So what to do now?

We could do something with the values inside the node. In fact we could copy the value of the next node in this node and then delete the next node. Bingo! :boom:

## Detailed Procedure

1. Set node.value to be equal to node.next.value .

2. Delete the next node by setting node.next as node.next.next .
  
#### Note:
- It is assumed that the given node is not the tail of any linked list.
- We also need to free the memory for the next node in some languages such as C++.

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

Animation for the C++ implementation could be seen below:-

![delete-node](https://user-images.githubusercontent.com/22693609/36656680-7c1a007a-1aef-11e8-84bf-76c01fcac55d.gif)
