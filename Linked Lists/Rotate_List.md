### Problem Statement

Given a singly linked list, rotate it to the right by *k* places, where *k* is non-negative.

In simple language, place the last k nodes of a linked list in front.

Ex:-   

Given Input:     1->2->3->4->5->NULL    and     k = 2,

Output:     4->5->1->2->3->NULL .



### Intuition

We could consider the whole linked list analogous to a big linked list with only 2 nodes. The first big node consisting the first (n-k) nodes of the given linked list and the second big node consisting of last k nodes of the given linked list, where n is the length of the given linked list.

![Capture](C:\Users\Rohit\Desktop\Capture.PNG)

Now, it gets converted into a simple problem in which we have to basically place the second part in front of the first part and we are done.

### Procedure

Now, in order to do the linking part, we first need to keep 4 pointers:-  

1. first node of first part(call it first_head)
2. last node of first part(call it first_tail)
3. first node of second part(call it second_head)
4. last node of second part(call it second_tail)



For linking, we just do:-

- second_tail->next = first_head
- first_tail->next = NULL

And, then we finally return our **new head as second_head**.

A small animation for the same could be seen below:-









But, how do we get all the 4 required pointers for our purpose?

- first_head is head of the given linked list
- second_tail is tail of the given linked list
- first_tail is (n-k-1) nodes to the right of given head pointer.
- second_head is first_tail->next




#### Note

- The *'k'* referred in the problem statement could also be more than the length of the given linked list. In that case we should convert 'k' into k%n so that it is always less than n.
- And after converting if it is equal to n or 0 we don't need to do anything to the list.



### C++ Implementation

```c++
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
    ListNode* rotateRight(ListNode* head, int k) {
        //Seeing for the 0 length linked list separately
        if(!head) return head;
        
        //Calculating the length of the linked list
        int n = 1;
        ListNode* node = head;
        while(node->next){
            n++;
            node = node->next;
        }
        
        //Converting k if k>n
        k = k%n;
        
        //If it gives us k=0 or k=n after conversion
        if(k==0) return head;
        
        //Setting the first_head and second_tail pointers accordingly
        ListNode *first_head = head , *second_tail = node;
        
        //Setting the first_tail
        ListNode *first_tail = head, *second_head;
        for(int i = 0 ; i < n-k-1 ; i++ )  //Moving forward (n-k-1) times
            first_tail = first_tail->next;
        
        //Setting the second_tail pointer too
        second_head = first_tail->next;
        
        //Linking part according to discussion
        second_tail->next = first_head;
        first_tail->next = NULL;
        
        //We return our new head
        return second_head;
    }
};
```

